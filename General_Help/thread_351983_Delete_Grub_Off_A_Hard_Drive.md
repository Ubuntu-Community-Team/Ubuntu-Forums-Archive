---
title: "Delete Grub Off A Hard Drive"
date: 2007-02-02
forum: General Help
---

### Post by CameronCalver on 2007-02-02
Hello i have drive draws in my computer so if i want to run ubuntu i put the ubuntu drive in and if i want pcbsd i put the pcbsd drive in but i also have a 10gb hd will no os on it to share files between the to but if i add files to it on ubuntu it adds a grub like thing on it so when i boot pcbsd it says grub error 22 but if i take the 10gb hd out it works so why is this how do i stop this from happening

---

### Post by danielph on 2007-02-02
Adding files on a disk will not add grub to that disk, Grub is installed by the installer program or manually. 
Error 22 is No such partition. 

It sounds like the MBR is looking at your 10GB disk to boot from.
Some questions:
Do both disks ubuntu and bsd boot up correctly without the 10GB installed?
Does ubuntu boot correctly with 10GB disk installed?
Was the 10GB disk installed when you installed Ubuntu?
Can you see a /boot folder on any of the 3 disks?

---

### Post by CameronCalver on 2007-02-02
ok right now the hard disk is not inseted and both of the drives are working so leave it at that in fine with how its going

---

### Post by danielph on 2007-02-03
Well it is difficult to work out the solution without more info, but from what you have said it sounds like the computer is booting off the wrong disk. Check out which is the active drive for booting and have a look at boot order in your BIOS when the 3rd disk is present.

If it is booting from the 3rd disk (10GB) this would explain why you are not able to boot.

---

