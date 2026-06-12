---
title: "Mounting discs?"
date: 2006-12-30
forum: General Help
---

### Post by haxer on 2006-12-30
Hello i wounder how to mount an hdd disk i have 2x200gb one with linux on it and one empty when i look under system--->administration---->Discs i says i have 2, /dev/hda and one /dev/hdb .. so what should i do to have hdb in use to? :-k I have reiserfs on hdb

---

### Post by pay on 2006-12-30
```
sudo nano /etc/fstab
```and add something like```
/dev/hdb1 /media/hdb reiserfs defaults 0 0
```

---

### Post by 0MG on 2006-12-30
In addition to the above example, you would have to

sudo mkdir /media/hdb

then

sudo mount -a

---

### Post by haxer on 2006-12-30
sudo nano /etc/fstab

and add something like
Code:

/dev/hdb1 /media/hdb reiserfs defaults 0 0

In addition to the above example, you would have to

sudo mkdir /media/hdb

then

sudo mount -a
Reply With Quote

Ok what should i do got me all confused now :-k Does ubuntu run along with reiserfs?

---

### Post by taurus on 2006-12-30
> **haxer said:**
> sudo nano /etc/fstab

and add something like
Code:

/dev/hdb1 /media/hdb reiserfs defaults 0 0

In addition to the above example, you would have to

sudo mkdir /media/hdb

then

sudo mount -a
Reply With Quote

Ok what should i do got me all confused now :-k Does ubuntu run along with reiserfs?

What's so confuse about the steps from above?  If you want to mount your second harddrive, you need to add an entry in your /etc/fstab.  Then, you create a new mount point for it and you mount it...

---

### Post by haxer on 2006-12-30
was this really the right way? When i open up my hdb i see folders with names "bin,etc,games,include,info,lib,man,sbin,src" is it really this i wanted?:confused:

---

### Post by pay on 2006-12-31
You wanted to know how to mount the drive. We told you how, you then mounted it. I fail to see what the problem is.

---

### Post by haxer on 2006-12-31
Ok but is it normal to see folder in a hdd thats never been mounted? It was clean as a white paper before this is it normal then to see folders there?:-k and how to make a shortcut to the disk?

---

### Post by pay on 2006-12-31
To make a shortcut try```
ln -s /media/hdb /where/you/want/it
```

---

### Post by haxer on 2006-12-31
Thanks pay and everyone else :) :KS

---

