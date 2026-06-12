---
title: "How to remove 8.04"
date: 2008-05-18
forum: General Help
---

### Post by jtheb on 2008-05-18
How do I remove Ubuntu 8.04

---

### Post by roe_polak on 2008-05-18
Are you going to replace it with something else? If you're going back to Windows you could just reformat the partition as NTFS and have extra storage for Windows. Depends on your installation and intentions. We need a little more info.

---

### Post by jtheb on 2008-05-18
I want to put the hard drive back to the original state.
I should have done a manual partition.  Now thw Windows partition is just big enough to hold Windows and no breathing room.  Ubuntu takes up the rest of the hard drive.  Need to re-install but will have to hard drive back to original size first.

---

### Post by roe_polak on 2008-05-18
Hmmm, tough one. You could try using the live cd and start up Gparted. Maybe you can delete the linux partitions (ubuntu + swap) and then resize your Windows partition.
 I'm not sure if it is possible to just resize the windows partition, as I keep my Windows and Linux on separate disks.

Resizing partitions can fail and corrupt partitions. If you can't resize you should consider wiping the hard disk and reinstalling Windows. Thats what i would do.

Remember to backup anything of importance before you do anything.

---

### Post by jtheb on 2008-05-18
Thanks
I reformatted the Ubuntu partitions to NTFS, then deleted them and resized Windows to the original size and am now re-imaging Windows to make sure it is original. Then I will re-install Ubuntu and make sure I manually partition for the new OS  All thanks to Partition Magic to.


BTW  Where does the root and password come into play?  I don't see where to set it.

---

### Post by neo_adi on 2008-05-18
> **roe_polak said:**
> 
Resizing partitions can fail and corrupt partitions. 


i totaly agree with that.. 
it happened to me .. have to totaly lose my data :( 


> **roe_polak said:**
> 
If you can't resize you should consider wiping the hard disk and reinstalling Windows. Thats what i would do.

Remember to backup anything of importance before you do anything.

i wouldn't recommend you to wipe the hard disk rather there are other options too.. 



[LIST=1]
[*]Go online. Download BootITNG. Load it onto a floppy disk. Reboot. Don't install as at this point it is a demo (unless you decided to pay for it). It will take you to a gui. Choose "Partition Work". Voila! You can change your partitions. --It will give you the usual warnings.

or


[*]for the resizing part, you can look up how to use the "resize2fs" command to resize ext2/ext3 partitions, or use a more general partition program like "parted".
[/LIST]


here is the link for the resize2fs online manual 
[http://linux.die.net/man/8/resize2fs](http://linux.die.net/man/8/resize2fs)


**Note**: always while resizing partitions you should backup the Linux installation if it's not taking too much space archive, dd, copy, which suits you best), resize the partitions then copy it back.

As for the bootloader, actually you would only need to boot with a Win98 floppy and run 'fdisk /mbr' to restore the MBR as it was before installing Linux.

---

### Post by roe_polak on 2008-05-18
Root password aren't as such required in Ubuntu as you just log in with your normal user and use 'sudo' (Super User DO) to carry out administrative tasks. If you for some reason need to log in as root you will need to set up a password first.

It is **not** recommended running or logging in as root unless you really, really know what you are doing or just don't care about your system. Using sudo cuts it for me in most cases.

---

### Post by Sef on 2008-05-18
Read [RootSudo]("https://help.ubuntu.com/community/RootSudo") for information on the benefits of sudo.

---

