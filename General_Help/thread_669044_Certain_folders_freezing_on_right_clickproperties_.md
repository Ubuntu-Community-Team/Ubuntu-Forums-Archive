---
title: "Certain folders freezing on right click/properties dialogue box"
date: 2008-01-16
forum: General Help
---

### Post by RatherGood on 2008-01-16
Hey all, 

I'm pretty stumped on this one so I've caved in and registered. 

I'm not overly new to ubuntu or anything, I recently switched from feisty and did a clean install of gutsy. I use LAMPP mostly and I have an odd/new problem. 

After decompressing a tarball under my /htdocs directory (ie, vbulletin, wordpress, wikimedia, etc) I usually right click and double check the properties. 

All my folders are fine except for the folders made by the tarball under htdocs (htdocs folder is fine too). When I right click it brings up the dialogue box with the Basic,Emblems,Permissions,Open With,Notes tabs and the directory browser screen turns grey. At this point it pretty well freezes - I can't select any of the tabs or close the window without using "Force Close". 

I'm running as Root so I have no idea if I am running afoul of any new security schemes. I've never had this problem with any other linux distro's or Feisty. 

I've even managed to duplicate this problem on another machine too. :confused:

---

### Post by jerrykenny on 2008-01-16
Your not really logged into gnome as root are you ?

I wont lecture you. . . . . but . . . . . . 

anyway, does it still happen when you're logged in as a normal user ?

try opening a terminal and look at the results from "top" when it happens again, maybe "top" will even let you kill the offending process.

---

### Post by jerrykenny on 2008-01-16
does 
/opt/lampp/lampp security

offer you any improvements relevant to your situation ?

---

### Post by RatherGood on 2008-01-16
> **jerrykenny said:**
> Your not really logged into gnome as root are you ?

I wont lecture you. . . . . but . . . . . . 

anyway, does it still happen when you're logged in as a normal user ?

try opening a terminal and look at the results from "top" when it happens again, maybe "top" will even let you kill the offending process.


Yes I am logged in as root to gnome... lampp needs to run as root and this machine isn't on a network so I figure no big deal. I just tried it with a user account and there is no problem from the user account. 

The user account obviously can't change the permissions for files root owns but it at least lets me cycle through the tabs without hanging.

---

### Post by jerrykenny on 2008-01-16
I can see how its pragmatic for you, wonder if its the file managers "preview" or "display" settings . . . . 

Perhaps you could install a simpler file manager like thunar or rox and try navigating with that instead ?

---

### Post by RatherGood on 2008-01-16
> **jerrykenny said:**
> I can see how its pragmatic for you, wonder if its the file managers "preview" or "display" settings . . . . 

Perhaps you could install a simpler file manager like thunar or rox and try navigating with that instead ?


Hi, thanks for the tip. Rox handles it fine. I can still change permissions from the command line but I'm really curious as to what is causing the issue with the tarballs (probablly security paranoia with root, scripts, and permissions). 

I tried both archive versions of joomla (zip and tar). The tarball still does the freezing but the zip file version doesn't.

---

### Post by jerrykenny on 2008-01-16
Perhaps if you create a zip archive. the original permission flags are lost, yes rox is good, its light and fast :)

---

