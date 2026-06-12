---
title: "compiz loads incorrectly every morning"
date: 2008-07-10
forum: General Help
---

### Post by cybergalvez on 2008-07-10
for the past week compiz has been loading incorrectly every morning (note I've not installed anything new).  Basically t get layering wrong, when you click on a menu option they are behind everything rather then on top as they should.  In any event every day I have to restart compiz.  How can I trouble shoot this, I'd like to fix it if I can rather then just restarting comnpiz manually everyday
Jose

---

### Post by sayakb on 2008-07-10
Open CCSM, Click on **General Settings**, click on **Focus & Raise Behavior **tab. Set *Focus prevention level* to **Low** and set *Focus prevention windows *to **& !(type=Menu)**

---

### Post by cybergalvez on 2008-07-11
giving this a try, will let you know how it goes
Jose

---

### Post by cybergalvez on 2008-07-12
> **LinuxIsInnovation said:**
> Open CCSM, Click on **General Settings**, click on **Focus & Raise Behavior **tab. Set *Focus prevention level* to **Low** and set *Focus prevention windows *to **& !(type=Menu)**

well so far this morning this looks like it worked.  Thanks, what exactly does this code do?
Jose

---

### Post by cybergalvez on 2008-07-21
> **cybergalvez said:**
> well so far this morning this looks like it worked.  Thanks, what exactly does this code do?
Jose

It did it again this morning, I booted the computer and the window layers were all wrong, the menus were all behind their programs rather then on top and when the screen saver went on, my desktop widgets stayed ontop of the screensaver (which is how I noticed something was wrong)
What should I look at to fix the problem
Jose

---

