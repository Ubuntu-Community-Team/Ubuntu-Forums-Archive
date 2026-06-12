---
title: "Braid Screesaver causing system hang/freeze"
date: 2007-04-28
forum: General Help
---

### Post by kpel on 2007-04-28
Pretty much what the topic says.  If I select Braid from the Screensaver menu it appears to peg my CPU usage and lock the system up.  If I'm **very** fast I can select it and then click to another one as I still have mouse input control, though it takes several minutes for the system to catch up.  If I attempt to test it the whole system will pretty much lock up solid.

Every other screensaver works fine.  I'd like to know either A) How to fix Braid or B) how to remove it so that I can randomize my screensavers without risking a system lockup.


Ubuntu 7.04
Beryl + Emerald
Nvidia-glx-new (1.0-9755)
Nvidia 7950 GX2
Core 2 Duo E6600
Gigabyte GA-965P-DS3

This is on a clean install with no file modifications other than to xorg.conf, and only then to add the *ARGB GLX Visuals* line to fix the missing window borders with Beryl.

---

### Post by kpel on 2007-04-30
Bumped in hopes of a reply.  If not I'll go mucking around in the directories myself.  *shudder*

---

### Post by fearpi on 2007-05-28
Also experiencing this issue. Also running Feisty with Beryl on an NVidia card.

---

### Post by dagrump on 2007-05-28
You might try adding "exit 0" as the first line of /etc/init.d/powernowd, this apparently makes your proc not scale down. My box would lock up constantly, but it has been good for several days now. Good luck.

---

### Post by xjgnsdof on 2007-11-29
I am experiencing the same problem in 32-bit Gutsy, and I already have "exit 0" in that file. The screensaver that freezes up my system, however, is "Zoom."

---

### Post by bford16 on 2007-12-05
I, too am having the same kind of problem with the Braid screensaver.  I am running a clean install of Gutsy, with an nVidia 6200 LE graphics card.  I am also using Compiz, with "Normal" effects.  Could this be a Compiz issue?

EDIT - Yes, I think so!  I turned off the effects, and now the screensaver works perfectly. HMMM.

---

### Post by ehcualp on 2007-12-05
I had the exact same problem with the braid screensaver. i was scanning thru the screensavers, and when i got to the braid one, it froze gusty. And then when ever it went into screensaver mode, or it i tried changing it, it would freeze. disabling desktop effects, like bford16 did, allowed my to change the screensaver. :)

---

### Post by richbl on 2007-12-07
Hello all,

The hanging of certain screensavers is, indeed, a known bug.

In the meantime, to remove or delete an individual screensaver, here's the procedure:

```

0) sudo rm /usr/share/applications/screensavers/screensaver_name.desktop
```

where screensaver_name is the name of the screensaver you want to remove (in my case, braid).

Regards.

---

### Post by SivArt on 2008-02-15
Hello guys,

I had the same problem with the braid screensaver and deleting it fixed the issue, my system is pretty good so it shouldn't hang;  I am running compiz and emerald on this system and wanted to know if this issue is caused by compiz and if someone opened a bug in regards to this issue.

Thanks!!!


Ubuntu Gutsy 7.10 x64
AMD X2 6000+
4 GB of RAM
NVIDEA 8800GT

---

### Post by richinnewzealand on 2008-02-20
Hi kpel,

just a short question regarding your graphics card. do u run 2 screen on it and that even with visual effects in extra mode? Having huge problems configuring my graphics card and having visual effects in extra mode running. Please advise me of howto get the system up and running and how to config xconfig.

Cheers,

Rich

---

### Post by dayhawk4 on 2008-03-05
Have the same problem.  Was able to connect to machine using ssh, and collected additional information.

     It would seem that when braid was started on my machine (a Dell Inspiron pre-built with Ubuntu, and Nvidia card....  Nvidia restricted driver), compiz.real and Xorg processes would jump up (when looking on top).  Sometimes crtl-alt-bckspc worked after a long delay, other times not.   

After going through all of the screensavers one by one, I found similar problems with the following screensavers....

Braid
Interaggregate
NerveRot
Vermiculate
Whirlwindwarp
Zoom

I 'fixed' the problem by removing the files screensavername.desktop ( i.e. nerverot.desktop) from the /usr/share/applications/screensavers directory.  While not a good save (as the screensavers aren't fixed), it keeps my system from locking up and needing hard boots with all of the problems associated with hard boots.

I discovered which ones were problems by having one machine logged into ssh of the test machine, and everytime I locked up the machine, I used top to kill the xorg process....  resetting the machine

I hope this helps someone else.....

Additionally there is a gnome configuration file that can apparently be used.... however I don't know where it is personally....

dayhawk4

---

