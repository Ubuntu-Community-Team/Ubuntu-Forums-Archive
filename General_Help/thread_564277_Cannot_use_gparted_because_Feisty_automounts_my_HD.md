---
title: "Cannot use gparted because Feisty automounts my HD read/write"
date: 2007-09-30
forum: General Help
---

### Post by kundalinikat on 2007-09-30
Hey I'm trying to resize an NTFS partition with Windows XP on it, from the live-disc GUI. I right-click on the desktop icons for the hard drives which Feisty has recognized and automounted correctly, and choose 'Unmount volume'... When I try to make gparted apply the changes, I get an error message that the drive is mounted read-write (and then Feisty automounts the drives AGAIN). What is the problem?

---

### Post by BLTicklemonster on 2007-09-30
In gparted, look at your toolbar at the top, and click on "partition" and look down, and you will see unmount. Click that to unmount the drive in question. gparted will close.Run gparted again, and you'll find your drive unmounted and ready for action.

Probably.

You are starting it from the terminal using 

sudo gparted


right?

Every time you do anything in gparted, it will probably close, so just open it again to do something else. Not sure if it's just me, or if that's the way it is.

---

### Post by bodhi.zazen on 2007-09-30
Actually that may work, but often the partition is often re-mounted at some point ...

Go to System > Preferences > Removable Drives and Media and uncheck the box(es) "Mount removable ..."

You can un-do this after you run gparted..

---

### Post by BLTicklemonster on 2007-09-30
I went through the same thing he's going through, and that's how I resolved it. I didn't have any idea that there was another way to do it.

Thanks!

---

### Post by ramjet_1953 on 2007-10-01
By far the best way to edit partitions is to use the GPartEd Live CD

You can get it from here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

This is an iso image that you burn to a CD and then boot from the CD.

Trying to partition a HDD that is mounted is like trying to change a tyre on a car that is being driven.

Regards,
Roger 8)

---

### Post by bodhi.zazen on 2007-10-01
> **BLTicklemonster said:**
> I went through the same thing he's going through, and that's how I resolved it. I didn't have any idea that there was another way to do it.

Thanks!

Well your solution usually works, the problem is occasionally the partition then is automatically re-mounted (which, although uncommon, is obviously a pain when your partitions keep re-mounting). 

all I did was show how to disable the auto mounting problem.

@ramjet_1953: +1 gparted live

---

