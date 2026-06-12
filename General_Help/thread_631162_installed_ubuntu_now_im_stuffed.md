---
title: "installed ubuntu now im stuffed"
date: 2007-12-04
forum: General Help
---

### Post by markcaetano@gmail.com on 2007-12-04
hi

um, just installed 6.06 with vista and xp ... now im totally screwed!

vista + xp booted fine. took 6Gb frome each 40 GB partition and installed ubuntu on it.

now when i boot xp works fine BUT

vista partition is totally screwed...not even xp will read it. when i boot from it it says the kernel is missing and i need to install a HAL file

ubuntu: starts to boot then says:

[FONT="Lucida Console"]Uncompressing Linux ... OK, Booting the Kernel
[4294669.222000]RAMDISK:ran out of compressed space
[4294669.222000]invalid compressed format(err=1)
[4294669.222000]Kernel Panic - not syncing:VFS: Unable to mount root FS on unknown-block (0,0)
[4294669.222000] _ [/FONT]

tried reinstalling 4 times with different settings but all i achieved was a dead vista.

installed linux on the clone of this pc and it was fine.

---

### Post by seshomaru samma on 2007-12-04
can you give more information on how you set the triple boot?
it would be best if you boot from the live cd and paste the output of the command :
```
sudo fdisk -l
```
also , did you follow any kind of guide or wiki to set it up?

---

### Post by nqsonk9 on 2007-12-04
Oh, I've heard a lot of complaination about dualing boot with Vista. I wonder is there any difference in the boot methode of Vista compare to XP ?

In your case, you'd better double check your grub and review the partition map.

If your plan is to revive the Vista partition, boot with hiren then  use the mbr utility, hope it'll help. 

After all, those MBR stuff are really annoying for me.

---

### Post by markcaetano@gmail.com on 2007-12-04
the grub has an option for ubuntu then a windows loader which then goes to a second menu where u can choose which windows OS to boot

---

