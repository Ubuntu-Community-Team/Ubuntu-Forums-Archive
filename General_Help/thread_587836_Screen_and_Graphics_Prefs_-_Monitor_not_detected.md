---
title: "Screen and Graphics Prefs - Monitor not detected"
date: 2007-10-23
forum: General Help
---

### Post by Gruu on 2007-10-23
My Daewoo L940M (the sticker from Fry's calls it an LXM-940M) isn't in the list of ubuntu's "Screen and Graphics Preferences" monitors. I know the standard resolution and refresh rate (they're on the box, which I have here), but I don't have any drivers, nor can I find any online. I have an intel 745m integrated graphics card, which it detects A-OK. I just can't find a driver for my monitor...

So, I want to either enter the settings in a safe way (i.e. not by hacking xorg.conf), or find a driver.

Any help is greatly appreciated!


Background info (if necessary):
> 
I just upgraded to Gutsy this evening. Over the last few months, my installation of Feisty has gone sour. When I first installed it, everything was working perfectly - it detected my XP and Vista partitions, it displayed graphics beautifully, and it even ran Neverwinter Nights. Then, my screen resolution started going haywire (I think it happened when I started installing/uninstalling mesa), and at some point I could no longer access the screen resolutions I wanted and have them display properly. Needless to say, my attempt to fix the problem via xorg.conf stuff only made things much, much worse. 


---

### Post by Gruu on 2007-10-24
Bump.

In short, is there anything I can do to get my monitor working if I know the specs? Maybe even write my own driver?


 I am moderately fluent in C (I am almost done with my B.S. in computer science...). If someone can point me to resources, or a tutorial, I'd appreciate it.

---

### Post by jdwhitfield on 2007-10-24
I'm having the same problem.  I don't mind hacking the xorg.conf but it seems this silly program changes it when I log in.  Do the generic drivers work in your case?  I tried the generic monitor for my comp and things seem ok but the resolutions are set to incorrect values.  

JDW

---

### Post by Gruu on 2007-10-24
The "generic plug and play" only gives me 640x480 @ 60Hz, which is more or less useless.

---

### Post by jdwhitfield on 2007-10-24
You can try running
 >   $ sudo dpkg-reconfigure xserver-xorg
to reconfigure your xserver.  This unfortunately didn't work for me.  It seems that no matter how I change my xorg.conf it doesn't matter.  But maybe it will work for you.

Also what is your graphics card?  I have an nVida (which is correctly identified) and there is command >  nvidia-xconfig that also didn't work for me but may be worth a try.

---

