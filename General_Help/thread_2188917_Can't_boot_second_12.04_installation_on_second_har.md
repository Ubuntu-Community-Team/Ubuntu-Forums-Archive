---
title: "Can't boot second 12.04 installation on second hard drive"
date: 2013-11-19
forum: General Help
---

### Post by jsedwards on 2013-11-19
Last week I installed 13.10 on an Dell PowerEdge that is a few years old.  I got it all set up and running fine, just the way I wanted.  But another machine failed and I need to use the Dell temporarily to replace it.  Since the Dell has two (SATA) hard drives, I thought I would use the second drive for this temporary stuff.  I unpacked all of the tarballs from the failed machine onto the second drive, and changed all the configuration things I can think of.  However, I cannot get grub to boot the installation (12.04) on the second drive.  The 13.10 installation boots fine.  I've run update-grub several times and it detects the 12.04 installation.  But when I select Ubuntu 12.04.3 LTS (12.04) from the grub menu I get:

```

error: no such device: 1de61fed-7e6d-4cda-ab80-53dfd35a04ec
error: hd1 cannot get C/H/S values.
error: you need to load the kernel first

```

I can 'e' edit the boot entry for 13.10 and change the kernel to 3.2.0-56 and root=/dev/sdb1 and then it will boot.  But i'm sure if I just edit grub.cfg the next update will write over it.

i just realized i have no idea what the proper way to boot multiple versions of Ubuntu is (like 13.10 and 12.04)?  I assume only one installation should be updating grub?

Thanks for any help!

-scott

---

### Post by jsedwards on 2013-11-20
I tried an interesting experiment last night: I did a clean install of 12.04 on the second hard drive.  When I got to the point where the install asked if I wanted to install grub in the MBR I answered yes.  When I rebooted it wouldn't boot either the newly installed 12.04 on the second hard drive or the original 13.10 on the first hard drive, it just dropped me into "grub rescue>".  I had to boot the 13.10 install disk in rescue mode to restore grub.

So can anybody say that it is possible to have installs of both 12.04 and 13.10 co-exist on a machine and have the grubs play nice with each other?

My new plan, that seems to be working so far, is to install 12.04 on a USB memory stick and when I'm done with it I can just take it out. :)

---

### Post by Bucky Ball on 2013-11-20
You *don't* edit grub.cfg. You edit /etc/default/grub.

13.10 would be upgrading grub as, at this point, 12.04 device is not recognised by grub unless you change grub manually.

Is this: 1de61fed-7e6d-4cda-ab80-53dfd35a04ec

... the correct UUID for the drive with 12.04 LTS on it? Might be an idea to:

1/ run 'sudo blkid' and get the correct UUID for the 12.04 disk;
2/ Check '/etc/fstab' and make sure the line you have for 12.04 has a matching UUID.

You might like to provide the output of 'sudo blkid' and the fstab file here.

*** Just noticed this is now 'Solved'. If this is the case, please share with the community what you did to solve it (forum ettiqutte). Was it this?

> **jsedwards said:**
> 

My new plan, that seems to be working so far, is to install 12.04 on a USB memory stick and when I'm done with it I can just take it out. :)

Thanks. ;)

---

### Post by jsedwards on 2013-11-22
> **Bucky Ball said:**
> 
You *don't* edit grub.cfg. You edit /etc/default/grub.


I don't see any way in /etc/default/grub to specify what installations I want to boot.  For example I have different versions of Ubuntu loaded on the following partions: /dev/sda1 /dev/sdb1 and /dev/sdb2.  In reading the grub info section 5.1 "Simple configuration handling":

   'grub-mkconfig' does have some limitations.  While adding extra
custom menu entries to the end of the list can be done by editing
'/etc/grub.d/40_custom' or creating '/boot/grub/custom.cfg', changing
the order of menu entries or changing their titles may require making
complex changes to shell scripts stored in '/etc/grub.d/'.  This may be
improved in the future.  In the meantime, those who feel that it would
be easier to write 'grub.cfg' directly are encouraged to do so (*note
Booting::, and *note Shell-like scripting::), and to disable any system
provided by their distribution to automatically run 'grub-mkconfig'.

My take on that is that I would have to write a 40_custom or a custom.cfg file to make the menu entries the way I want.  After reading that I think maybe the way to go is take the advice "those who feel that it would be easier to write 'grub.cfg' directly are encouraged to do so" and disable the automatic running of update-grub.  That would solve my problem.

> **Bucky Ball said:**
> 
13.10 would be upgrading grub as, at this point, 12.04 device is not recognised by grub unless you change grub manually.


It doesn't seem like that is true to me.  When I run update-grub on any of the installations, it finds and puts all of them in the boot menu.  But other than the 13.10 installation (on /dev/sda1) they won't boot.

> **Bucky Ball said:**
> 
Is this: 1de61fed-7e6d-4cda-ab80-53dfd35a04ec

 ... the correct UUID for the drive with 12.04 LTS on it? Might be an idea to:

1/ run 'sudo blkid' and get the correct UUID for the 12.04 disk;
2/ Check '/etc/fstab' and make sure the line you have for 12.04 has a matching UUID.


I did check that and it is correct in all the cases.  I don't think it ever gets to the point of reading fstab.  I doesn't even load the kernel.

> **Bucky Ball said:**
> 
You might like to provide the output of 'sudo blkid' and the fstab file here.


/dev/sda1: UUID="9125ccce-fb97-4990-9dbd-a8599205fb4c" TYPE="ext4" 
/dev/sda2: UUID="447dc572-e11d-477c-b359-799ca885252b" TYPE="swap" 
/dev/sda3: UUID="62661774-2afa-4565-9893-316bbe41bbc7" TYPE="ext4" 
/dev/sdb1: UUID="1de61fed-7e6d-4cda-ab80-53dfd35a04ec" TYPE="ext4" 
/dev/sdb2: UUID="ec9b5a23-a840-4113-b0b9-75c75506a529" TYPE="ext4" 
/dev/sdb3: UUID="a7610ec3-d133-4549-a88c-2a17ade97554" TYPE="ext4" 
/dev/sdb4: UUID="3cf351aa-8ae6-4be5-97c8-07d38f74dae9" TYPE="ext4" 

I don't see any point in including fstab (which one?) here.  It is grub that pukes, and as far as I know grub doesn't read fstab??

> **Bucky Ball said:**
> 
*** Just noticed this is now 'Solved'. If this is the case, please share with the community what you did to solve it (forum ettiqutte). Was it this?


Yes, the solution to my overall problem (changing the machine temporarily to boot into a different version) was fixed by booting from a USB memory stick.

The solution to having Ubuntu 13.10 installed on /dev/sda and 12.04 installed on /dev/sdb, is NOT solved.  And from my experience I don't see how that can work automatically out of the box.  The only relatively simple solution I see is editing /boot/grub/grub.cfg by hand and disabling the automatic update grub.  That of course has bad long term consequences.

Thanks!!

---

