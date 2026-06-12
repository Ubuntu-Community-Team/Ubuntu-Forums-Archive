---
title: "Booting into grub.  Help!!"
date: 2018-03-03
forum: General Help
---

### Post by loonsailor on 2018-03-03
I was running just fine, then last night when the system offered me a bunch of upgrades I agreed and walked away.  This morning, I find that my system only boots to the grub prompt.  I've looked around, but most of the advice I've found doesn't work for me.

I tried to find my existing linux file from grub, but it doesn't seem to be anywhere that I can see it.
[ATTACH=CONFIG]278781[/ATTACH]


I am also able to boot UEFI from my bios.  It comes up and gives me the following:

[ATTACH=CONFIG]278782[/ATTACH]


I ran my linux install disk in live mode to see if I could learn anything.  That works, but I'm not sure how to see what's on my hard drive from there, or how to fix it.  I tried update-grub from the live install, but it gives me a cryptic error about being unable to access /cow.  I could do a new install of linux, but if I do that would I trash my existing data, the few programs I've added, etc?

I don't know the exact version of ubuntu, but it was a recent install, from late December.  It's running off an SSD.  It is a single boot system, no Windows or anything else is on the drive.

What should I do?  Please Help!!

---

### Post by oldfred on 2018-03-04
I do not know LVM.

Your first ls command says you have LVM, which means your / (root) is not in a partition but in LVM or logical volumes. The logical volumes are all in one physical partition, but then manual boot has to load /boot which is outside of LVM and then load ubuntu--vg-lvm or whatever. 
Is it also encrypted? Then you have to load extra .mod grub files for LVM & encryption.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If encrypted make sure LVM is mounted & unencrypted before trying fixes.
 
More info on LVM:

 Full-system encryption with manual control and dual-booting Paddy Landau
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627) 
   LVM with encryption Issues with newer kernels 4.13.0-32-generic xenial
[https://ubuntuforums.org/showthread.php?t=2385932](https://ubuntuforums.org/showthread.php?t=2385932) 
   [SOLVED]Secure boot issue - fix with Boot-Repair LVM with encryption
[https://ubuntuforums.org/showthread.php?t=2350963](https://ubuntuforums.org/showthread.php?t=2350963) 

      
 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)
[https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm)
[https://linuxconfig.org/linux-lvm-logical-volume-manager](https://linuxconfig.org/linux-lvm-logical-volume-manager)

---

### Post by loonsailor on 2018-03-04
Thanks for diving in, oldfred.  Boot info is at [http://paste.ubuntu.com/p/F9Tf92mHqt](http://paste.ubuntu.com/p/F9Tf92mHqt).  Very cool!  Now what?

---

### Post by oldfred on 2018-03-04
I still do not know LVM.

But your grub.cfg in the ESP which is a configfile entry 3 lines to chain load to the full grub.cfg in your install.

      ```
 search.fs_uuid d00c9fa7-2d40-4462-a750-8172eb0e76a0 root lvmid/KWNRIp-JQip-oKsi-GHAV-5mD9-0BXw-oF7mqA/m3yeqZ-nxQt-U8iS-FARI-1m4f-4io5-CgKEjX 
set prefix=($root)'/boot/grub' 


```

Mine, but standard partitions:
```
search.fs_uuid 5c1e1a3f-261f-4da5-a0c2-8f479b3039de root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

But note yours is missing last line. Your last line should be same as mine.
So mount your ESP - efi system partition and /EFI/ubuntu/grub.cfg add the configfile entry.

I note that your configuration does not have a /boot partition. Most default installs I have seen have a separate /boot partition which is an ext2 partition outside LVM. And issue has been size of that partition, but new installs make it larger.

Did you partition yourself. I also have seen where /boot is not now required as grub has necessary drivers (.mod files) to load LVM. Do not know if then you may need those in ESP and add insmod lines to load drivers or grub has automatically added those as you have LVM?

If you look in /boot/grub/x86_64-efi folder you will see many xxx.mod files, including lvm.mod.
And in grub the .mod files are added with:
insmod lvm

But that works since grub has path to /boot/grub folder. Not sure how you would even add to ESP configfile grub if needed.

---

### Post by loonsailor on 2018-03-04
Thanks.  I'll try that.  Alternatively, is it safe to let boot-repair do it for me?
```
sudo apt-get install -y boot-repair && boot-repair
```

---

### Post by oldfred on 2018-03-04
You can use Boot-Repair.
But I think the only way that may get updated is if you use the advanced mode and the full uninstall & reinstall of grub.
And if issue is really a bug in grub not adding the last line, that may not work. But should not make it worse.
I would manually add the configfile line first and see if that is the only issue or not.

---

### Post by loonsailor on 2018-03-04
> **oldfred said:**
> 

So mount your ESP - efi system partition and /EFI/ubuntu/grub.cfg add the configfile entry.


Did you partition yourself. I also have seen where /boot is not now required as grub has necessary drivers (.mod files) to load LVM. Do not know if then you may need those in ESP and add insmod lines to load drivers or grub has automatically added those as you have LVM?


Ok, this is probably an embarrassingly dumb question, but how exactly do I do that mount?

I didn&#8217;t do anything out of the ordinary re partitioning.  I simply did the install of an Ubuntu dvd that I burned in December.  I must have answered yes to a question re the LVM, but nothing unusual.

---

### Post by oldfred on 2018-03-04
LVM is one of the install options, but really is for advanced users or if you must have full drive encryption.
If you used the default install option, I would expect you to also have a /boot partition?

From live installer, /mnt is a default location, so you do not have to create it:
       sudo mount -t vfat /dev/sda1 /mnt 
sudo -H nano /mnt/EFI/ubuntu/grub.cfg

If any issues use ll to see where you are at and what directories or paths are there.

I have an ESP on my sdb drive and these  commands worked for me.

```
fred@Z170N:~$ sudo mount -t vfat /dev/sdb1 /mnt 
[sudo] password for fred: 
fred@Z170N:~$ sudo -H nano /mnt/EFI/ubuntu/grub.cfg

```

---

### Post by loonsailor on 2018-03-05
It works!  Adding that one line to /mnt/EFI/ubuntu/grub.cfg solved the problem, and my sys now boots normally.

Thanks, oldfred!

---

