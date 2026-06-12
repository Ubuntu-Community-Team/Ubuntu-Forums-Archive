---
title: "[SOLVED] Ubuntu 7.10 won't start normally"
date: 2008-01-01
forum: General Help
---

### Post by White_Panther on 2008-01-01
First I wanted to say that I am new to Linux and that I am glad I made the change,  Also Happy New Year!!!!

Now my problem is that in my laptop I recently installed OpenSUSE and Ubuntu as dual boot OS.  I did not like Open SUSE that much and decided to format the partition that held that OS.  I used Ubuntu's version of partition manager.  Now Open SUSE was installed in a partition ahead of Ubuntu (don't know if this changes anything) and now when I try starting my Ubuntu from the GRUB it will no let me start normally, I need to always go to recovery mode.  Now before it starts it reports a problem with
 "* <=(red) File system check failed
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually"

Which I have no Idea how to, and then it continues

"A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@mylaptop-laptop:~#            "

If I hit ctrl+d twice it will boot and everything seems fine.  Except that at the end it, before shutting down it tells me the system is shutting down in red letters.

Any help would be great,  Otherwise I will need to do a clean install.

PS: My laptop is a Toshiba Satellite A215-S4697 with AMD Turion64 TL52

---

### Post by ~LoKe on 2008-01-01
Type this into the terminal:
```
sudo fdisk -l
```
You might have to fsck the drives..

---

### Post by White_Panther on 2008-01-01
Thanks for the quick response

I tried that and this the message I got is:

"Command 'sudo' is available in '/usr/bin/sudo'"

So I ran that directory and it just shows the three partitions that I have.

---

### Post by ~LoKe on 2008-01-01
What's the name of the device?  Something like /dev/sda?

Boot up a LiveCD or something similar and try to fsck the partition.

```
fsck /dev/sda1
```

---

### Post by White_Panther on 2008-01-01
~LoKe thanks for the quick responses.

this is what I got after running fsck

ejkennedy@ejkennedy-laptop:~$ fsck /dev/sda4
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda4 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

fsck.ext3: Permission denied while trying to open /dev/sda4
You must have r/w access to the filesystem or be root
ejkennedy@ejkennedy-laptop:~$ 
ejkennedy@ejkennedy-laptop:~$ fsck /dev/sda3
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda3 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

fsck.ext3: Permission denied while trying to open /dev/sda3
You must have r/w access to the filesystem or be root
ejkennedy@ejkennedy-laptop:~$ fsck /dev/sda1
fsck 1.40.2 (12-Jul-2007)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda1
ejkennedy@ejkennedy-laptop:~$

---

### Post by ~LoKe on 2008-01-01
Eek!  I said boot up a LiveCD.  You want to fsck a partition that isn't mounted, or you could do damage.

---

### Post by White_Panther on 2008-01-01
from the live CD it gives me the same message

---

### Post by ~LoKe on 2008-01-01
While in the LiveCD, try typing this:
```
sudo umount /dev/sda
```
What does it output?

---

### Post by White_Panther on 2008-01-01
I tried to do that on all of the partitions and it said that non of them are mounted,  BTW Ubuntu is loaded on sda4, swap is on sda1, sda3 is free space, and sda2 was opensuse

---

### Post by White_Panther on 2008-01-01
```
umount: /dev/sda4: not mounted
```

---

### Post by ~LoKe on 2008-01-01
If it's not mounted, try...
```
sudo fsck /dev/sda4
```
If it says it's mounted, do not proceed!

---

### Post by White_Panther on 2008-01-01
This is the output from fsck on sda4

```
fsck 1.40.2 (12-jul-2007)
e2fsck 1.40.2 (12-jul-2007)
/dev/sda4: clean, 115823/3227648 files, 705080/6446081 blocks
```

---

### Post by ~LoKe on 2008-01-01
> **White_Panther said:**
> This is the output from fsck on sda4

```
fsck 1.40.2 (12-jul-2007)
e2fsck 1.40.2 (12-jul-2007)
/dev/sda4: clean, 115823/3227648 files, 705080/6446081 blocks
```

Cool, now try it on the other partitions.

---

### Post by White_Panther on 2008-01-01
```
fsck 1.40.2 (12-jul-2007)
e2fsck 1.40.2 (12-jul-2007)
/dev/sda3: clean, 817/13434880 files, 473275/26856663 blocks

fsck 1.40.2 (12-jul-2007)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda1
```

And sda2 does not exist any longer, since I formatted

---

### Post by ~LoKe on 2008-01-01
You...you formatted your swap partition?  You might have to run gparted again and format it to a valid swap filesystem.  I suggest waiting for someone to come along who's more familiar with that process.

---

### Post by White_Panther on 2008-01-01
I can see the swap partition on sda1 using gparted

---

### Post by White_Panther on 2008-01-01
reinstalled ubuntu and it works fine now

---

