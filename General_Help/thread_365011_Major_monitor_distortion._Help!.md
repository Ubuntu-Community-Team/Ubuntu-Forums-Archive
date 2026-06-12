---
title: "Major monitor distortion. Help!"
date: 2007-02-19
forum: General Help
---

### Post by Flufflebuns on 2007-02-19
You'll all have to forgive me for I am a COMPLETE noob to Ubuntu.  I just today installed Ubuntu 6.10 on an old Dell Laptop.  I used the CD installation and during the Live CD process I had a few major problems.  First error said exactly:

"There was an error starting the GNOME Setting Daemon. Some thing, such as themes, sounds, or background settings may not work correctly. The setting Daemon restarted too many times. The last error message was: Child process did not give an error massage, unknown failure occured. GNOME will still try to restart the Settings Daemon next tiime you log in"

The major problem is that my monitor is extremely distorted.  I can see all the icons sort of, but it's like someone took a knife and chopped it into pieces and pasted them in random vertical places.  My cursor will appear in two places, and I can only read windows by dragging them to the far left of the screen which appears perfect, and anything past that to the right is horribly distorted. 

So I thought maybe I could solve this by installing all the files, and so i fully installed Ubuntu on a fresh partition.  I now don't get that GNOME error, but the screen is just as distorted.  So then I updated all the software, and rebooted, and still doesn't work.  

I figure this has something big to do with my graphics card, but i have no idea where to begin updating it or doing a fresh install.  It has an 

ATI Mobility M4
16.0M
SDR SGRAM 1:1 / SDRAM

Maybe it's some other problem, but I have no idea how to fix this.  I also tried the Live CD of 6.06 and the same problem occurred.  Would switching to Xubuntu solve this sort of problem? 

Anyway I'd really appreciate some help, but please be patient with me I have NO idea what anything means, I've never used Ubuntu before, though I'm good at working with windows.

---

### Post by dcstar on 2007-02-19
> **Flufflebuns said:**
> You'll all have to forgive me for I am a COMPLETE noob to Ubuntu.  I just today installed Ubuntu 6.10 on an old Dell Laptop.  I used the CD installation and during the Live CD process I had a few major problems.  First error said exactly:

"There was an error starting the GNOME Setting Daemon. Some thing, such as themes, sounds, or background settings may not work correctly. The setting Daemon restarted too many times. The last error message was: Child process did not give an error massage, unknown failure occured. GNOME will still try to restart the Settings Daemon next tiime you log in"

The major problem is that my monitor is extremely distorted.  I can see all the icons sort of, but it's like someone took a knife and chopped it into pieces and pasted them in random vertical places.  My cursor will appear in two places, and I can only read windows by dragging them to the far left of the screen which appears perfect, and anything past that to the right is horribly distorted. 

So I thought maybe I could solve this by installing all the files, and so i fully installed Ubuntu on a fresh partition.  I now don't get that GNOME error, but the screen is just as distorted.  So then I updated all the software, and rebooted, and still doesn't work.  

I figure this has something big to do with my graphics card, but i have no idea where to begin updating it or doing a fresh install.  It has an 

ATI Mobility M4
16.0M
SDR SGRAM 1:1 / SDRAM

Maybe it's some other problem, but I have no idea how to fix this.  I also tried the Live CD of 6.06 and the same problem occurred.  Would switching to Xubuntu solve this sort of problem? 

Anyway I'd really appreciate some help, but please be patient with me I have NO idea what anything means, I've never used Ubuntu before, though I'm good at working with windows.

It may be that your video driver has been detected incorrectly.

Do a forum search for "vesa" & "xorg.conf" and you should see some detailed procedures on how to get your system working in a basic mode, then you can look into getting it going 100% with your video hardware.

---

### Post by Flufflebuns on 2007-02-19
I searched for stuff with those two commands, and followed a process to set default xorg something to vesa.  It asked a bunch of stuff I didn't know the answers to and now I can't access X at all.  I don't know how to use the command prompt at all, and want to get this working right.

---

