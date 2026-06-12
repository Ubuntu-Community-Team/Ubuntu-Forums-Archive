---
title: "Feisty and my 8800"
date: 2007-05-06
forum: General Help
---

### Post by FoolFromHell on 2007-05-06
Edgy got me the "xserve" error, whatever that is and Feisty makes my monitor stop receiving a signal at all. My monitor is on but shows a black screen with he error that no signal is being received.
I went to the IRC chat and they told me to use the alternative install disk.
So, I did. I partitioned my hard drive to 210GB NTFS/ 90GB EXT3 + linux swap etc.
Well, when I tried booting in this time, the monitor stopped getting a signal again...
The command prompt is available but I dont know how to use it.
My specs are as follow
C2D e6600
EVGA 680i motherboard
EVGA 8800GTX
2GB DDR2-800 RAM
300GB SATA HDD
Can somebody tell me how to fix this?
I found [this]("http://www.albertomilone.com/nvidia_scripts1.html")
Does this work for the 8800 series?
And how to get it to work from the command prompt?
Thank you.

---

### Post by FoolFromHell on 2007-05-06
Btw, im really new at this.
Have no absolute idea how to work command prompt except the ipconfig and ping commands in windows...
I can learn though...

---

### Post by FoolFromHell on 2007-05-06
I tried these commands my friend gave me.
sudo apt-get install nvidia-glx which didnt work.
It said it installed fine and it asked me for my install CD again.
But my monitor lost the connection when I tried to load up the GUI again.
I then tried 
sudo apt-get install nvidia-glx-new
This asked me if I wanted to isntall something unstable or something and it said it installed fine.
The monitor still wont receive a signal...
Im now in my Windows partition again.

---

### Post by FoolFromHell on 2007-05-06
Found this:
sudo wget [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9746/NVIDIA-Linux-x86-1.0-9746-pkg1.run)
Doesnt work at all.
Gives a 404...

---

### Post by calraith on 2007-05-06
You need to change the driver in xorg.conf to the "nvidia" driver.  By default, X uses the "nv" driver, which doesn't work with some newer GeForce cards.  When you boot into Ubuntu and your monitor goes all no-signal on you, hit Ctrl-Alt-F1 to get to a terminal.  Log in, and type the following at a bash prompt:
```
sudo nano -w /etc/X11/xorg.conf
```
Hit Ctrl-W and search for "nv".  Replace nv with nvidia.  Hit Ctrl-X, then Y to close nano and save changes.  Then hit ctrl-alt-del or type the following to reboot:
```
sudo reboot
```
Does that take care of the problem?

---

### Post by FoolFromHell on 2007-05-06
I tried it but the xorg file is empty.
I tried sudo dpkp-reconfigure xserver-xorg also but the GUI didnt load and the xorg file still wasnt there.

---

### Post by calraith on 2007-05-07
Don't forget that the file system in Linux is case sensitive.  /etc/**x**11/xorg.conf is not the same as /etc/**X**11/xorg.conf.  Tab completion helps.  Type and tab as follows, for instance:[INDENT]**sudo nano -w /et**[SIZE=1][COLOR=RoyalBlue][tab][/COLOR][/SIZE]**X**[SIZE=1][COLOR=RoyalBlue][tab][/COLOR][/SIZE]**xo**[SIZE=1][COLOR=RoyalBlue][tab][/COLOR][/SIZE]
[/INDENT]If at any point you hit the tab key and your shell doesn't fill in the rest of the directory or file name, you probably have a typo.  Backspace and fix as appropriate.

That's how I do it anyway.  Tab completion can be used this way as sort of a filesystem spell checker.  I find it highly unlikely that /etc/X11/xorg.conf would simply be missing on a fresh Ubuntu installation.

---

