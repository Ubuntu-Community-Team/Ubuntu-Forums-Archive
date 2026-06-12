---
title: "temporary files"
date: 2008-02-18
forum: General Help
---

### Post by anksi4u on 2008-02-18
is there anythig like temporary files in ubuntu which can be deleted..i am running out of space so desperately need to free some

---

### Post by sandysandy on 2008-02-18
> **anksi4u said:**
> is there anythig like temporary files in ubuntu which can be deleted..i am running out of space so desperately need to free some

you can also increase ur ubuntu partition size by using GParted. That&#347; what i did when i ran out of space.

regards

---

### Post by Irony on 2008-02-18
To clean out your /var/cache/apt folder do;

```
sudo apt-get clean
```

Also delete the following folder;

```
~/.thumbnails
```

Also do the following;

[http://ubuntuforums.org/showthread.php?t=315654](http://ubuntuforums.org/showthread.php?t=315654)

---

### Post by Shazaam on 2008-02-18
Also go to....
/home/yourusermame/Trash clean it out and /root/.Trash
To clean /root/.Trash you need to be ROOT so type this in terminal....
```
gksudo nautilus
```
which will open nautilus as root. Go to "View>Show Hidden Files" and check it off then clean out anything inside /root/.Trash.
WARNING!!! Anything you do logged in as root is PERMANENT!!!!! You can kill Ubuntu by deleting/changing the wrong things. Please be carefull.

---

### Post by anksi4u on 2008-02-19
when we use synaptics manager to download thigs it says two thigs one is whats the size of the files to be downloaded and how much extra space is used...is this extra space required for temporary files and if yes then are these required and if not required cant we delete them..and where do we delete them from

---

### Post by kpkeerthi on 2008-02-19
Synaptic lists the size of the files to be downloaded (the .deb files) and the approximate space to be used on disk after the debs are installed. 

The downloaded debs are kept in /var/cache/apt. It is safe to clean that folder using **sudo apt-get clean** command.

Also see...
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

