---
title: "permission needed to add Gimp themes"
date: 2012-10-20
forum: General Help
---

### Post by rigidigital on 2012-10-20
[FONT="Book Antiqua"]I just upgraded Gimp to version 2.8, that went well but I'm having a problem extracting the gimp themes which I downloaded into the correct directory. Meaning the directory where the themes must be placed. I keep getting a notification that I dont have permission. I cant seem to get around this problem. Why dosen't it just ask me for my admin password ?

Thx for your help again,

Mike.[/FONT]:guitar:

---

### Post by ibjsb4 on 2012-10-20
Put **sudo** in front of the command you are using.

---

### Post by rigidigital on 2012-10-20
I actually can't see a way to use sudo ? All I am doing is , well first I just try to extract the zip gimp themes to usr/share/gimp/2.0/themes

I just get the permission notification.

Secondly, I extracted the zip gimp themes to the usb stick then copied the entire group of themes, went to the directory to paste them but the paste option was... greyed out...didn't want to even try and work :(

I did include an image to help in case I am not explaining the problem I'm having well enough.:confused:

---

### Post by Scott Goodgame on 2012-10-20
Try this... drop to a command line control-t if in unity (i think, i'm xfce)
then gksudo file-roller  then try your stuff...
Let me know..
Scott

---

### Post by CARLYN on 2012-10-21
> **Scott Goodgame said:**
> Try this... drop to a command line control-t if in unity (i think, i'm xfce)
then gksudo file-roller  then try your stuff...
Let me know..
Scott

Hi Scott and thx for your response. I dont understand why some directories need permission and others don't, well I do understand a little of that.  Just dont get why some have to be so difficult :)

I really couldn;t follow your instructions on how to unzip into the themes directory, could you walk me throuigh it a little bit ?

PS. I was having trouble logging in so i created a new ID. :KS

---

### Post by pbrane on 2012-10-21
unless you have to use these themes system wide it's easier to just extract them to ~/.gimp-2.8/themes.

if you need them in the system folders then you should follow **ibjsb4** or **Scott Goodgame**'s suggestions.

I believe ALT+F2 should bring up the application launcher. type **gksudo file-roller** and hit enter. you should be prompted for your password. open the archive and extract it to the themes folder.

You'll need admin privileges for directories that are not owned by you or that you're not a group member of. It's pretty much that simple.

---

### Post by rigidigital on 2012-10-21
> **pbrane said:**
> unless you have to use these themes system wide it's easier to just extract them to ~/.gimp-2.8/themes.

if you need them in the system folders then you should follow **ibjsb4** or **Scott Goodgame**'s suggestions.

I believe ALT+F2 should bring up the application launcher. type **gksudo file-roller** and hit enter. you should be prompted for your password. open the archive and extract it to the themes folder.

You'll need admin privileges for directories that are not owned by you or that you're not a group member of. It's pretty much that simple.

Ok, thanks for the further explanation. I think I can follow that. Ill post when I've successfully done it !  :-({|=

---

### Post by rigidigital on 2012-10-21
Last question about this. 

1.I am the owner and only user of my computer. Can I use a command that will give me full access to all directories without typing in my password ?

---

### Post by Scott Goodgame on 2012-10-21
You really don't want to do that...
Those parts of the file system are really for mostly no touchy. It asks you permission so you don't do something stupid on accident.

---

### Post by rigidigital on 2012-10-21
Thx Scott. Im the type that would have ended up regretting you giving me that information.

I used Macintosh up untill 2000. I bought a cheap desktop and ordered SUSE online.

It arived with a nice box, manual, cd's , lots of stickers and a shirt.

It installed and operated the modem and printer without needing me to provide installation disks. My impression was this SUSE was pretty slick and clever. Then I went to windows because for my ability windows was easier.

Now I came across some stats yesterday that put Ubuntu as the top rated distro and SUSE AT THE BOTTOM.

---

