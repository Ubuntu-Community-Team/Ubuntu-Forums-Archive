---
title: "adding hard drive"
date: 2007-01-13
forum: General Help
---

### Post by feest on 2007-01-13
Hi all, when i try to add my drive with my previous installation to put over some files linux cannot boot, it gives some weird error and drops to a terminal wich can only run certain administration tasks. how do i boot with that other disk?

---

### Post by kebes on 2007-01-13
First off, double check that you've added the hard drive with the right master/slave settings. If both hard-drives are on the same IDE chain, you'll need to make sure that the primary drive (with Ubuntu OS on it) has a jumper set to "master" and the other drive is set to "slave".

On some newer IDE setups, it's actually the IDE cable that controls which one is master and slave. The cable will have a black, blue, and grey connector. (Blue connects to motherboard, black to master drive, grey to slave.) You may have to set both drives jumpers to 'cable select' in this case.



If that doesn't fix it, then you can try booting into a LiveCD and work from there. If you only need to copy the files (and after that you will remove the second hard drive) then you can just use the LiveCD to copy over the files you want.

If you want the second hard driver permanently connected, then use the LiveCD to re-install grub so that it now boots properly. To do this involves opening a terminal and using "grub" or "grub-install" to reinstall grub based on the new hardware setup. Something like:

grub-install /dev/hda

You'll have to check the grub documentation and your hardware setup. For instance if you're using SATA drives then it would be "grub-install /dev/sda" and if you want to install grub to a partition instead of the master boot record, you'll have to modify the commands appropriately.

---

### Post by kebes on 2007-01-13
> **feest said:**
> it gives some weird error?

It would also help if you could exactly describe that error!

---

### Post by feest on 2007-01-15
well i cannot discribe the error since i'm not able to connect to inet with it. but i can try a live boot thx for that, further i do not use ide disks they are both sata so i cannot give them master slave settings.

---

### Post by kebes on 2007-01-17
> **feest said:**
> i do not use ide disks they are both sata so i cannot give them master slave settings.

On some motherboards, the SATA connectors are numbered, and the drive you boot from actually has to be SATA0 (or SATA1 or whatever) for it to work properly. On other motherboards it doesn't matter. Check the manual for your motherboard.

[QUOTE=feest]ubuntu did not recognised it and crashed to somekind of terminal.[/quote]

If I'm understanding correctly, Ubuntu crashes when the second hard drive is installed, right? Does Ubuntu boot normally with that second drive disconnected?

> you said that i should reinstall grub but before i'm gonna do this i wann ask you if you're sure because it passes the grub stage and boots the correct edgy disk.

Well if it passes the grub part of the boot then I guess that's not the problem... so don't reinstall grub just yet.


> you also said that i should copy my files from one disk to another using my live cd but the live cd is not able of mounting disks (maybe damn small linux is gonna try soon) so that isn't gonna work either.

So you're saying that you can boot into the LiveCD session? If so, this is progress... you can then try mounting the drive manually using the commandline. See instructions here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)

While in the LiveCD session you can also try doing disk checks using the command "fsck". If it reports errors, post them here.

> now my third thing is that once i mounted my new disk to my other install and i install windows on the old one will this erase grub? note that grub is installed on the other disk.

In all likelihood, after installing Windows you will lose your master boot record and have to reinstall grub. There is no way to prevent Windows from doing this. But, re-installing grub from a LiveCD is quite easy.


Hope that helps... if you're still running into problems, please describe the problem in detail and post any error messages you see!

---

### Post by feest on 2007-01-18
> On some motherboards, the SATA connectors are numbered, and the drive you boot from actually has to be SATA0 (or SATA1 or whatever) for it to work properly. On other motherboards it doesn't matter. Check the manual for your motherboard.


> If I'm understanding correctly, Ubuntu crashes when the second hard drive is installed, right? Does Ubuntu boot normally with that second drive disconnected?

ubuntu boots probably with only one disk, with the other disk installed it crashes to a terminal like thing, (not a complete terminal) i will make a picture of it soon (if this is readable). 


> Well if it passes the grub part of the boot then I guess that's not the problem... so don't reinstall grub just yet.
ok.


> So you're saying that you can boot into the LiveCD session? If so, this is progress... you can then try mounting the drive manually using the commandline. See instructions here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)

yeah, will try to mount disks in damn small linux ([www.damnsmallinux.org](www.damnsmallinux.org)) to copy files, then i can try to mess up the old disk XD


> While in the LiveCD session you can also try doing disk checks using the command "fsck". If it reports errors, post them here.

tried that, i failed (not really an expert in mounting) but dsl is able to mount from live cd


> In all likelihood, after installing Windows you will lose your master boot record and have to reinstall grub. There is no way to prevent Windows from doing this. But, re-installing grub from a LiveCD is quite easy.

sigh, ok...


> Hope that helps... if you're still running into problems, please describe the problem in detail and post any error messages you see!

ok.

---

