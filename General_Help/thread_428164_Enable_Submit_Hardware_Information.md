---
title: "Enable Submit Hardware Information"
date: 2007-04-30
forum: General Help
---

### Post by lingnoi on 2007-04-30
I've been searching around but I can not find out how to display the button to submit hardware information to the Ubuntu hardware database in the device information window.

Is there a config file somewhere? I have the correct package, etc but I do not have the submit hardware information button. If you see in the picture below the manual shows the button but my window doesn't have it but you can see that the package is installed because I have the database collection wizard.

[URL=http://img338.imageshack.us/img338/1606/nobuttonnr7.png]
[IMG]http://img355.imageshack.us/img355/3147/nobuttonxv0.png[/IMG][/URL]

---

### Post by spankymasterc on 2007-04-30
Ignore this

---

### Post by dcstar on 2007-04-30
> **lingnoi said:**
> I've been searching around but I can not find out how to display the button to submit hardware information to the Ubuntu hardware database in the device information window.
........]

Applications-System Tools-Ubuntu Device Database.

If it is not visible, System-Preferences-Main Menu and enable it.

---

### Post by lingnoi on 2007-05-01
Ok I figured this out you need to type.

```
hwdb-gui
```

---

### Post by lingnoi on 2007-05-04
For some reason I can not get any information I submit through the hwdb-gui to display on the site. I wanted to submit my hw db stats for a bluetooth bug I am having.

Anyone else having this problem as well?

---

### Post by koma77 on 2007-06-15
I have the same problem: I can't get any information with hwdb-gui.
How can I re-scan my hardware? Any update on this?

---

### Post by mozkill on 2007-12-13
the hwdb-gui  tool shows up in my default Ubuntu 7.10 installation, in the Administration tools menu, but after I submit I went to the website where the information is supposedly stored and I am unable to figure out the site works:

[http://hwdb.ubuntu.com/](http://hwdb.ubuntu.com/)

The site has a list of the most recent submittals  but in EVERY CASE it looks like the submittals had failed because they are all empty and they look like this:

> Page autorefresh: every 10min 
Ubuntu hardware database entry : 375fb0b0416904e38e69b4d6e2df4895
This is an interim page, that does not show more then some basic data from the dataset.
If you dont see any cpu or memory data below, you might have sent a broken file,
this is most likely the case if hal is not running or has the wrong (non ubuntu hoary or breezy) version.
 

Couldnt detect laptop 
(assuming Desktop) 
 

It looks to me like the database is broken.

---

