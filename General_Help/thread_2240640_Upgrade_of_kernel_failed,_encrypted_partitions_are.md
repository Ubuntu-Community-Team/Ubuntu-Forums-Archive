---
title: "Upgrade of kernel failed, encrypted partitions are not booting"
date: 2014-08-21
forum: General Help
---

### Post by nicolasdiogo on 2014-08-21
Hello guys,


here is the situation..

my lovely laptop has encrypted disk, so everytime i boot up, it requires me to enter a password.

after the last kernel update i find that it is no longer asking me for a password at boot.

any suggestions?

i have booted with a USB using the same version of Ubuntu LTS and it seems that everything is there.

Many Thanks in Advance!

---

### Post by nicolasdiogo on 2014-08-24
So the disk is fine

But the kernel will not boot as the disk is fully encrypted. 

How do i configure the system to use a password to decrypt the fully encrypted disk. 



Thanks

---

### Post by MrSteve on 2014-08-24
please try recovery mode
hit/hold/press the shift key at boot

this should give you the option of using the last kernel to boot from since the update ...
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by nicolasdiogo on 2014-08-25
Thanks MrSteve

I can not find that option as there is no other kernel available. .

Is there an alternative?

---

### Post by MrSteve on 2014-08-25
i think you are going to need a command line guru to help
so you can install a kernel from the terminal ...

---

### Post by sotiris2 on 2014-08-25
What exactly is happening? Do you get a black screen with an error? "No OS Installed"? 
Can you get to grub if you hold shift while booting? Is /boot also encrypted?

---

### Post by nicolasdiogo on 2014-08-26
hello


thanks for looking into this problem folks,

the system boots into the list of available 'kernels'

there is no counter - normally it would be a counter (30secs)

there is a single entry for Ubuntu
choose that and we find a purple screen that never changes.

i am not sure what info you require.
so i am attaching the grub.cfg

[ATTACH]255836[/ATTACH]

if you would like further info please let me know

i have already taken a copy of the files that i required off this system.

so if the worse comes. it will not be too bad.


thanks,

---

### Post by nicolasdiogo on 2014-08-28
bumping..


there must be a way to tell the kernel to use a password at boot time.
could someone with a full-disk encryption be so kind to publish their **grub.cfg** from their **/boot ** ?


Thanks,

---

### Post by sotiris2 on 2014-08-28
There is my grub.cfg from an install of 14.04.01 on a virtual box. Selected Encrypt whole disk an it auto-selected LVM.

79cd2a72-44ed-44e7-9a00-0f53d20adb44 is my /boot partition (ext2, non encrypted). 

34ba7ccd-add3-464b-93a2-08b2e79923f8 is my encrypted crypt-luks (sda5).  I see no reference to it on the file.

---

### Post by nicolasdiogo on 2014-08-28
Thanks Sotiris2

let me see if i can get it going again.

---

### Post by nicolasdiogo on 2014-08-28
Thanks


i could not find any difference.
maybe somebody could throw some info on this matter?


Cheers

---

### Post by nicolasdiogo on 2014-08-28
sorry 

i could not fix it so i have reintalled the system.

and i am now reloading my personal files.


how annoying!

---

