---
title: "Can't boot from Redo on pen drive"
date: 2017-03-29
forum: General Help
---

### Post by raleigh3 on 2017-03-29
I have put Redo on a pendrive using both Unetbootin and Tuxboot.

However, when I select that drive, it goes to the Ubuntu boot menu.

Is there something I am doing wrong ?

The md5sum for the .iso is correct.

---

### Post by TheFu on 2017-03-30
I've never tried tuxboot.
I've never heard of "redo" and found unetbootin not to always work.
Not all flash drives are compatible with all USB ports for booting.  They may work fine for everything else, except booting.

A few suggestions.
* make certain that USB booting is enabled in the BIOS.
* try using a different USB port.  On my chromebooks, only 1 USB port will boot. The other will not.
* try using a different flash drive. Not all are compatible with every machine or every USB port.
* try using a different flash creation tool.  On Windows, I've had luck with yumi. On Linux, I just use dd to write the disk.
* try using a different distro - I'm assuming that redo is a distro of some sort?

From what you've said, we can't possibly know if you did anything wrong. There simply isn't enough data.

Even if a flash boot setup works on a different machine, that doesn't mean it WILL ABSOLUTELY work on the next one. I've had issues with cheap and expensive drive and with no-name and brand name drives.  Just have to try a few.  I mark the ones that to boot with a silver sharpie dot.

---

### Post by raleigh3 on 2017-03-30
Trying dd failed. I also used the sync command afterwards

Used 

> sudo dd if=/home/andy/Downloads/redobackup-livecd-1.0.4.iso of=/dev/sdc bs=10M



Redo backup is similar to Clonezilla which makes an exact copy of your hard drive.

I have tried all your suggestions except trying another port which I will try shortly.

---

### Post by TheFu on 2017-03-30
I have used a dd with a bs of 1M to shove lubuntu, ubuntu-mate and ubuntu-server onto flash drives. I think your command should work just as well.

What "fails" about that attempt?  Does 'dd' fail? How?  Any error messages? "fail" is extremely vague and impossible to help with that being the only information relayed.

---

### Post by lisati on 2017-03-31
*Thread moved to **General Help**.*

---

### Post by sudodus on 2017-03-31
Did you try according to the following link?

[http://redobackup.org/download.php](http://redobackup.org/download.php)

I don't think it is a hybrid iso file (which means that it does not work to clone it with dd).

---

### Post by raleigh3 on 2017-03-31
> **sudodus said:**
> Did you try according to the following link?

[http://redobackup.org/download.php](http://redobackup.org/download.php)

I don't think it is a hybrid iso file (which means that it does not work to clone it with dd).

Yes, I followed website directions.

It failed with both Unetbootin and Tuxboot.

I have no problem with making a bootable pen drive with Clonezilla on it.

---

### Post by sudodus on 2017-03-31
Yes, Clonezilla is easy to make bootable on USB. I'm using Clonezilla since several years :-)

The Redo web-site wrote about the newest version of Unetbootin. Did you use the current version of Unetbootin from the developer's PPA? The version in Ubuntu's repository is old.

[https://launchpad.net/~gezakovacs/+archive/ubuntu/ppa](https://launchpad.net/~gezakovacs/+archive/ubuntu/ppa)

---

### Post by sudodus on 2017-04-01
I noticed that 'Redo Backup and Recovery' has not been updated since 2012-11-21 (version redobackup-livecd-1.0.4.iso). I think you should consider using a tool that is being developed.

---

