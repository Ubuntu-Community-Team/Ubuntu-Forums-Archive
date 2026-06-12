---
title: "More Newbie questions...."
date: 2007-09-24
forum: General Help
---

### Post by breakerr on 2007-09-24
Ok then...after reviewing all the threads suggested suggested by the automatic feature of the forum I haven't found the answer on them or google.

I just wanted to ask something....after playing so much with the desktop and all those settings in case that for any X reason I have to get back to my usual Gnome interface and get to defaults without clicking switching and flying around how could I or we set panels to defaults...I mean is there a command or something to make all get back to the first configuration from when you first installed ubuntu.

Right now I cant get my panel to show me the little icon with 2computer monitors together showing that I'm connected to internet and also cant find the way to make gaim or any other application like Kiba-Dock sistray to show in the systray as it was before...apparently I changed something and know I don't know how to fix it.

*Also I would love to know why if I'm the administrator every time I see my splash screen loading before it finish I'm able to read RESTRICTED-MANAGER on it ???? 

THANKS A LOT in advance.

---

### Post by HermanAB on 2007-09-24
The easiest way to restaore your desktop settings to the default, is to create a new user account.

Cheers,

Herman

---

### Post by Adramelech on 2007-09-24
I think the restricted manager you see is the graphical driver manager, it has nothing to do with you been an administrator, it is just a program in charge of some drivers that are not open source (restricted).

---

### Post by mali2297 on 2007-09-24
Run in terminal:
```

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

```

This will remove all your gnome-related customized settings. If you want to backup your old settings, rename the above directories and files instead.

---

### Post by strabes on 2007-09-24
> Right now I cant get my panel to show me the little icon with 2computer monitors together showing that I'm connected to internet and also cant find the way to make gaim or any other application like Kiba-Dock sistray to show in the systray as it was before...apparently I changed something and know I don't know how to fix it.

*Also I would love to know why if I'm the administrator every time I see my splash screen loading before it finish I'm able to read RESTRICTED-MANAGER on it ????

Right click on a blank area of the panel and click "Add to Panel..." Then, add the "Notification Area" applet.

You are not the "administrator" by default in linux. This is a security feature. To read more about this sort of thing, read [this page](http://www.psychocats.net/ubuntu/permissions).

---

### Post by breakerr on 2007-09-24
> **mali2297 said:**
> Run in terminal:
```

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

```

This will remove all your gnome-related customized settings. If you want to backup your old settings, rename the above directories and files instead.

I copy paste that code you gave me and hit enter...nothing happens so I then restart by CTRL + Alt + BackSpace but nothing changes :sad::(

---

### Post by an93l on 2007-09-24
did you shift+insert the code into the terminal or the normal ctrl+v. i am just assuming that when you say nothing happens the terminal was empty of comands as well if not just ignore this, as i wouldn't know ow to return the default's.

---

### Post by breakerr on 2007-09-24
> **an93l said:**
> did you shift+insert the code into the terminal or the normal ctrl+v. i am just assuming that when you say nothing happens the terminal was empty of comands as well if not just ignore this, as i wouldn't know ow to return the default's.

THANKS A LOT after restarting all comes back to normal and the same as the first time :D thanks, now I just need to set everything as it was before :p 

THANKS GUYS......a LOT.

---

### Post by ajgreeny on 2007-09-24
Don't forget that for many commands that have executed OK in the terminal, including rm, cp, mv, etc etc, there is no output to say anything has happened, though if something has not occurred as it should from the command, there will be an error message shown.  This is one more good reason to always backup files before you use the terminal to do things with them;  one slip and you can lose a lot of data or files.

---

### Post by strabes on 2007-09-24
By the way, you can just highlight text and then middle click to paste it. Text is copied automatically when highlighted.

---

### Post by breakerr on 2007-09-26
Hey there...me again....just a quick question.....right now I have my desktop all matching with murrina theme in metacity and all is brown and fancy cool...but some pages/sites have the background with the same dark background color and light brown text....how can I make my theme manager to exclude firefox site from being skinned ??? I want firefox to be skinned to I just dont want the sites/pages to be skinned.

Also I just installed XMMS and wanted to copy paste the skins I just downloaded for it and the XMMS folder tells me that Im not the owner and I dont have permission because the owner is ROOT so I wonder how can I be root to set permissions for that specific folder :confused::confused::confused:

---

### Post by an93l on 2007-09-26
you can set it in firefoxes options to not use the system colours i can't remember exacly where it is but just have a look for appearance it should be a check box in there somewhare. i had the exact same problem.

---

### Post by breakerr on 2007-09-27
> **an93l said:**
> you can set it in firefoxes options to not use the system colors i can't remember exactly where it is but just have a look for appearance it should be a check box in there somewhere. i had the exact same problem.

Thanks a lot _an93l_ but my two questions are still pending......

* How can I make firefox to ignore the background color of my metacity theme in the sites/pages or how can I make my metacity theeme to avoid skinning or setting the same color to the backgrounds of the sites/pages I visit ????

* How can I copy/paste some skins I downloaded for XMMS to the XMMS skin folder when I get a pop up little window telling me that I'm not the owner and I can see in the permissions properties of that window that the owner is ROOT ????? ( I dont want to enable ROOT I just want to be able to paste the skins)

---

### Post by breakerr on 2007-09-29
apart from the entry above I would like to know how I can defragment or clean disk usage and things similar to windows system maintenance to keep the Operating system working properly...**how you do that in Ubuntu ????**

---

### Post by mali2297 on 2007-09-29
> **breakerr said:**
> apart from the entry above I would like to know how I can defragment or clean disk usage and things similar to windows system maintenance to keep the Operating system working properly...**how you do that in Ubuntu ????**

There isn't any defragmentation tool for the file system ext3 (which is default for Ubuntu). You shouldn't need one either because ext3 doesn't usually become fragmented, unless the file system is nearly full.

---

