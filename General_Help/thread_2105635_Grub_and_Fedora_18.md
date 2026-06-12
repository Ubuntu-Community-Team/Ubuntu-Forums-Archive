---
title: "Grub and Fedora 18"
date: 2013-01-16
forum: General Help
---

### Post by sentimentGX4 on 2013-01-16
Hello, I'm having a problem where Grub (on Ubuntu 12.04 LTS) cannot detect Fedora 18, even after "sudo update-grub".

>  Device Boot      Start         End      Blocks   Id  System
/dev/sda1           10240   378890239   189440000    7  HPFS/NTFS/exFAT
/dev/sda2       378912766   597964799   109526017    5  Extended
/dev/sda3       597964800   625133567    13584384    7  HPFS/NTFS/exFAT
/dev/sda5       595034112   597964799     1465344    b  W95 FAT32
/dev/sda6       378912768   445530111    33308672   83  Linux
/dev/sda7       576606208   595032063     9212928   82  Linux swap / Solaris
/dev/sda8   *   445532160   446556159      512000   83  Linux
/dev/sda9       446558208   527446015    40443904   8e  Linux LVM
/dev/sda10      527448064   576604159    24578048   83  Linux

Fedora is on sda8 and sda9. Ubuntu is on sda6.

Does anyone have any advice on how I can fix this?

---

### Post by rrich1974 on 2013-01-16
you should mount the fedora partition first, then run the "sudo update-grub"

---

### Post by sentimentGX4 on 2013-01-16
Nope, mounting the Fedora partitions did not work. Well, I managed to mount sda8; but this is the message I'm getting for sda9. (Which explains why "sudo update-grub" didn't work, I guess.)

> ~$ sudo mount /dev/sda9 /mnt
mount: unknown filesystem type 'LVM2_member'


---

### Post by rrich1974 on 2013-01-16
what do you mean by having fedora on two partition? 
what is happening when you try to open the partition in nautilus. 
opening a partition in nautilus automatically mounts it. 
i never mount a partition in terminal. 
on the other hand, maybe fedora 18 had made same changes in its own partition. 
this method have worked for me in fedora 17.....i dont know about 18. i dont use fedora anymore.

---

### Post by sentimentGX4 on 2013-01-16
Well, I don't actually know if Fedora is two partitions. All I know is that when I let Fedora "automatically configure" itself when installing, it created two partitions: a boot partition (sda8) and a second partition (sda9). I cannot manually install Fedora due to a bug. And, yeah, a lot did change in the Fedora 18 installation process. It's a shame because this is two really glitchy releases in a row after the Beefy Miracle debacle and, if I cannot install Spherical Cow, it will mean that I will be leaving Fedora since they're pulling the plug on support for Verne.  

How do you open and mount something on Nautilus? Is it just the default GUI file browser? I am not seeing sda9 under devices at all.

On GParted, I see a red exclamation point next to Fedora's partition (as well as Windows). According to the default GUI file browser, it means that I cannot mount Windows because it is in hibernation. Perhaps I cannot mount Fedora for the same reason?

---

### Post by rrich1974 on 2013-01-16
i dont know what to say since i dont have this situation. 
i used fedora 17 and ubuntu but i installed fedora 17 manually on a 10 GB root partition and grub on its own partition then, update grub from ubuntu. 
the swap partition was used in common by ubuntu and fedora. 
you also can go to windows, install easybcd, rewrite MBR then enter another entry in MBR and install grub in ubuntu partition (also from easybcd) 
or wait for a better answer.

---

### Post by sentimentGX4 on 2013-01-16
Okay, thanks for your help rrich1974!

Upon right clicking sda9 and selecting "information" on GParted, the program explains that the red exclamation point is for "Warning: Logical Volume Management is not yet supported."

---

### Post by grahammechanical on 2013-01-16
> How do you open and mount something on Nautilus? Is it just the default GUI file browser?

Nautilus is a bit more than a file manager. It is closely integrated into the desktop. When we open a partition using Nautilus (File Manager) to access the folders and files on it, we in effect, mount that partition. So, we do not need to run a command in a terminal.

This seems to be the problem

>  I am not seeing sda9 under devices at all.

It is my guess that this is the reason

> "Warning: Logical Volume Management is not yet supported."

sda9 is part of a LVM and is not seen as a separate partition. 

[http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux)]("http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux)")

Regards.

---

### Post by mc4man on 2013-01-16
Didn't have any issue yesterday with a fedora 18 install but - 
created some free space first
used manual partitioning & specified 'regular' partition, not lvm

ubuntu showed on the fedora grub screen & fedora shows fine after switching back to ubuntu grub though did have to mount the fedora partition before updating grub

> $ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-0-generic
Found initrd image: /boot/initrd.img-3.8.0-0-generic
Found linux image: /boot/vmlinuz-3.7.0-7-generic
Found initrd image: /boot/initrd.img-3.7.0-7-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Fedora release 18 (Spherical Cow) on /dev/sda2
done


---

### Post by sentimentGX4 on 2013-01-16
I have the notorious "Error checking storage configuration" bug that the Fedora developers knowingly neglected upon release. -.-

[https://bugzilla.redhat.com/show_bug.cgi?id=854471](https://bugzilla.redhat.com/show_bug.cgi?id=854471)

I'll try installing Fedora on a regular partition. Or maybe I will try using the Fedora bootloader.

---

### Post by oldfred on 2013-01-16
You have to install the lvm2 driver in Ubuntu and then mount Fedora, so grub2 can find it. Then it works.

There is little advantage to LVM if really using it as one partition amount many. It is intended as an entire drive (or more) to make it easy to resize partitions. But it adds a level of complication. Many here multi-booting just install Fedora to a partition.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
lvm info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)

---

### Post by sentimentGX4 on 2013-01-16
> **oldfred said:**
> You have to install the lvm2 driver in Ubuntu and then mount Fedora, so grub2 can find it. Then it works.Thanks for the advice! I didn't realize there were lvm2 drivers available. 

For other newbies out there, here are the commands in order to install lvm2 on Ubuntu.
> sudo -i
apt-get install lvm2
modprobe dm-mod
vgchange -a y

Now Fedora boots fine. Thanks again, everyone!

---

