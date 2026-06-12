---
title: "Stop screen blanking in Kubuntu?"
date: 2007-01-18
forum: General Help
---

### Post by elscire on 2007-01-18
Could anyone please help me with this? I'm sure it would be trivial if only I knew where to look.

I have a problem with the screen blanking in KDE. It does so after 10 minutes and I would rather it didn't at all, but I can't find the setting for the life of me.

I'm on edgy kubuntu, running XGL and Beryl.

kde-guidance-powermanager is apparently installed, but as with the creator of  [this thread]("http://ubuntuforums.org/showthread.php?t=284761"), issuing such in a terminal results in a "command not found".

Other suggestions involving the 'xset s' options have also been unsucessful.

The option for DPMS in my xorg.conf is present, though DPMS doesn't seem to work. Commenting the DPMS line out altogether and restarting X has no apparent effect on the blanking either.

Help would be much appreciated! I'm supposed to be using my laptop for a group video presentation tomorrow.. =|

---

### Post by allwin on 2007-01-18
Look, I know my answer does not apply to KDE, however, there is a program for GNOME called "gconf-editor" which displays a treeview of all GNOME options.  If you go down the list, you will eventually find the parameter not to blank out the screen so quickly.  I wish I remembered exactly where it was...the list isn't that extensive, so you can hunt and find it.  Installing GNOME is easy, and you can have two desktop systems on your machine.  When you log on after installing GNOME, check the options at the bottom of the screen, and it will offer GNOME as well as KDE.  Then maybe you could run your presentation under GNOME.

Call this "Emergency Plan B";  if you can't find it in time, you could install GNOME and run it from there in about 20 minutes or so.  OK, call it Plan 9 from outer space.  You know, I've got KDE, GNOME, XFCE, and Enlightenment on my system, and I know that some KDE programs run just fine under GNOME.  May look just a tad funny, but they work.

---

### Post by elscire on 2007-01-21
Thanks for the suggestion, allwin. In the end I discovered that adding "screen blank" "0" to the "ServerFlags" section of my xorg.conf achieved the desired result =)

---

### Post by felixnine on 2007-01-21
I have this same problem too and it's extremely frustrating. I'm going to try modifying my xorg.conf, but why doesn't messing with xset work? I have a script that runs when Xfce starts:

```

#!/bin/sh

xrdb /home/andrew/.Xresources
xset s noblank
xset s off
xset s noexpose
xset s 0 0

```

... which is everything I could think of, but the damn thing still blanks after ten minutes. My monitor doesn't go into standby, it just goes black. Is this a problem with XGL or something? The problem only cropped up after I started using XGL ("xset s noblank" and/or "xset s off" used to work).

---

### Post by rianquinn on 2007-01-21
I have the same problem using KDE. I drives me crazy. I would love for Kubuntu to turn this off by default. My PC works fine, but my Tablet PC always blanks after about ten minutes. The worst part is the only way to get the screen back is to close my lid, wait a few seconds, and then re-open the lid. 

The forums have a lot of posts about this problem with no real answer. Is there a way to tell somebody who works on development to fix this?

---

### Post by elscire on 2007-01-22
> **felixnine said:**
> Is this a problem with XGL or something? The problem only cropped up after I started using XGL
I think it may be. If I start a KDE session without XGL, then alternative options work. With XGL, the only way I have had any success with is changing my xorg.conf

---

### Post by felixnine on 2007-01-22
well, that's relatively brutal, but at least we're on our way to getting a clear picture of what the problem is. it's annoying, but even if it's not fixable, the benefits of XGL/Beryl far outweigh the problem. i had to go back to the ol' 2D Xfce and it sucked, bad.

---

### Post by juantao on 2007-02-05
From another forum I found this and it absolutely works! Put the following in your xorg.conf file and restart X (Ctrl + Alt + Backspace). My screen has (finally) not gone blank all day. Damn! That was a pain in the butt.

Section "ServerFlags"
        Option "blank time" "0"
        Option "standby time" "0"
        Option "suspend time" "0"
        Option "off time" "0"
EndSection

---

### Post by Noffie on 2007-03-21
I have gotten ```
xset s off
``` to work on my DSL project.  I'm curious if xset isn't particular to vanilla X, while these xorg.conf settings are for XFree86.org - makes sense to me.

Or maybe the flavor of X in Ubuntu doesn't work with xset s?  I know the official man pages said that not all displays support all of the xset commands.

Any X experts care to comment?

---

### Post by voyou on 2007-03-25
> **felixnine said:**
> I have this same problem too and it's extremely frustrating. I'm going to try modifying my xorg.conf, but why doesn't messing with xset work? I have a script that runs when Xfce starts:


Presumably, the problem is that your xset script only effect Xgl, not the underlying X server - and, obviously, when the xorg server blanks the screen, Xgl gets blanked as well. 

Try adding export DISPLAY=:0 to the top of your script.

---

### Post by ferd on 2007-11-26
> **juantao said:**
> From another forum I found this and it absolutely works! Put the following in your xorg.conf file and restart X (Ctrl + Alt + Backspace). My screen has (finally) not gone blank all day. Damn! That was a pain in the butt.

Section "ServerFlags"
        Option "blank time" "0"
        Option "standby time" "0"
        Option "suspend time" "0"
        Option "off time" "0"
EndSection

Yes the screen does not go blank all day, but it does not shut down when " put display to sleep " option in Power Management is selected. I prefer no screen saver at all in preference to this.
I

---

### Post by twothird on 2008-05-15
i still had the problem / just edited my xorg.conf with the serverflags code. will edit my post as soon as i have the time to watch some south parks to check this out hehe.

but to be honest, ferd, i guess just adding "blank time" "0" would be sufficient :lolflag:

does anyone know what is the measure here? 0=0ms?

____________

yep, from ```
Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
EndSection
```
I used only ```
Section "ServerFlags"
Option "blank time" "0"
EndSection
```
and the screen does turn itself off as set up in power management. it does not go blank. the screensaver turns itself on.
resolved.

---

