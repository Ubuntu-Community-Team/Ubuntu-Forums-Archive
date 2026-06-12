---
title: "audacity error"
date: 2005-10-02
forum: General Help
---

### Post by casfindad on 2005-10-02
I'm running Hoary on a PII, 400 MHz computer. I installed Audacity from the repository using apt-get, and it installed with no errors. However, when I run the program, I get the following error:
> There was an error initializing the audio i/o layer. You will not be able to play or record audio.
Error: Host error.
Of couse, this severely limits the usefulness of the program. ;-) I'm not sure the audio is working on this computer (I can hear the system bell, but no other sounds.), so I tried installing and running Audacity on an iMac running Hoary on which the sound works fine. Same error message shows up.
Any ideas how to fix this? Thanks in advance for your help!

---

### Post by aysiu on 2005-10-02
I seem to remember getting this problem once before. It was either because I was using the wrong engine (aRTs versus gstreamer, I think) or there was some other audio program open at the time I started Audacity.

---

### Post by casfindad on 2005-10-02
[QUOTE=aysiu]I seem to remember getting this problem once before. It was either because I was using the wrong engine (aRTs versus gstreamer, I think) or there was some other audio program open at the time I started Audacity.[/QUOTE]
I didn't think I had any other audio program open, but I tried again, making sure this was not the case. Same problem as before. I'm too much of a newbie to understand your comment about engines, but I did see that the instructions at ubuntuguide for installing audacity included installation of gstreamer prior to audacity. So I installed all the libraries and codecs listed at ubuntuguide, uninstalled audacity and re-installed it. I still get the same error message.
I also tried working through the sound configuration recommended at [http://ubuntuforums.org/showthread.php?t=26567](http://ubuntuforums.org/showthread.php?t=26567). When I got to the part where they recommended:
[INDENT]sudo gedit /etc/esound/esd.conf[/INDENT]
I noticed two things: First, my esd.conf file was already edited to match the recommendation. (That's because I had already made the modifications recommended at [http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly).)
Second, I saw the following error message when I ran the gedit command listed above:
[INDENT]casey@Theodore:/etc/apt$ sudo gedit /etc/esound/esd.conf
- using device default
- using device default
ALSA lib pcm_dmix.c:868:(snd_pcm_dmix_open) unable to open slave
[/INDENT]
I'm not sure if this helps trouble-shooting, but I thought I'd mention it.

---

### Post by tehwa on 2005-10-02
Go to System > Preferences > Sound, and uncheck "Enable Sound Server Startup". Restart Audacity. This is where the sound is having conflicts.

---

### Post by casfindad on 2005-10-02
Thanks for your message. I tried unchecking "Enable Sound Server Startup", but I still get the same error message. I also tried restarting the computer after this, then running Audacity. Same error.

---

### Post by matthew on 2005-10-02
I can reproduce your problem on my computer. I don't know why it happens. However, I can run Audacity normally by opening a terminal and typing
```
audacity
``` and it works just fine with no other changes whatsoever. It's not really a fix, but it is a usable workaround.

---

### Post by casfindad on 2005-10-02
[QUOTE=matthew]I can reproduce your problem on my computer. I don't know why it happens. However, I can run Audacity normally by opening a terminal and typing
```
audacity
``` and it works just fine with no other changes whatsoever. It's not really a fix, but it is a usable workaround.[/QUOTE]
Nice to know it's not just me! Unfortunately, I tried starting from the terminal, but I still get the same error message.

---

### Post by danoyoto on 2006-01-21
Well I have the same error, when I run it from terminal same thing....HOWEVER if I run it from terminal through sudo its fine,  so does anyone know how I can make the shortcut on the applications/sound/menu run as root?

---

### Post by uberlaff on 2006-01-28
[QUOTE=tehwa]Go to System > Preferences > Sound, and uncheck "Enable Sound Server Startup". Restart Audacity. This is where the sound is having conflicts.[/QUOTE]


yes, this fixed mine... thanks for the post.

---

