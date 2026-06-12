---
title: "Advice on setting up shares"
date: 2007-09-20
forum: General Help
---

### Post by the_nite_owl on 2007-09-20
I am running Feisty x64 in a LAMP server config with the Gnome desktop installed.  The system is dual boot with Windows XP though I rarely boot into XP anymore and have setup XP in a virtual under VirtualBox.

I have a second hard drive in the system which is a SATA drive and was formatted as NTFS under XP.  Under Ubuntu it is sda1.
I want to setup this drive for sharing and have installed Samba and figured out how to setup user IDs for access but the drive itself is read only and I am not sure what to do about it.

I read the how to on using ntfs-3g to get NTFS drives read/write available under linux.  Is this a good way to go?  Am I better off to re-format the drive to a native linux format?
The drive has to be accessible from a MAC and several Windows devices and I want to be able to setup different permissions for different groups.
I am still a relative newbie but learning a lot as I go.

I tried changing ownership and permissions on the drive but everything I tried failed without errors and I realized it was probably because it is an NTFS drive.

Thoughts?

---

### Post by tombott on 2007-09-20
I use ntfs-3g for reading and writing to NTFs drives without any issues.
However if you can format to Ext3 then why not, I can access my ubuntu ext3 shares from my xbox, and my wife xp laptop.
My wife can happily write data to the share without any problems.
So in a nutshell if you don't need the drive to be NTFS then format to Ext3 and all should be groovy!

---

### Post by notwen on 2007-09-20
Agreed, if you're going to be using the additional drive strictly on the Linux box, I would go ahead and format it to ext3.  Then just setup Samba and all should be good to go. =]

---

### Post by the_nite_owl on 2007-09-20
I have never had to format a drive in Linux other than during the installation process.  Any info on how to go about this and do I run a risk of screwing up my Grub install?  In the past when I have added drives to the system Grub would start crashing with error 17.  I guess the list of or order of drives/partitions got changed and threw Grub for a loop.

---

### Post by notwen on 2007-09-20
Well being you're not changing any partitions involving your Linux OS(/, /home, or swap) I don't believe GRUB would have issues from this.  That said I would check your /etc/fstab to see what's being auto-mounted,  you may end up having to change the UUID of your 2nd drive to /dev/sda1.  I may be wrong, but I don't think this should be too difficult of a task. =]  You may want to confirm with someone more knowledgeable in this area than I.

---EDIT---

You may also have to remove the Windows entry in your /boot/grub/menu.lst so you cannot accidentally select Windows in your GRUB menu.

---

### Post by the_nite_owl on 2007-09-20
> **notwen said:**
> Well being you're not changing any partitions involving your Linux OS(/, /home, or swap) I don't believe GRUB would have issues from this.  That said I would check your /etc/fstab to see what's being auto-mounted,  you may end up having to change the UUID of your 2nd drive to /dev/sda1.  I may be wrong, but I don't think this should be too difficult of a task. =]  You may want to confirm with someone more knowledgeable in this area than I.

---EDIT---

You may also have to remove the Windows entry in your /boot/grub/menu.lst so you cannot accidentally select Windows in your GRUB menu.


Actually, the drive I am setting up for the share is separate from the one with the windows partition so that makes things easier.  The primary drive is partitioned for Windows and Linux but the drive I need to format is the second drive in the system and has nothing on it that would be a loss.
I just have to figure out the steps to format and then if I need to mount the drive manually?

---

