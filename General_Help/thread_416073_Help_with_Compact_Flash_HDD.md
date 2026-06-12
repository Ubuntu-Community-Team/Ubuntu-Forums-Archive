---
title: "Help with Compact Flash HDD"
date: 2007-04-20
forum: General Help
---

### Post by telovoyagarcar on 2007-04-20
ok.. i have an ubuntu server set up on a normal hard drive, and i just installed a 2GB compact flash card in it, using an IDE adapter, so the bios sees it as a hard drive.
I need to find out where it is being mounted so i can use the "dd" command to flash the card with an image i got already in the main hard disk.
Im trying to follow the instructions to write the ipcop image to the CF, but i cant figure which one of these is the CF or even if it is being listed there:

root@server:~# df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda1 3.7G 1.2G 2.4G 33% /
varrun 188M 44K 188M 1% /var/run
varlock 188M 0 188M 0% /var/lock
procbususb 188M 60K 188M 1% /proc/bus/usb
udev 188M 60K 188M 1% /dev
devshm 188M 0 188M 0% /dev/shm



here are 2 things i dont understand... first is the 3.7G size number for sda1 .
I assume sda1 is the hard drive and this HD is 20GB.. so where is the rest of the space?

And then where is the 2gb flash drive? what are all those 188m mount points?
How can i find the 2gb CF card?

as you can see i am a nooooooobb
thanks a lot guys

---

### Post by telovoyagarcar on 2007-04-20
ok... i see now where the 20 GB are

root@server:~# fdisk -l

Disk /dev/sda: 20.0 GB, 20020396032 bytes
240 heads, 63 sectors/track, 2586 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         521     3938728+  83  Linux
/dev/sda2             522         553      241920    5  Extended
/dev/sda3             554        2586    15369480   83  Linux
/dev/sda5             522         553      241888+  82  Linux swap / Solaris


but still can't find the CF card:confused:

---

