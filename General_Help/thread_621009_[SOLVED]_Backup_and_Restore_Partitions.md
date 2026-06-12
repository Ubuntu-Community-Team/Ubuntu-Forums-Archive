---
title: "[SOLVED] Backup and Restore Partitions"
date: 2007-11-23
forum: General Help
---

### Post by lucast on 2007-11-23
I am looking for help or a guide to Backing up Partitions and Restoring them.  My system is as follows

SDA - (160GB)
SDA1 - WinXP-x64 (NTFS)
SDA2 - Ubuntu (ext3)
SDA3 - Swap

SDB - (160GB)
SDB1 - My Documents (Fat32)

USB Drive (500GB) for Backups

I have been reading a few posts on how to do this and I am now a bit lost.  I am not an advanced user/neither a beginner.  I enjoy experimenting in both systems and tend to break them often.

I want to make a clean backup of each partition after I next reinstall everything (if I am correct I can use dd or partimage?)

Then the next bit is a bit grey to me on how to restore the backup so that the system is still bootable?

Im not sure about my terminology here but:
Ideally I would like to make a single image, a bit like and ISOfile for a DVD of all my partitions and when something breaks I just need to restore from this file and everything works again. (Windows and Linux is back to my original setup and booting).

Any advice, links, guides would be much appreciated.

---

### Post by banewman on 2007-11-23
Here's a howto - hope it helps
[http://www.arsgeek.com/?p=637](http://www.arsgeek.com/?p=637) :)

---

### Post by lucast on 2007-12-04
I have had a read of the link you sent me which was very helpflull.  I have one more question before I do this.  I understand now how I can backup my Linux distro and restore it.

Before I started using Linux a few years ago I tried copying Windows to a separatre disk and  then when I wanted to restore my computer from it, nothing worked.  I Fdisk'd the drive and created a new partition which was a different size, formatted it using a boot disk and copied all the files back.  I now understand about the hiden and system files, which I didn't copy.

So my question is, my Windows partition is currently mounted in Linux as /Windows.  I copy all the files in that folder to a tar file.  Now when I next re-build my computer I can create all my  partitions, format them then unzip my windows archive to the newly formated drive and it works?

I guess I would need to install a boot loader again like Grub and everything should work?

Thanks again for any help.

---

### Post by nqsonk9 on 2007-12-04
> 
I guess I would need to install a boot loader again like Grub and everything should work?

Oh yes, if you've make any change to the MBR of your driver.

Well, to backup a WinOS, I think ghost will be the finest choice.

---

### Post by lucast on 2007-12-04
Thanks for the reply.  I will use ghost for my Win Partition.

Out of interest what is it that Ghost can do, that copying every file can't do?

I have a good understanding of computers but not how file systems work.  So to me if every file is copied and then replaced when I want to restore, what in theory won't work?

Its just that I want to move to a Linux only world, but like to have windows there for peace of mind and to test the odd program. So I would like ot do all my administrative tasks from Linux if possible (including backup and restores).

---

