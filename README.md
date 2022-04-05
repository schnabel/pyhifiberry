# pyhifiberry
Python library to interface with Hifiberry OS API (audiocontrol2). There are two APIs available:
* [REST](https://github.com/hifiberry/audiocontrol2/blob/master/doc/api.md)
* [socketio](https://github.com/hifiberry/audiocontrol2/blob/master/doc/socketio_api.md)

This package is targeting mainly the needs for a [hifiberry integration for Home assistant](https://github.com/willholdoway/hifiberry).

## Usage example of the socketio API
Runs for 100 secs and prints artist name if metadata events occure.
``` python
import asyncio
from pyhifiberry.audiocontrol2sio import Audiocontrol2SIO

def metadata_callback(metadata):
    print(metadata['artist'])

async def main():
    api = await Audiocontrol2SIO.connect(<HIFIBERRY_IP>, <HIFIBERRY_PORT>)
    api.metadata.add_callback(metadata_callback)
    await asyncio.sleep(100)

if __name__ == '__main__':
    asyncio.run(main())
```