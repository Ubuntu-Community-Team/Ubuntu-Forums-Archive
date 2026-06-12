---
title: "changing speed of an audio file"
date: 2020-03-04
forum: General Help
---

### Post by Skaperen on 2020-03-04
i have an audio file in .flac format with a sample rate of 44100 Hz.  i can play it at half speed using "[COLOR=#0000cd][FONT=courier new]**mplayer -speed 0.5 filename**[/FONT][/COLOR]" which then takes twice as long to play.  i want to make another .flac file that is played the usual way (without the -speed option) but sounds at half speed and takes twice as much time.  supposedly the [COLOR=#0000cd][FONT=courier new]**sox**[/FONT][/COLOR] program can do this for me.  perhaps [COLOR=#0000cd][FONT=courier new]**ffmpeg**[/FONT][/COLOR] can do this by overriding the input sample rate to convince it that it is getting 88200 Hz for a file that is really 44100 Hz.

both of these commands are very complicated as a result of trying to support so many features.  they are overwhelming for my simple need.  if i can't determine the correct way to run these, i'll just convert to raw and write a little C program to double every sample.  **can anyone suggest the appropriate way to convert this?**

i will then make an mp3 from the slowed down file.

---

### Post by HermanAB on 2020-03-04
You already done it with player.  Just save the file:
mplayer [http://path_to_stream](http://path_to_stream) -dumpstream -dumpfile outFileName

---

### Post by Skaperen on 2020-03-04
i have many such files to do this for.  i want to script it.

---

### Post by mastablasta on 2020-03-05
Audacity offers batch processing: [https://ttmanual.audacityteam.org/o/man/batch_processing.html](https://ttmanual.audacityteam.org/o/man/batch_processing.html)

---

### Post by HermanAB on 2020-03-05
Sox is easy to use and it will guess what you are trying to do, based on the filenames, so you don't need to specify everything.

The general syntax of sox is: sox inputspec inputfile outputspec outputfile filters

Here is some essential reading: [https://linux.die.net/man/1/sox](https://linux.die.net/man/1/sox)

Sox has a 'speed' parameter, which does both tempo resampling and a pitch change to speed up (or slow down) audio:
$ sox inputfile.flac outputfile.flac speed 0.5

With wildcards:
$ sox inputfile*.flac outputfile*.flac speed 0.5

---

### Post by Skaperen on 2020-03-06
i want the pitch of slowing down to be unchanged.  the pitch should be one octave lower because of the slowdown.  i have the man page.  it's just too messy to form all those options together when i don't really know which i need.  i've tried some before.  i've either gotten no change or just noise.

---

### Post by Skaperen on 2020-03-06
turns out sox did it right!  yay!  the pitch was not affected by anything besides the speed change.  it's like it was on an old vinyl album at 33+1/3 and playing it at 16+2/3 (which some older turntables have) and nothing messing with what the needle picks up.

---

