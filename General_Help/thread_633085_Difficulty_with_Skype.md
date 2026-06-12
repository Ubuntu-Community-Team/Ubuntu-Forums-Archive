---
title: "Difficulty with Skype"
date: 2007-12-06
forum: General Help
---

### Post by pgray on 2007-12-06
I'm a new Ubuntu user (Dell Inspiron 1420 with 7.04 pre-installed).  I have downloaded Skpye for Linux 1.4.  I find my Skpye account with no problem and the loudspeakes work well when calling but my mike does not pick up sound (either the built-in mike or a plug in mike).  Can someone advise me on how to set/adjust the mike?  Thanks

---

### Post by KhaaL on 2007-12-06
Can you record sound in another program? I think the problem is that your mic isn't enabled by the mixer.

---

### Post by pgray on 2007-12-06
Thanks Khaal,
I tried recording (applications-sound and video-sound recorder-record) but got nothing.  Your pronosis sounds correct.  How do you enable the mikes in the mixer?  Parker

---

### Post by KhaaL on 2007-12-06
Hmm, since I use KDE I don't have the same mixer as you, luckily it can be changed through the console!

Fire up a console and type:
alsamixer

Once in alsamixer press F4 to go into the capture device section. Turn them up a notch. with the up arrow.

Also press F3 to go in the playback section and press the right arrow to go to the input source columm. Make sure mic is selected on those.

Once you're finished, exit with "Esc" and try again. 

I hope you don't mind using the console :)

---

### Post by pgray on 2007-12-06
I went to the Alsamixer (1.0.13).  At the right side of the mixer I have "line in as output" turned off, "Mic as output" turned off, and "input source" which gives me three options - "front mic, line, and mic".  I tested all three options with Skype with no luck.  I didn't see how to turn on the two settings that are turned off but don't know whether or not I need to.  Thanks for your help.  Parker

---

### Post by KhaaL on 2007-12-06
Oh, I forgot one thing - When you're in the capture tab, is your capture devices on? they can be switched with spacebar (= toggles capture facility). Oh, and you turn those settings on with m (which stands for mute).

There's more help in alsamixer when you press F1. 
Let me know if you still need help!

---

### Post by Dave Otter on 2007-12-06
Try going to volume control(speaker icon on rt tool bar) Rt click icon  go to Volume control
  go to edit  enable mic,mic boost and mic capture.
  back to vol control   should give options Playback .recording.switches
 go to each and enable mic,.mic boost and mic capture
     Hopefully should now work

---

### Post by pgray on 2007-12-09
Thanks Khaal and Dave,
I still have not been able to capture sound (but am getting much more familiar with the alsamixer and Ubuntu - thanks).  I have the capture switch on and set at high volume and in the mixer panel I have tried the "input source" in all three settings - mic, front mic and line.  I have also tried the "line as output" and "mic as output" both on (00) and mute (mm).  Any further advice would be welcome.  Parker

---

### Post by Dave Otter on 2007-12-09
Try Volume cotrol(rt click icon)
  Edit-Preferences enable both mic cature and mic boost+20db

---

### Post by pgray on 2008-01-09
Dear Dave and Khaal,
Thank you for your help.  I am still not able to get the mike.  I took a break from trying to solve the problem over Christmas.  I have the capture setting on with high volume.  With the help of Dell (on-board diagnostics) I determined that the mic hardware does work.  I tried changing device to OSS but with no success.  I also confirmed that esd.conf was correctly configured.  Do you have any more ideas?  Thanks again.  Parker

---

### Post by magiver on 2008-01-10
I had the same problem in my 1420 but with ubuntu 7.10
Double click in the volume control, go to edit > preferences, select digital and input source, go to the recording tab and turn up the volume of digital and finally go to the options tab an d select "mic" as the input source.
It worked for me in 7.10...
I hope this solves your problem

---

### Post by ulmito on 2008-01-10
try ..

1) added gutsy-proposed to my sources.list
2) ran apt-get update
3) installed linux-backports-modules
4) restarted the laptop to reload the kernel and modules
5) ran alsamixer and set the following settings:
   Section: [All]
     Digital Input Source: Digital
     Input source: Front Mic (probably unnecessary)
   Section: [Capture]
     Capture: max volume, capture ON
     Digital: max volume
6) and, at last, started gnome-sound-recorder with input "Digital" to check if that worked - and it did 

also try skype 2.0 video...

[http://www.skype.com/intl/en/download/skype/linux/beta/](http://www.skype.com/intl/en/download/skype/linux/beta/)

:popcorn:

---

