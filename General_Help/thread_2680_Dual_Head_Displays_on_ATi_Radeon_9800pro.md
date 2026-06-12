---
title: "Dual Head Displays on ATi Radeon 9800pro"
date: 2004-10-30
forum: General Help
---

### Post by Borgmeister on 2004-10-30
Hi guys new to ubuntu,very impressed with general hardware detection, such as my wg511 on my laptop, which i dual boot with yoper now.  However, on my desktop, i have 2 displays, which work great with winslows xp. I was wondering, if it were possible to set it up in ubuntu. Also, netgear wg311v2, which your installer saw fine, but failed to work with, i need ndiswrapper i know, but, how do i use apt without a network cable? or internet connection?

---

### Post by fng on 2004-10-30
yes it is possible to get the 2 displays working.

The easiest way is to run fglrxconfig.  It will adjust your /etc/X11/XF86Config-4 config file.
The hard way is to manually edit that file :).

---

### Post by Zillion on 2005-01-31
2 (noob) questions.

Are you absolute sure about dual head working on a radeon9800 pro? I cant get it to work in Suse and thinking of trying Ubuntu instead

Does Ubuntu have own Ati drivers or do we need to dld them from Ati?

tx

---

### Post by mendicant on 2005-01-31
Search in aptitude (or synaptic) for fglrx for the ATI drivers.  They won't be the latest ones if you're working in warty.

---

### Post by Zillion on 2005-02-02
allright I got it running :D

I just did what was descibed in the 1st post of [http://www.ubuntuforums.org/showthread.php?t=3567](http://www.ubuntuforums.org/showthread.php?t=3567)

when sudo fglrxconfig I selected bigscreen and evrything is working now ok, including 3d, however windows still gives me a bit better fps in 3d games but I guess thats the quality of the ati drivers

---

### Post by socratic on 2005-02-02
Ok, I got the ATI drivers up and running some time back in November, I think, but at the time, there were a couple of annoying behaviors: dialog boxes, the login screen, etc., were aligned to the center of the desk area and were cut in half, with half on each monitor; the gnome bars stretched across both displays.  Anyone know if these have been fixed in the more recent driver releases?

---

### Post by Zillion on 2005-02-10
[QUOTE=socratic]Ok, I got the ATI drivers up and running some time back in November, I think, but at the time, there were a couple of annoying behaviors: dialog boxes, the login screen, etc., were aligned to the center of the desk area and were cut in half, with half on each monitor; the gnome bars stretched across both displays.  Anyone know if these have been fixed in the more recent driver releases?[/QUOTE]

yep i got that too with bigscreen

---

### Post by mendicant on 2005-02-10
Looks like the ATI driver doesn't support Xinerama extensions:
[http://www.rage3d.com/content/articles/atilinuxhowto/Linux_ATI.html#SECTION000142000000000000000](http://www.rage3d.com/content/articles/atilinuxhowto/Linux_ATI.html#SECTION000142000000000000000)

Look at section 13.2.3

---

### Post by n1np0 on 2008-01-15
I think the issue with having the login screen split in half between your displays was cause you wanna enable the option "BigDesktop" or maybe that's what you meant by bigscreen... well anyway, i used bigdesktop in sudo aticonfig.. im new to all the ubuntuness tu but this is the place where i figured out how to get my dualhead setup the way i wanted.

[http://ubuntuforums.org/showthread.php?t=301941&highlight=ati+dual+head](http://ubuntuforums.org/showthread.php?t=301941&highlight=ati+dual+head)

just my two cents

---

