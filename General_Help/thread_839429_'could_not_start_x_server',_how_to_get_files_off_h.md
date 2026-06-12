---
title: "'could not start x server', how to get files off hard drive?"
date: 2008-06-24
forum: General Help
---

### Post by arphaus on 2008-06-24
Hey all,

I will start by stating that I am, most likely, stupid.  The cause of my current issue is undoubtedly the fact that I powered the computer off (via power button) while it was booting into the desktop last night.  (my lame excuse: it was past midnight and I wanted leave work :()

So when booting, I get the login (with audio), and can login normally (with the resulting audio, which I can mute with my multimedia buttons).  I see my desktop background and ... that's it.

Being a noob, all I can do is ctrl-alt-backspace, at which point it shuts down like normal until I get the 'could not start x server' message.  And then I have to power it off manually.

I'm Googling for solutions, but others seem to have causes like system updates, or config changes that resulted in the error.  Also, my internet is down, so I can't get online w/ Ubuntu (I can with XP & a neighbor's hotspot, but dunno how to do that with Ubuntu & the commandline).

I need to suss out the last resort - getting my data off the Ubuntu partition.  I installed Ext2IFS, but that allows me to mount the drive but not access any of the data - XP asks if I want to reformat.  Hopefully I can get the x server issue resolved.

MUCH THANKS to anyone with suggestions.


Arp

---

### Post by rampageoberon on 2008-06-24
With EXT2IFS, XP will not be able to read the drive if it is not unmounted properly. So its worth trying to use command line to shut down the PC properly and then use the driver in XP.

```
sudo shutdown -h now
``` or
```
sudo reboot
```

---

### Post by pytheas22 on 2008-06-24
If you put in a Linux live CD you should be able to easily mount your Ubuntu partition (provided it's not corrupted) and access the data that way.  I don't think the drive is corrupted, however, or else you wouldn't be seeing as much as you do.  I actually don't think the problem is as serious as you might think.  There's probably just an issue with X or Gnome that should be easy to solve.

In the lower left option of the login screen there's a place where you can click to select which session to use.  Can you log in using the failsafe Gnome session or the failsafe terminal?  Let me know and from there we can decide the best course to take.  If I were you I'd try to fix the existing system before pulling off your data and reinstalling.

---

### Post by arphaus on 2008-06-24
Thanks for both ideas - after I posted here, I restarted into recovery mode and this time it recommended a manual filesystem check, which it's doing now.  There's a lot of unattached inode stuff.

XP is booting normally, so there's probably no hardware issue.

In the meantime, my dsl came back so I can finally use my other computer.

---

### Post by jualin on 2008-06-24
Have you try reconfiguring your X server. Since you can get up to the login screen you cant press CTRL-ALT-F1 to go to the command line. > sudo dpkg-reconfigure xserver-xorg and follow the instructions. Then to go back to the login GUI screen just press CTRL-ALT-F7. Maybe this will help you fix the Xorg problem. The LiveCD alternative sounds good too if you want to back up your data.

---

### Post by arphaus on 2008-06-24
the filesystem check seemed to work - figures that the random wallpaper that opened was the [red 'Join the Revolution']("http://www.gnome-look.org/content/show.php?content=73194&forumpage=1&PHPSESSID=56ac027e39d38adb4562b9894ec18d38") one :-P

Seems to connect to my wifi, but without access the interwebs.  I'll have to figure that out.

Gotta say - I love the Ubuntu community.  Peeps ALWAYS come through - thanks so much!

---

### Post by Gunman1982 on 2008-06-24
Just a short tip: 
ctrl-alt-backspace tells linux to shutdown the x-server (gnome/kde/xfce/...)
ctrl-alt-delete tells linux to reboot

small step for mankind, huge step for linux ... or whatever

---

### Post by Gunman1982 on 2008-06-24
sry doublepost

---

### Post by pytheas22 on 2008-06-24
If you post the output of:
```

lspci
```

(or lsusb if your wireless card is a USB stick)

someone can probably tell you how to get it working.  Or you could start a new thread in the networking subforum.

---

### Post by arphaus on 2008-06-24
thanks - it was a really basic issue: i had unplugged my router :-P

---

