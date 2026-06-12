---
title: "Installed Linux, unable to boot"
date: 2007-08-18
forum: General Help
---

### Post by Allanon.gc on 2007-08-18
Hey guys,

I'm very new to linux and decided to finally trout out Ubuntu after my friend told me how great it was. I dl'ed a 64 bit linux live cd and had to switch it to VGA in order to be able to see anything when I started/installed it. After I installed my partitions I restarted my comp and got the GRUB loading screen. However when I tried to start linux it didn't work. I was able to start through the recover mode and booted to the desktop through startx, one of the only shell commands I know. Anyway I decided to dl some of the linux updates including a video driver and then I needed to restart. Now I can't even use recover mode to boot linux. When I type startx it says it doesn't recognize my display deriver.


Here's my build

EVGA Nvidia GeForce 8800GTX
Intel Conroe Core 2 @ 2.66Ghz stock, 3.2Ghz OC'ed
G.Skill PC6200 DDR 2 2GB @ 920 Mhz
Seagate 300GB Sata II 7.2k RPM HDD
Samsung 160 Sata 7.2k RPM HDD
Creative X-Fi MusicMaster
OCZ Gamestream 600W PSU, 680 Peak load

---

### Post by merlinus on 2007-08-18
What grub error did you get when trying to start in regular mode?

You can try this at the command prompt after booting in Recovery Mode:

```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```

This should at least get you to a GUI, then you can search how to install the correct video drivers for your card.

-merlin

---

### Post by Allanon.gc on 2007-08-18
I'll go try that line and then write down the exact error I get.

Also startx doesn't let me get into a gui and gives me an error instead.

---

### Post by Scunizi on 2007-08-18
you could try /etc/init.d/gdm restart

---

### Post by Allanon.gc on 2007-08-19
Got this error Nvidia: Could not open this device file /dev/nvidia0 (IO error)

and then a bunch of Nvidia devicies such as PCI that couldn't work and a screen detected but not able to work


Fatal Server Error XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining

---

### Post by Scunizi on 2007-08-19
If you can get to the command line without the GUI.....

Go to the command line and type sudo dpkg-reconfigure -phigh xserver-xorg.  This will reset your video driver file.  You can see it and edit it manually if you type sudo nano /etc/X11/xorg.conf.  Nano is a command line text editor.  Use the arrow keys to get around and when done editing, CTRL+o (not zero) to save then CTRL+q to quit.  In the file you will find a line that mentions which driver is currently set.  If it says nvidia, you can manually change it to vesa.  This is the generic video display driver that usually always works.  Now save the file. 

If when you started Ubuntu to get to the command line and you DIDN'T choose the rescue kernel then....sudo /etc/init.d/gdm restart and see what happens.  If nothing happens type sudo shutdown or simply reboot cold.  You may be suprised with a gui at this point on restart.

Now since you have one of the latest nvidia cards you need to read...

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
At the time of this how to, the Nvidia 8600 was not supported with the nvidia driver available from within ubuntu.  There is mention of a work-a-round.  There are also numerous threads in the forums for installing the nvidia driver supplied directly by Nvidia that will be compatible with your card...

One thing of note.. by using the 64bit version of Ubuntu you've opened a pandoras box of issues that may be difficult to overcome as a new user.  You might just consider dl'ing the 32 bit version and run that.  You may find it much less problemmatic.  Most programs are written for 32 bit (even in the windows world) and sometimes the 32 programs don't like running inside of a 64 bit environment.  If you stick with 64 bit you will eventually be forced to learn how to compile from the source code.  

Get you feet wet first with 32 bit.  As they say, Ubuntu is great but... it aint Windows :) ....

---

### Post by Scunizi on 2007-08-19
Sorry for the double post but I thought I'd give you someplace to go to get help in real time as opposed to the forum.

Use an irc client, xchat, chatzilla for Firefox, bitchx, etc and log onto chat.freenode.net port 8001 and connect to #ubuntu for the gnome environment, #kubuntu for the KDE environ., #ubuntu-server for, doh, the server version of ubuntu.

---

