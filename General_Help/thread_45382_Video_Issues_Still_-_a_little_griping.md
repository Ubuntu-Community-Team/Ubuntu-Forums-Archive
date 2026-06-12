---
title: "Video Issues Still - a little griping"
date: 2005-06-29
forum: General Help
---

### Post by wadesmart on 2005-06-29
I just had to gripe outloud on this one issue. 

My move to linux has been very good but this video thing is just total crap. I have tried four different video viewers. Two just crash on start up and two do nothing at all. Its very frustrating. Its so difficult to get work done when your work is viewing media. 

I wish someone with lots of linux knowledge would create a site just for installing and trouble shooting video problems. Yea, its a dream. 

Wade

---

### Post by rachii on 2005-06-29
what viewers have you tried?  do you have drivers?

---

### Post by wadesmart on 2005-06-30
06302005 1151 GMT-5

I have mplayer. I have xine. I have totem. I just read the ubuntu guide on installing more codecs and after doing all of that, mplayer doesnt crash immediately but it still wont play any movies. Totem I cant really figure out. When I enter a url in the Open Location, it does nothing at all. Same with xine. I cant even figure out how to open a location on that one. I can only try local movies. 

I tried Synaptic Package Manger and did the update on that with these three and that didnt do anything. Im a little at a loss being still new. Im not sure what else to do. 

Wade

---

### Post by rachii on 2005-06-30
what type of media or filetypes are you trying to work with?

---

### Post by wadesmart on 2005-06-30
06302005 1628 GMT-5

I work for as a psych specialist for a advert company and they send me many formats, mostly wmv and links to asf. Now, asf I havnt seen that I can access but wmv Im told I can. 

wade

---

### Post by gil-galad on 2005-06-30
Try a open a video file with mplayer in the command line and paste the output.  Someone will get to the bottem of this for you.

---

### Post by wadesmart on 2005-06-30
06302005 2012 GMT-5

I dont know how to do that yet. The command line is still a bit difficult. Im learning as fast as I can. 

Wade

---

### Post by rachii on 2005-06-30
right click on teh desktop
click on 'open terminal'
when it opens, type in "mplayer filename"   (without quotes  and filename refering to the file you want to play)

mplayer should open like always (except in the terminal it will output information about it running)   then just like always, in mplayer file, open-file.   and then after mplayer crashes  copy and paste all the text that was output in the terminal

---

### Post by wadesmart on 2005-07-03
07032005 1050 GMT-5

MPlayer 1.0pre6-3.3.5 (C) 2000-2004 MPlayer Team
CPU: Intel Pentium 4/Xeon/Celeron Foster (Family: 8, Stepping: 7)
Detected cache-line size is 64 bytes
MMX2 supported but disabled
SSE2 supported but disabled
CPUflags:  MMX: 1 MMX2: 0 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled for x86 CPU with extensions: MMX SSE



Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0 : No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing everapper.wmv.
File not found: 'chicagoBB-Cady.wmv'
Failed to open chicagoBB-Cady.wmv


Exiting... (End of file)

I found a post where this guy said he couldnt access movies, and he was trying movies.com. Another poster said that they could with the updated MPlayer. I ran the update from Synaptic Package Manager and then went to movies.com and sure enough I could view a video. However, at any other site I havent been able to. 

This morning I went back to movies.com and I cant again view any video. 

Wade

---

### Post by wadesmart on 2005-07-03
07032005 1103 GMT-5

Thanks to a note from another forum, I was told to try and download the video first and see if I can see it. Sure enough, MPlayer wont play it still but Xine will. There is no sound so Ill have to go back to UbuntuGuide and see what I can do about that. 

Wade

---

