# convert midi to mp3

https://www.onlineconverter.com/

```
timidity input_file.mid -Ow -o - | ffmpeg -i - -acodec libmp3lame -ab 64k output_file.mp3
```
https://ourcodeworld.com/articles/read/1395/how-to-convert-a-midi-file-to-mp3-using-timidity-and-ffmpeg-in-ubuntu-2004


## mido: create/edit midi object
```python
import mido

port = mido.open_output()
mid = mido.MidiFile('d2yui.mid')

for msg in mid.play():
    print(msg) 
    port.send(msg) # https://stackoverflow.com/questions/68311242/why-do-i-hear-no-sound-when-playing-midi-with-mido-on-macos

```
### midi on MacOS: 
need turn "IAC driver" live, but "IAC driver" is a bus, not a mixer
https://github.com/mido/mido/issues/180

# play midi
## use pygame

```python
import pygame

pygame.mixer.init()
m = pygame.mixer.music

m.load('d2yui.mid')
m.play() # non-blocking

```
## use timidity
```
brew install timidity
timidity d2yui.mid
```
