---
title: "Problem with Ubuntu and Blender"
date: 2007-11-06
forum: General Help
---

### Post by LuxVan on 2007-11-06
Hi,
my problem is:
When I start Blender from terminal with "Blender -w" I have the following error code:

> luigi@luigi-desktop:~$ blender -w
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.4.4.
Checking for installed Python... got it!
Ignoring Xlib error: error code 168 request code 148
Ignoring Xlib error: error code 168 request code 148


Moreover, When I start Blender the window get opened only in full screen and when I render a project of mine, if I try to move the pop-up with it mouse, it get closed.
[[IMG]http://img61.imageshack.us/img61/8035/schermataha3.th.png[/IMG]](http://img61.imageshack.us/my.php?image=schermataha3.png)
I think that the problem is compiz-fusion because when I disable it the error doesn't occur.

My Ubuntu is 7.10 and my hardware is a Pentium core 2 duo 2.4 gh; 2 gb of Ram and nvidia geforce 8800 gts.
Thank you for your help.

---

### Post by LuxVan on 2007-11-06
Up.

---

### Post by LuxVan on 2007-11-06
Up.

---

### Post by LuxVan on 2007-11-07
Up.

---

### Post by saxofoner on 2007-11-07
Fellow Blender user here.  I've read about problems involving Blender v. Compiz-Fusion, so I'd say fool around with drivers and versions, just disable CF when you actually need to use Blender.  I'm (  :-) ) getting my new laptop tomorrow, w/ a similar gfx card (Quadro 570M (basically an 8600GT w/ DDR3) so I'll screw around and let you know what I find.

---

### Post by adwatkin19 on 2007-12-14
I am also having this problem, all the compiz flashiness just becomes very slow and VERY VERY annoying to deal with. 

If anyone can shed some light on this i would be VERY VERY greatful

Adam

---

### Post by LuxVan on 2007-12-16
Up.

---

### Post by pPrdrm on 2007-12-16
Hi LuxVan,
The error with Xlib doesn't have anything to do with blender not opening in window mode. It has something to do with the version of Xlib and the one that blender is looking for. I had no Xlib problem in Gutsy thow. I had the same problem awhile ago and the solution I've found is to put an extra option in blenders luncher command, after the -w one. Try this command: [COLOR="Red"]/path/to/blender/blender -w **_-p 0 0 1270 945_[/COLOR]**. The first to zeros are for the upper left pixel on the screen that the window will appear and to next two numbers are for the size that the blender window will have. I don't know why the -w option was not enough but -p worked.

---

### Post by swap_i on 2008-01-08
> **pPrdrm said:**
> Hi LuxVan,
The error with Xlib doesn't have anything to do with blender not opening in window mode. It has something to do with the version of Xlib and the one that blender is looking for. I had no Xlib problem in Gutsy thow. I had the same problem awhile ago and the solution I've found is to put an extra option in blenders luncher command, after the -w one. Try this command: [COLOR="Red"]/path/to/blender/blender -w **_-p 0 0 1270 945_[/COLOR]**. The first to zeros are for the upper left pixel on the screen that the window will appear and to next two numbers are for the size that the blender window will have. I don't know why the -w option was not enough but -p worked.

That's great! I changed link to the Blender in main menu and it's work. Thank you!

---

### Post by mosaic2s on 2008-02-09
friends,
i first used blender on xp, liked it.

now i have it installed in ubuntu gutsy. however the menu buttons give a garbled screen around text when accessed. strange. can not figure it out.

---

