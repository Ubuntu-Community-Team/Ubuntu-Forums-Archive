---
title: "Can't access tty; Job control turned off"
date: 2008-04-16
forum: General Help
---

### Post by Tigairius on 2008-04-16
I think the installed version of Ubuntu is 6.06 on the hard drive that's giving me problems... let me explain the situation.

I've had Ubuntu on a slave drive and Windows XP on a master drive for a while now, and I had windows installed before I had Ubuntu installed. Recently I had major computer issues and had to reformat my Windows hard drive, however; I backed up a lot of important files on my Ubuntu hard drive before I reformatted my Windows hard drive, and now I am unable to access my Ubuntu hard drive due to that error. (/bin/sh: Can't access tty; Job control turned off) 
I don't know much of anything Linux related, but I am an advanced Windows user. I'd appreciate any help I can receive.

:popcorn:

Edit: I don't even need Ubuntu to work as much as I just need to access the files on the hard drive.

---

### Post by pointone on 2008-04-16
When you formatted your Windows drive, you likely changed it's UUID. This would cause errors with Ubuntu trying to mount the drive via its old UUID during boot. 

I'm assuming you drop to a BusyBox prompt after this error. You'll need to edit /etc/fstab and change the UUID for your Windows partition to match the output of "blkid".

---

### Post by Tigairius on 2008-04-16
How would I do that?

---

### Post by pointone on 2008-04-17
Firstly, does it drop you to a prompt where you can enter commands after it fails? If not, your problem lies elsewhere.

If it does, run "blkid" and "cat /etc/fstab" and compare the UUIDs. One of the partitions won't match. Run "nano /etc/fstab" and change the offending entry.

---

