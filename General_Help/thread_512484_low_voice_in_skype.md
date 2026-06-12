---
title: "low voice in skype"
date: 2007-07-29
forum: General Help
---

### Post by ali780 on 2007-07-29
Hi
I've installed skype on my ububtu 7.04. The problem is that when I use it my voice is very low. in fact my microphone record my voice very low and the other people have problem in hearing me. 
How can I fix it?

---

### Post by bettlebrox on 2007-07-29
Have U raised the record volume on the Mic? 

If your using Gnome right click on the Sound applet, click "Open Volume Control", then click on the "Recording Tab" and see what the volume level of the Mic is set to.

---

### Post by ali780 on 2007-07-29
&#1615;Tthanks for fast reply
in the recording window I have just    Capture    that is set to the highest level.

---

### Post by laidback on 2007-07-29
From a terminal run 
$ Alsamixer
and check the settings there. Push them up into the red if needs be.

---

### Post by ali780 on 2007-07-29
I used alsamixer. it is also on the red. but problem persist

---

### Post by samuliri on 2007-07-30
see this:

[http://ubuntuforums.org/showthread.php?t=143512](http://ubuntuforums.org/showthread.php?t=143512)

---

### Post by laidback on 2007-07-30
This may sound daft but could you check that you have it in the correct socket..it's easy to get it wrong...headphones and mic swapped for example. My mic is the pink socket.

---

### Post by ali780 on 2007-07-30
No
Is is plugged in correctly.

---

### Post by laidback on 2007-07-30
Have you tried Sound Recorder?
I got this working correctly before I managed to get the Skype sound working properly.
There's a Capture setting in File>Volume Control>Capture which seemed quite sensitive. I expect it's the same as Alsamixer but you get feed back in the sense that you can record and playback quite quickly.

---

### Post by ali780 on 2007-07-31
I tried it but my sound recorder doesn't work!

---

### Post by laidback on 2007-07-31
Oh dear, I'm not surprised Skype doesn't then.
I have "Record as" set to Voice Lossy...not one of the CD settings.
You must save the file before you can play it back.

If you still cannot get it working, has it worked before?

---

### Post by ali780 on 2007-07-31
When I try to save the file I face with this error
"Could not save the file "Invalid parameters"

I am confused!

---

### Post by xc3RnbFO8P on 2007-07-31
Are you using the lates Skype 1.4 beta?
Have you check out:
Software requirements

    * Qt 4.2.1+
    * D-Bus 1.0.0
    * libsigc++ 2.0.2
    * libasound2 1.0.12

---

### Post by ali780 on 2007-08-01
I don't check anything. How do I check these?

---

### Post by xc3RnbFO8P on 2007-08-01
Open Synaptic Manager ( System - Administration )
Search Qt 4
and you should see  libqt 4 core
is it installed?

---

### Post by ali780 on 2007-08-01
It is already installed.

---

### Post by xc3RnbFO8P on 2007-08-01
Have you check the rest?
* D-Bus 1.0.0
* libsigc++ 2.0.2
* libasound2 1.0.12

---

### Post by ali780 on 2007-08-01
I just check Qt 4. Do I check others in a simillar way?

---

### Post by xc3RnbFO8P on 2007-08-01
Yes

---

### Post by ali780 on 2007-08-01
libasound2 1.0.13 
libsigc++ 2.0-0c2a
dbus 1.0.2
are installed

---

### Post by xc3RnbFO8P on 2007-08-01
Then you check alsamixer
dobble clik on volume control

---

### Post by ali780 on 2007-08-01
It seems in alsamixer everything is ok. Microphone is selected and it is in the highest level.

---

### Post by xc3RnbFO8P on 2007-08-01
edit preferences input source
how many have you

---

### Post by xc3RnbFO8P on 2007-08-01
Here is mine:

---

### Post by laidback on 2007-08-01
In Sound Recorder don't use "Save" but use "File>Save as" which allows you to choose the directory etc. Mine does as yours does, I don't know why, but this works OK for me.

---

### Post by ali780 on 2007-08-01
> In Sound Recorder don't use "Save" but use "File>Save as" which allows you to choose the directory etc. Mine does as yours does, I don't know why, but this works OK for me.
Ok it works but the sound is very low!

---

### Post by laidback on 2007-08-01
Try File>Open Volume control and then mess with the settings.
Also select a different capture, mine has 3, Capture....Capture2

---

