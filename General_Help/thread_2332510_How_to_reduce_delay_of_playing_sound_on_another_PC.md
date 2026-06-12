---
title: "How to reduce delay of playing sound on another PC across network"
date: 2016-08-01
forum: General Help
---

### Post by JimLS on 2016-08-01
I have set up a python script on a BeagleBone which, when conditions exist, plays a sound on another Ubuntu box on the same network.  The delay between the condition triggering and the sound is several seconds and I want to reduce the delay.  I am using this in python:

 os.system("ssh myth@192.168.20.107 aplay -D sysdefault /BBB/sound.wav")

Does ssh cause significant delay?  I also considered putting the sound file on a ram disk.
The sound file size is 42k.

---

### Post by JimLS on 2016-08-03
I put 
useDNS no 
in the ssh config file.  That seemed to improve average time a little but I still get times that vary from 2 seconds to about 12 seconds delay.  The time includes playing the sound so 2 seconds is almost instantaneous.  I have a folder on the PC set up as a location for the BBB so perhaps I could put a file there quicker and have the PC trigger the sound when it detects the file.  Or I could just put a USB sound device on the BBB and avoid the network delays.  Would just need extension wire for the speakers to put them where I want.

---

