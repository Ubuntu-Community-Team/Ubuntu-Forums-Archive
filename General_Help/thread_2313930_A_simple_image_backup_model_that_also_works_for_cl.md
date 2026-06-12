---
title: "A simple image backup model that also works for cloning?"
date: 2016-02-17
forum: General Help
---

### Post by PaulBx on 2016-02-17
I've been doing disk image backups to a 1TB USB drive for years now, using dd and gzip (I have filled the empty spaces with zeros so gzip squeezes it down to nothing). And I have restored that image to the same drive a couple of times when I screwed something up that I had to recover from, and it worked fine for that purpose. My drive is encrypted and has logical volumes, but it is irrelevant since dd just reads and writes every bit on the drive. It's quite simple and convenient; I boot up a puppy linux dvd to do it so nothing on the hard drive is active during backup (it's not mounted).

I tried using this method (without the gzip) to clone a bootable Flash drive, but it didn't work. I suppose that because the target flash drive was different from the source one, there was some anomaly. Anyway it did not yield a bootable flash drive; I don't know why not. (The target was larger, of course.)

This makes me think that all those hard drive images I have been storing for all these years will be of no use if my hard drive (actually an SSD) dies and I have to replace it. Or in other words, that a simple dd/gzip will not be able to clone a hard drive.

I have looked at a bunch of alternatives including clonezilla but they all seem very complex since they do not do bit-for-bit copies; they probably require to work with a mounted filesystem and decrypted data which then has to be encrypted again in the save set, and all sorts of other difficulties.

Is there no way to make dd work? Perhaps some little thing that can be tweaked?

---

### Post by sudodus on 2016-02-17
> **PaulBx said:**
> I've been doing disk image backups to a 1TB USB drive for years now, using dd and gzip (I have filled the empty spaces with zeros so gzip squeezes it down to nothing). And I have restored that image to the same drive a couple of times when I screwed something up that I had to recover from, and it worked fine for that purpose. My drive is encrypted and has logical volumes, but it is irrelevant since dd just reads and writes every bit on the drive. It's quite simple and convenient; I boot up a puppy linux dvd to do it so nothing on the hard drive is active during backup (it's not mounted).

I tried using this method (without the gzip) to clone a bootable Flash drive, but it didn't work. I suppose that because the target flash drive was different from the source one, there was some anomaly. Anyway it did not yield a bootable flash drive; I don't know why not. (The target was larger, of course.)

I have done what you describe, and it works for me. I have also made [compressed dd-images of pendrives](http://ubuntuforums.org/showthread.php?t=2259682) and expanded them to larger pendrives, and it works too. These pendrives have an MSDOS partition table. It is more complicated with GUID partition tables, because of a backup copy of the partition table at the very end of the drive. This might be fixed after cloning, if you use gdisk in one of the advanced modes.
> 
This makes me think that all those hard drive images I have been storing for all these years will be of no use if my hard drive (actually an SSD) dies and I have to replace it. Or in other words, that a simple dd/gzip will not be able to clone a hard drive.

I have looked at a bunch of alternatives including clonezilla but they all seem very complex since they do not do bit-for-bit copies; they probably require to work with a mounted filesystem and decrypted data which then has to be encrypted again in the save set, and all sorts of other difficulties.

Is there no way to make dd work? Perhaps some little thing that can be tweaked?

After you have used ***Clonezilla*** a few times, it is not hard to use. It is also faster than dd, because it copies only used blocks (you need not zeroise the unused blocks). I suggest that you learn how to use it.

As always: A backup system must be ***tested*** (to a 'third' drive). You should never rely on a backup that you have not tested.

-o-

Linux systems are actually quite easy to backup and restore (easier than Windows). You need not clone them.

- Copy the whole directory tree (of each partition) to another linux file system with ***rsync*** ```
sudo rsync ...
``` according to the tips in ```
man rsync
```

- Install the bootloader

- If UEFI, copy also the whole directory tree of the EFI partition.

... or use one of the dedicated ***backup tools***.

---

### Post by Bucky Ball on 2016-02-17
Here's some Clonezilla links you might find of interest:

Home site:
[http://clonezilla.org/](http://clonezilla.org/)

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

Clone hard drive:
[http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/)

I've also used [(http://www.fsarchiver.org/QuickStart#How_to_extract_filesystems_from_an_archive)"]fsarchiver ]("[http://www.fsarchiver.org/QuickStart#How_to_extract_filesystems_from_an_archive)which might be worth a look. sudodus would be better qualified to tell you the differences between the two.

---

### Post by HermanAB on 2016-02-17
Copying the whole kit and kaboodle is a big waste of time.  Linux is mirrored all over the world on hundreds of servers at large institutions such as universities and ISPs.  Saving a tired old copy of it is not particularly useful.  It is better to only backup your data and install the latest and greatest Linux version when the inevitable happens.

---

### Post by PaulBx on 2016-02-17
> Saving a tired old copy of it is not particularly useful.

Unless my time is worth something. There are lots of setup items stored in /etc and who knows where else that took me a long time to get right; I don't want to go through that again if I can avoid it.

I looked at that Clonezilla example, to create an image. Only 25 steps. Not counting the 12-step process to generate a boot dvd.  :rolleyes:

BTW I forgot to mention, in my adventure of cloning a bootable flash drive, I did get it to work with your mkusb utility, or another one, can't remember which.

> because of a backup copy of the partition table at the very end of the drive. This might be fixed after cloning, if you use gdisk

Thanks, that appears to be what I am looking for. I will have to practice my backup/recovery with this addition.

---

### Post by sudodus on 2016-02-17
Good luck :-)

---

