---
title: "Sound only comes out of PC speaker."
date: 2016-12-08
forum: General Help
---

### Post by solorize on 2016-12-08
Hi,

I wonder if someone can help me.

I have just installed Lubuntu v16.04 but am having a problem with audio.

If I play any audio it just comes out of my PC speaker and not
out of my speakers that are connected to my on-board sound.
[I]
(I have my pc as dual-boot and if I go into windows the sound
works correctly i.e. comes out the speakers connected to the
onboard sound.)[/I]

Does anyone know how to fix this in Lubuntu? As I would like
to use this as my primary OS.

Thanks in advance.

---

### Post by Keith_Helms on 2016-12-08
Till somebody else comes along and gives you the real answer, I'll give you a guess. ;)

Open a terminal window and type alsamixer.   Hit F6 to select the soundcard if needed and then use the left/right cursor keys to select the desired output device and the up/down cursor keys to adjust the output sound level for that device.

---

### Post by fyfe54 on 2016-12-08
Press the Super (Windows) key and start typing "sound", no quotes.  Click on the Sound Application thens elect the appropriate output in the "Play Sound Through" section.

---

### Post by solorize on 2016-12-08
Thank you both for your replies, much appreciated.

I will give them both a try tonight when I get home and see
if it sorts my problem out.

---

### Post by solorize on 2016-12-08
Thank you both for your replies, much appreciated.

I will give them both a try tonight when I get home and see
if it sorts my problem out.

---

### Post by solorize on 2016-12-08
OK I managed to solve my issue :D

I tried Keith's suggestion, but that did not work.
I then tried fyfe54's suggestion, but my 'Super Key', did not do anything.

So I then right clicked on the '**volume icon**' on the right side of the task bar
and selected '**Volume Control Settings**'.

This then bought up the **ALSA Mixer GUI**.

Then after a bit of clicking around on the various selections I managed to turn off the
sound from the PC speaker, which was on the '**Master Mono**' column.

I then turned on the sound on the '**Head..**'
column, which enabled sound through my stereo speakers which are connected to my PC.

Below is a screen-shot of the 'ALSA Mixer', with the changes I made as per above.

[IMG]http://i68.tinypic.com/2ilei2p.png[/IMG]


I hope this helps others with similar problems.

---

