---
title: "unmount_all?"
date: 2004-10-31
forum: General Help
---

### Post by bvc on 2004-10-31
Hi all :-D 

> umount: /: device is busy
umount: /: device is busy
manager.c/1187: unmount_all: unmounting /dev/hdb8
umount: /xdata: device is busy
umount: /xdata: device is busy
manager.c/1187: unmount_all: unmounting /dev/hdb9

That's what I get in vt1 when I logout of gnome. I then have to remount my partions. Any idea what's umounting my partitions? I'm only concerned because it's trying to unmount / :shock:

---

### Post by Perfect Storm on 2004-10-31
Bvc you have to pull out your harddisc everytime you logout :P (j/k ;) )


I'd experienced same problem only with my DVD-drives while inserting a DVD and then logout.

---

### Post by bvc on 2004-10-31
hi AI  :D 

Well, this has always happened, everytime, regardless of what I've done or not done. They are internal hd's/partitions. Happened with warty to.

```
proc            /proc           proc    defaults        0       0
/dev/hdb7       /               ext3    defaults        1       1
/dev/hdb6       /ml             ext3    defaults        1       2
/dev/hdb1       /rescue         ext3    defaults        1       2
/dev/hdb9       /xbkup          ext3    defaults        1       2
/dev/hdb8       /xdata          ext3    defaults        1       2
/dev/hda6       /xp             vfat    defaults        0       0
/dev/hda8       /hda8           vfat    defaults        0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0

``` 



Funny that this post was moved.

**Forum**
[U]Hoary Hedgehog Development Release (2 Viewing)
The place to go to discuss Hoary Hedgehog development releases and ask for help.[/U]

 8-[

---

### Post by cacofonix on 2004-10-31
Next time it happens type in lsof +D  and what your trying to unmount  it lists the command and process using it, you can then locate or use the kill command to close them down.

cacofonix

---

### Post by bvc on 2004-10-31
thank you for reminding me of lsof....sheesh, been 3 years since I've used that.

it's famd, which is required by, or used to be required by gedit and nautilus, among others I'm sure. If that's the case, I can't disable it, so I guess I need to file a bug, unless I can find some way to tell it to let go or not monitor files there, if that's what it is doing, I guess :mrgreen: 

I don't see anything in the man page for fan.conf or in the file.

I've done nothing special so I can't be the only one effected by this.

---

### Post by bdoetsch on 2004-10-31
you aren't. got the same problem here...

---

### Post by bvc on 2004-11-14
prob fixed with current hoary's replacement of fam with gamin

[EDIT] well, it was...not now....nevermind

---

