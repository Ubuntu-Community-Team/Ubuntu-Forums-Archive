---
title: "Black screen after 10 min."
date: 2007-01-18
forum: General Help
---

### Post by SLIMwoogi on 2007-01-18
Hello. Guys. 
First, I'm sorry about my poor English.

I got a Problem.](*,) 
--------------------------------------------------------------------------------------------------------------------------------------
I'm using Edgy + XGL + Beryl. Everything is OK except this. Every time I do nothing(don't typing or moving mouse) with desktop for 10 min. my monitor become black out. To recover the screen I must type any key or move mouse.  For example, When I watching a movie, screen show me a black screen after 10 min. exactly.  But I can still hear the sound of movie file. Not just watching something. When download something, I got a same problem.  First time I just thought that it's screensaver.  So I configured System >> Preferences >> Screensaver  not to work. ( Uncheck "Activate screensaver when computer is idle")
But this action didn't work.
Next, I configured "System>>Preferences>>Power Management"  never put the screen to sleep.
But this didn't work too.

What's the problem? I got a no idea. Please help me.](*,) 


My Desktop Specification
--------------------------------------------------------------------------------------------------------------------------------------
CPU : AMD Athlon3500+
GPU : ATI Radeon x1650Pro ( installed  ATI Proprietary Linux x86 Display Driver 8.33.6)
RAM : 2GB
OS : Ubuntu Edgy(x86)

---

### Post by Iowan on 2007-01-18
Might there be a BIOS setting (power management?) causing that problem?

---

### Post by tariqf on 2007-01-26
I have the same problem except mine is 30mins then blank. I have an HP laptop with no bios settings for this or power management. I have disabled al lpower management and screensavers in ubuntu. 

please can anyone help it's so annoying!

---

### Post by jocko on 2007-01-26
To fix it, add these lines to the end of your /etc/X11/xorg.conf:

```

Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection

```

---

### Post by Galphanore on 2008-03-03
> **jocko said:**
> To fix it, add these lines to the end of your /etc/X11/xorg.conf:

```

Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection

```Well then, my only question now is how do I "thank", in the forum sense of the word, someone. I've been looking around for a couple days to try to find something to solve this problem and this worked perfectly.

Other then the time I accidentally uninstalled my hal and rebooted to a "file not found" message, this forum has had the answer to every question I've had. It wouldn't surprise me if, had I asked instead of simply reinstalling, someone would have know how to fix that too.

Thanks jocko.

---

### Post by jocko on 2008-03-04
> **Galphanore said:**
> Well then, my only question now is how do I "thank", in the forum sense of the word, someone. I've been looking around for a couple days to try to find something to solve this problem and this worked perfectly.

Other then the time I accidentally uninstalled my hal and rebooted to a "file not found" message, this forum has had the answer to every question I've had. It wouldn't surprise me if, had I asked instead of simply reinstalling, someone would have know how to fix that too.

Thanks jocko.

You're welcome!

---

### Post by Linux_Falz on 2008-05-26
Hey there,

Sorry to resurrect this thread but I'm having the same problem and this solution isn't working for me unless I'm doing it wrong!

I type " gksudo gedit /etc/X11/xorg.conf " in my terminal and add:

Section "ServerFlags"
    Option      "blank time" "0"
    Option      "standby time" "0"
    Option      "suspend time" "0"
    Option      "off time" "0"
EndSection

to the file that appears.  However, I still get the black screen!

I'm with an ATI graphics card and using Ubuntu 8.04, consequently when I run a video in full screen mode the video runs very poorly, whereas it's perfect if it's half screen or so.  I know my graphics card can handle it because I did it on windows just fine.  I'm actually using desktop zoom to make my videos full screen which is fine but I was wondering if there was a more 'long term' solution for this issue too!

Thanks in advance, any help on either of my problems will be greatly appreciated!

EDIT:  I should add that I'm VERY new to linux so if my terminal code is wrong then I'm sorry for making such a simple mistake!  (loving it so far though!  Even without games :P)

---

### Post by Linux_Falz on 2008-05-26
OK it seems that the first issue is resolved!

I no longer get a black screen!  I tweaked the file some more and now it works!

So thanks a lot jocko for that one :)

Issue #2 with videos playing verrrrrrrry painfully slowly in full screen mode is still around, though! :(  Of course I can avoid this with desktop zoom but a long-term fix would be greatly appreciated!

Thanks ;)

---

### Post by jocko on 2008-05-27
> **Linux_Falz said:**
> OK it seems that the first issue is resolved!

I no longer get a black screen!  I tweaked the file some more and now it works!

So thanks a lot jocko for that one :)

Issue #2 with videos playing verrrrrrrry painfully slowly in full screen mode is still around, though! :(  Of course I can avoid this with desktop zoom but a long-term fix would be greatly appreciated!

Thanks ;)

This may be because you are using the wrong video output.
For gstreamer apps (totem etc.) start gsteamer-properties (type it in a terminal or ctrl+F2).
Under the Video tab, set "Standard Output" to "X Window System (X11/XShm/Xv)".
If you can choose between more than one device, try "Xgl Generic Texture Video" (which will be there if you have Xgl installed).

Other media players have their own settings.
In mplayer (no gui version), you can try different video output methods by:```

mplayer -vo [COLOR=Blue]xv[/COLOR] filename
``` (try gl2, gl and x11 instead of xv to see which works best, but my guess is that xv will be the best).
To have mplayer always use the best video output:
```
gedit ~/.mplayer/config
```
Add this line:
```
vo=xv,gl2
``` This means mplayer will first try xv and then fall back to gl2 if xv fails. Put the two that works best for you.
In the gui version of mplayer (gmplayer) you can set video output in preferences-->video.

---

### Post by Linux_Falz on 2008-05-27
OK - I downloaded mplayer.

I tried it in full screen and it was slow (just like my VLC) so I tried what you suggested:

Firstly I opened a terminal and typed: mplayer -vo xv filename

That got me this response:

cs@CS:~$ mplayer -vo xv filename
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 47, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing filename.
File not found: 'filename'
Failed to open filename.


Exiting... (End of file)
cs@CS:~$ 




I then did:  gedit ~/.mplayer/config

the only thing that document had written in it was:

"# Write your default config options here!"

I added this line, anyway:

"vo=xv,gl2"

So it now reads:

"# Write your default config options here!

vo=xv,gl2"




Then I tried mplayer again in full screen and it was no different :( so I'm still using desktop zoom!

Thanks for the response, though!  Any other suggestions? :o

---

### Post by jocko on 2008-05-27
> **Linux_Falz said:**
> OK - I downloaded mplayer.

I tried it in full screen and it was slow (just like my VLC) so I tried what you suggested:

Firstly I opened a terminal and typed: mplayer -vo xv filename

That got me this response:

cs@CS:~$ mplayer -vo xv filename
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3200+ (Family: 15, Model: 47, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing filename.
File not found: 'filename'
Failed to open filename.


Exiting... (End of file)
cs@CS:~$ 




I then did:  gedit ~/.mplayer/config

the only thing that document had written in it was:

"# Write your default config options here!"

I added this line, anyway:

"vo=xv,gl2"

So it now reads:

"# Write your default config options here!

vo=xv,gl2"




Then I tried mplayer again in full screen and it was no different :( so I'm still using desktop zoom!

Thanks for the response, though!  Any other suggestions? :o

When I wrote "filename" I of course meant that you should use the *actual name of the file you want to play*.
And when you say you run mplayer, do you really run mplayer (no gui) or do you run gmplayer (gui version of mplayer)?

---

### Post by Linux_Falz on 2008-05-27
When I run MPlayer it simply says "MPlayer - Video" in the application bar - so I'm guessing it's just MPlayer?

---

### Post by jocko on 2008-05-27
> **Linux_Falz said:**
> When I run MPlayer it simply says "MPlayer - Video" in the application bar - so I'm guessing it's just MPlayer?
Do you start it from the command line, with the command:
```
mplayer -vo xv *name_of_a _video_file*
``` (where *name_of_a _video_file *is the (path) and name of an actual video file)? In that case you get the version without gui, which means you just see the video window and no control window. For that you need to set the correct video output in the ~/.mplayer/config file (or include the "-vo xv" in the startup command every time).

Or do you start from the menu? In that case you'll get the gui version (gmplayer). which has a gui, i.e a graphical user interface, with menus and a window with control buttons and so on. In that case you right click one of the windows and select preferences in the menu and set the video output in the "video" tab.

---

### Post by Linux_Falz on 2008-05-27
Ok I started it from the menu (gui version), I clicked preferences, went to video output and selected the xv setting.  It still didn't work, unfortunately :(  

My graphics card could handle things like Counter Strike and Full Screen Videos easily on windows so I don't think it's my card.  Perhaps my card isn't supported, but it does say driver enabled.  It's an ATI Sapphire Radeon 256mb X800 Ultimate.  

This problem is frustrating!  It's strange because I can play the movie perfectly in half size and I can even rotate my cube and it STILL plays perfectly!  This suggests to me that it is not a graphic card error.

Once again, thanks for your input, jocko, the help is really appreciated.

---

