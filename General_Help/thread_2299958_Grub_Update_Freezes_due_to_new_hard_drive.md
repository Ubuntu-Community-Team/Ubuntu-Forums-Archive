---
title: "Grub Update Freezes due to new hard drive"
date: 2015-10-22
forum: General Help
---

### Post by Bowei_Zhao on 2015-10-22
I recently put a new hard drive into my desktop.

The day after I did that, my 'apt-get' stopped working and I found it was due to Grub not being able to complete.

Anytime sudo update-grub is run, it will generate this:
```

bowei@bowei-Linuxbook:~$ sudo update-grubGenerating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
^C


^X


^Z
[2]+  Stopped                 sudo update-grub



```

I have to manually stop it because it never completes.

I have googled this and found other resources which including excluding that drive from Grub, and stopping OS-Prober.

Disabling OS Prober fixes my issues and lets me actually use Ubuntu again

Problem now is that when I boot up my PC, Grub doesn't show Windows anymore.....of course not. 

I've read conflicting documents on how to edit out a partition (and am scared of messing stuff up).

I mess around with my hard drive positions a lot as this is a desktop which is why I don't want to 'hardcode' a hard drive sdb or sda into my grub as it may very well not be that later on.

These are my disks:
```

bowei@bowei-Linuxbook:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931.5G  0 disk 
&#9492;&#9472;sda1   8:1    0 931.5G  0 part 
sdb      8:16   0 223.6G  0 disk 
&#9500;&#9472;sdb1   8:17   0   350M  0 part 
&#9500;&#9472;sdb2   8:18   0 179.3G  0 part 
&#9500;&#9472;sdb3   8:19   0     1K  0 part 
&#9492;&#9472;sdb5   8:21   0    44G  0 part /
sdc      8:32   0 465.8G  0 disk 
&#9492;&#9472;sdc1   8:33   0 465.8G  0 part 
sdd      8:48   0   1.8T  0 disk 
&#9492;&#9472;sdd1   8:49   0   1.8T  0 part 
sde      8:64   0   1.8T  0 disk 
&#9492;&#9472;sde1   8:65   0   1.8T  0 part /media/bowei/test
sr0     11:0    1  1024M  0 rom  
bowei@bowei-Linuxbook:~$ 



```

I can't run boot-repair as it is stuck on the OS-Prober scanning systems page as well so I can't use it to give you guys a boot-info.

Windows is on the 223.6G hard drive which is sdb2 here.

I believe Linux is installed on sdb5. sde1 is my external hard drive.

I may install other OS's on the other drives but honestly... I just want my stuff to work.

Shutting down, unplugging the new hard drive, booting back in and running sudo update grub gives me no issues at all though

> 
 bowei@bowei-Linuxbook:~$ sudo lsblk[sudo] password for bowei: 
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931.5G  0 disk 
&#9492;&#9472;sda1   8:1    0 931.5G  0 part 
sdb      8:16   0 223.6G  0 disk 
&#9500;&#9472;sdb1   8:17   0   350M  0 part 
&#9500;&#9472;sdb2   8:18   0 179.3G  0 part 
&#9500;&#9472;sdb3   8:19   0     1K  0 part 
&#9492;&#9472;sdb5   8:21   0    44G  0 part /
sdc      8:32   0 465.8G  0 disk 
&#9492;&#9472;sdc1   8:33   0 465.8G  0 part 
sdd      8:48   0   1.8T  0 disk 
&#9492;&#9472;sdd1   8:49   0   1.8T  0 part /media/bowei/test
sr0     11:0    1  1024M  0 rom  
bowei@bowei-Linuxbook:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-31-generic
Found initrd image: /boot/initrd.img-3.19.0-31-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found Windows 8 (loader) on /dev/sdb1
Found Windows 8 (loader) on /dev/sdb2
done
bowei@bowei-Linuxbook:~$ ^C




but this isn't what i need. I want my new hard drive....to work


Any help please?

---

### Post by oldfred on 2015-10-22
What is new drive?
Does BIOS/UEFI see it correctly?

How is it partitioned? Did you copy anything to it yet?

Post these with new drive plugged in:
sudo parted -l
sudo blkid

---

