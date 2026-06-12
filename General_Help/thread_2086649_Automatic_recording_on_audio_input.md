---
title: "Automatic recording on audio input"
date: 2012-11-21
forum: General Help
---

### Post by jlangvand on 2012-11-21
Hi

What I want to achieve, is to automatically record audio from line in when the volume is above a certain level. Preferably, the audio files should be named with the current time stamp, and everything can be controlled from the CLI. Does it exist any programs that could achieve this?

Secondly, if I don`t get this to work as described, I would like to continuously record the audio stream, and save the results to sub-clips every 15th minute or so. What would be the best solution for that?

---

### Post by stinkeye on 2012-11-21
Take a look at this application.
[**_[COLOR="DarkRed"]https://launchpad.net/~osmoma/+archive/audio-recorder[/COLOR]_**]("https://launchpad.net/~osmoma/+archive/audio-recorder")
> You can control the recorder from command-line with the --command option. 
Valid commands are; status,start,stop,pause,show,hide and quit.
See audio-recorder --help for more information.

Been having a play around with it and seems to do what you want.
Tested in Quantal.
Recording by voice level control (first pic) cuts off the first part of the word though,
which would be expected.
It will pause recording when the input level falls below a set level for a certain duration. Default is 4 secs below 30%.

The second pic shows a setting that works to record using my headset mute button to pause recording.
My recording level never falls below about 5% when unmuted, so it only pauses when I mute to 0% level.

Tick the timer section and uncomment and edit the settings you want.Then press the save button.
Marking the Add button records to 1 continuous file.
If unmarked a new file is created after each pause in recording.
Files are saved to ~/Audio

---

### Post by jlangvand on 2012-11-21
Thank you, this seems to be exactly what I'm been looking for! The audio source is a radio scanner, and usually a transmission starts with some noise which will trigger the recording in time.

Going to test it out now ;)

---

### Post by stinkeye on 2012-11-22
> **jlangvand said:**
> Thank you, this seems to be exactly what I'm been looking for! The audio source is a radio scanner, and usually a transmission starts with some noise which will trigger the recording in time.

Going to test it out now ;)
Glad to help.
Just a note, I noticed when the **add** box is marked it continues recording to the same file 
even when you quit and restart audio-recorder.
You need to unmark the add box and press record start and then stop to 
get a new timestamp and then mark the add box again.

---

