---
title: "black screen ubuntu 12.04 after loading screen"
date: 2013-01-24
forum: General Help
---

### Post by caiorrs on 2013-01-24
hey guys

I have been using ubuntu 11.10 and then I upgraded it to 12.04, i used it for a while.

But yesterday when I chose ubnutu (on GRUB) it appeared the loading screen and then a black screen appears, and nothing happens, I waited like 20 minutes, but its stills in the same situation. I'm using the live usb here, I found some solves, but here they didnt work.

I use ubuntu 12.04 and windows 7 (dual boot)

I appreciate if youcould help me,
Thanks guys =D

---

### Post by caiorrs on 2013-01-24
please help me =S

---

### Post by caiorrs on 2013-01-24
somebody??

---

### Post by Bashing-om on 2013-01-24
caiorrs; Hi !

Could be any number of things causing ubuntu not to load.
Do some basic simple things first and see what results.
Boot upto grub, choose a "recovery" kernel -> choose the fsck option in the recovery menu. When the file system check completes, choose "resume normal boot" .

Do you boot to the desk top ?

[INDENT][INDENT]try'n to help

[/INDENT][/INDENT]

---

### Post by caiorrs on 2013-01-25
I did it but it didnt work, it verified and corrected some issues in the sda1 and sda2, but after this it stopped, and i couldnt return, so I ctrl + alt + del, to restart and it didnt work, i tried something different too, like update the grub, and apt-get update and apt-get upgrade, but it didnt do any effect =S

---

### Post by Bashing-om on 2013-01-25
caiorrs;

Let's assume then that the "black" screen is a result of no driver loaded for the graphics card.
Boot up to the grub menu, insure the latest kernel is highlighted, press the "e" key to edit.
Booting parameters: Arrow down to the line similar to this; "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash"
Arrow across to the term "quiet splash" insert the term "nomodeset" before "quiet splash" -> ctl-x to continue the boot process.
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Do you now boot to the desk top ? If so will advise on a permanent solution.
[INDENT]try'n to help

[/INDENT]

---

### Post by caiorrs on 2013-01-26
just tried this, didnt work too, I entered in a specie of terminal 1 time, and the other times the loading screen frozen in the fifth point (the five points of loanding..)

desperated here D=

---

### Post by Bashing-om on 2013-01-26
caiorrs;

Let's try another approach and delve a bit deeper,
Boot up the recovery mode and choose the root access terminal. Be careful and sure of what you do here - you are ROOT . No mistake is forgiven or reverseble if it affects the system in particular.
What results with this command sequence(oldfred's methology) - ??:Seeing if cleaning and updates resolves the situation.
```
 
#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get autoremove
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
All that does is update it again.

```May have to (re)mount the "root" partition, I do not recall if it is initially mounted as read-only in this option.
With the above done -one command at a time, awaiting results upon completion of each command: Reboot with terminal command:
```
shutdown -r now
```[INDENT][INDENT]boots now to GUI ?
[/INDENT][/INDENT]

---

### Post by caiorrs on 2013-01-26
every command I type i got this error:

E: impossible to write to /var/cache/apt/
E: the lists or the files of status could not be analised or opened

---

### Post by Bashing-om on 2013-01-26
caiorrs;

I am going to theorize that the partition is mounting "read only".

From the recovery mode/root console:
```
mount -o remount,rw /
```Which mounts the root partition "read write".
Now try that command sequence to clean up and update the system.

Reboots to GUI ?

---

