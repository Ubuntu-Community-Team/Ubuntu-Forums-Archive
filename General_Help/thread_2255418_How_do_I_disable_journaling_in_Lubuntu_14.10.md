---
title: "How do I disable journaling in Lubuntu 14.10?"
date: 2014-12-04
forum: General Help
---

### Post by steve169 on 2014-12-04
I've installed Lubuntu 14.10 onto an 8-GB flash stick.

As a security measure I want to disable journaling and shred any of the leftover journaling files.

A three-year-old post suggests using this command:
     **tune4fs -O ^has_journal /dev/sdc1**
but terminal says there is no such command and suggests **tune2fs**.

I'm a newbie and need step-by-step instructions.

---

### Post by sudodus on 2014-12-05
***Edit***: Boot from a live linux CD/DVD/USB drive (another drive, not the one you want to change).
Thanks to [**[COLOR=#000000]kalehrl[/COLOR]**]("http://ubuntuforums.org/member.php?u=1457293") for adding this important instruction :KS

I think the only error in '4' instead of '2', so use this command (sudo to get superuser privileges)

```
sudo tune2fs -O ^has_journal /dev/sdc1
```

Quotes from ```
man tune2fs
```

```
       -O [^]feature[,...]
              Set or clear the indicated filesystem features (options) in the filesystem.   More  than
              one  filesystem  feature  can  be  cleared  or  set  by separating features with commas.
              Filesystem features prefixed with a  caret  character  ('^')  will  be  cleared  in  the
              filesystem's superblock; filesystem features without a prefix character or prefixed with
              a plus character ('+') will be added to the filesystem.

              The following filesystem features can be set or cleared using tune2fs:

...
                   has_journal
                          Use  a  journal  to  ensure filesystem consistency even across unclean shut&#8208;
                          downs.  Setting the filesystem feature is equivalent to using the -j option.

```

It can also be a good idea to mount the root partition with the mount option noatime to decrease writing and reduce wear. So in the file /etc/fstab, add the noatime to the fourth column

from something like

```
UUID=cdc8b4a5-46af-43bd-91fc-876c21ef9887 /               ext4    [COLOR=#ff0000]defaults,errors=remount-ro[/COLOR] 0       1
```

to something like
```

UUID=cdc8b4a5-46af-43bd-91fc-876c21ef9887 /               ext4    [COLOR=#ff0000]defaults,[/COLOR][COLOR=#800080]noatime,[/COLOR][COLOR=#ff0000]errors=remount-ro[/COLOR] 0       1
```

Edit with superuser privileges, for example with the text editor nano

```
sudo nano  /etc/fstab
```

---

### Post by steve169 on 2014-12-05
Many thanks, Sudodus.

I have one related question:

I understand journaling to be a record of past files. I want to shred all of these journaled copies. How do I find them?

---

### Post by sudodus on 2014-12-06
If you have journaling, the journal resides in the partition in a way similar to files (but I don't know the details). I would assume that when you switch off journaling, that this process is switched off - no more writing to the journal - but I don't think that the existing journal data are removed. And I don't know a way to wipe the information without wiping the whole drive (or at least the whole partition).

Are you prepared to wipe and re-install? In that case I suggest that you use a suitable tool to overwrite the whole 8-GB flash pendrive with zeroes. There are efficient tools for hard disk drives and SSDs, for example ***hdparm*** and ***DBAN***. I'm not sure if they work with pendrives. ***dd*** works but is risky (and with only 8 GB it is reasonably fast). You could use [mkusb]("https://help.ubuntu.com/community/mkusb") (from the terminal window) to make the dd method safer.

```
sudo -H mkusb wipe-whole-device
```

---

### Post by vasa1 on 2014-12-06
> **sudodus said:**
> ... I would assume that when you **switch off journaling**, that this process is switched off - no more writing to the journal - but I don't think that the existing journal data are removed. And I don't know a way to wipe the information without wiping the whole drive (or at least the whole partition).
...
Can journaling be switched off? Or does one have to use a non-journaling filesystem (ext2?)?

---

### Post by kalehrl on 2014-12-06
It can be switched off but you need to boot from a live linux CD to do so.
The disk on which you want to switch off journaling must be unmounted.
Then you just issue:
```
 tune2fs -O ^has_journal /dev/sda1
```
Of course, change /dev/sda1 according to your setup.
I just use ext2 on my eee pc to avoid all this.

---

### Post by sudodus on 2014-12-06
> **vasa1 said:**
> Can journaling be switched off? Or does one have to use a non-journaling filesystem (ext2?)?

Yes, according to the description in post #2 (and the manual page for tune2fs).

---

### Post by HermanAB on 2014-12-06
Howdy,
A few comments:
a. Disabling journaling is unwise, since it can lead to data loss.
b. Shred doesn't really work right.  Also, on a flash disk, erasing the data once is good enough - after an erase, it is gone.
c. The best security is to encrypt the whole drive and then you need not worry about the journal contents.

---

### Post by matt_symes on 2014-12-06
Hi

A few more comments.

ext3 is ext2 with journaling
ext4 has extras such as extents.
They are forward compatible but not backward compatible which is why you can turn an ext2 file system into an ext3 file system.
The journal is pointed to by inode number 8 and removing the journal just unlinks this file.

I have to agree with all Herman's comments as well. Use encryption instead and keep the journaling.

Kind regards.

---

### Post by steve169 on 2014-12-07
> **sudodus said:**
> It can also be a good idea to mount the root partition with the mount option noatime to decrease writing and reduce wear. So in the file /etc/fstab, add the noatime to the fourth column ...

Dear Sudodus:

     I looked in my **/etc** directory but found no **fstab** file. Could it be somewhere else?

---

### Post by steve169 on 2014-12-07
> **HermanAB said:**
> The best security is to encrypt the whole drive and then you need not worry about the journal contents.

Dear HermanAB,

I tried to install Lubuntu 14.10 with encryption and it went haywire. (I've forgotten exactly what went wrong.)

I have Lubuntu 14.10 installed on my flash stick now. Is there a way to encrypt _after_ installation?

---

### Post by sudodus on 2014-12-07
> **steve169 said:**
> Dear Sudodus:

     I looked in my **/etc** directory but found no **fstab** file. Could it be somewhere else?

Installed Ubuntu based system should have that file, including Lubuntu.

Even live Ubuntu based system should have that file, but it is different (I just checked with Lubuntu 14.10 to be sure).

The following command (copied from this reply and pasted into a terminal window) should show the content of the fstab file.

```
cat /etc/fstab
```

---

### Post by sudodus on 2014-12-07
> **HermanAB said:**
> Howdy,
A few comments:
a. Disabling journaling is unwise, since it can lead to data loss.
b. Shred doesn't really work right.  Also, on a flash disk, erasing the data once is good enough - after an erase, it is gone.
c. The best security is to encrypt the whole drive and then you need not worry about the journal contents.

> **matt_symes said:**
> Hi

A few more comments.

ext3 is ext2 with journaling
ext4 has extras such as extents.
They are forward compatible but not backward compatible which is why you can turn an ext2 file system into an ext3 file system.
The journal is pointed to by inode number 8 and removing the journal just unlinks this file.

I have to agree with all Herman's comments as well. Use encryption instead and keep the journaling.

Kind regards.

+1

> **steve169 said:**
> Dear HermanAB,

I tried to install Lubuntu 14.10 with encryption and it went haywire. (I've forgotten exactly what went wrong.)

I have Lubuntu 14.10 installed on my flash stick now. Is there a way to encrypt _after_ installation?

I think it is much better to reinstall than to try to fix the security afterwards.

The following link is actually describing how to ***test*** full encryption, but it ***works well to help installing*** it too. [COLOR=#b22222]WARNING: It will use the whole disk !!![/COLOR][COLOR=#ff0000]
[/COLOR]
[http://iso.qa.ubuntu.com/qatracker/milestones/326/builds/85079/testcases/1439/results](http://iso.qa.ubuntu.com/qatracker/milestones/326/builds/85079/testcases/1439/results)

---

