---
title: "Black Screen to login (with no GUI) on boot"
date: 2020-02-06
forum: General Help
---

### Post by Dan_Bowser on 2020-02-06
Hello,

I think I know what the issue is but I have no idea how to fix it.

Yesterday i was trying to fix a broken package. One piece of advice I got was to disable all third party PPA's. So I did that through the GUI. After I managed to get the package installed I went back to the PPAs I had disabled and re-enabled MOST of them. I think I forgot to re-enable the NVDIA PPA for my graphics driver. (I'm using mesa/dxvk and I need the newest drivers.)

Now when I boot the system I get a black screen with the following,

Ubuntu 18.04.4 LTS uH2 tty1
uH2 login: 

I've tried a few login/password combinations but I can't actually get into the system. I've always used the GUI to login so I remember what the login GUI reported my user name as but that doesn't work as a log in here.

Solutions?
I can create a flashdrive with ubuntu on it and boot from that. The only issue is that I REALLY don't want to reinstall everything so I'd have to boot into some kind of recovery mode and re-enable the NVIDIA PPA. Is this possible?

If someone knows how the system stores login info I might be able to guess the correct login/password and then re-enable the PPA from the terminal.

Other ideas?

I guess let me know what to do. All of my work is on that hard drive, I have a backup on another drive, but I'd still loose a fair bit of work. Maybe a month or more.

Regards

---

### Post by CatKiller on 2020-02-06
You can boot from a live USB to back up your files.

In a standard install the name of your home folder is the same as your user name. 

Disabling the PPA wouldn't do anything to software that was already installed; they're just locations to get new packages from. It's your unspecified broken packages or your unspecified fix that would have broken stuff. From your sparse description it seems like you've removed your display manager, which would be GDM by default if you were using Gnome. 

When booted into the live USB you can chroot into your installed system to run commands - like package management or editing files - as if you'd been able to boot normally.

---

### Post by dragonfly41 on 2020-02-06
Can you use Ctrl+Alt+F1 .. through to Ctrl+Alt+F6 to access shell?

---

### Post by Dan_Bowser on 2020-02-06
Maybe it removed the driver because the PPA was no longer active and the package was seen as obsolete?

Ctrl + Alt + F2 only changes the tty1 to a tty2.

I remember the name of the home folder...

O.K. I just checked it. When I use the name of the home folder as  the login the usual password I used to login through the GUI works. 

I'm at a terminal. Is there anyway to check if NVIDIA drivers are installed and operational? Or should I do something else? I do also have a bootable USB that I made in the last hour.

---

### Post by CelticWarrior on 2020-02-06
> **Dan_Bowser said:**
> Maybe it removed the driver because the PPA was no longer active and the package was seen as obsolete?

It didn't. That's not how it works. How it actually works has been correctly explained above.


> When I use the name of the home folder as  the  login the usual password I used to login through the GUI works. 

As expected, that IS your user. Whatever you were trying before wasn't.
You can check the Nvidia drivers with ```
lsmod | grep nvidia
```

---

### Post by CatKiller on 2020-02-06
> **Dan_Bowser said:**
> I'm at a terminal. Is there anyway to check if NVIDIA drivers are installed and operational? Or should I do something else?

We still don't know what state your machine is in, or the nature of the changes you made to it. If you've got rid of GDM, for example, then you won't have a graphical login regardless of the state of the Nvidia driver. 

There are a bunch of ways to interrogate your system to see the status of your driver. You can see if the package is installed, you can check dmesg, you can read the xorg log, you can use inxi, or any number of other things.

---

### Post by Dan_Bowser on 2020-02-06
The fix I used to get the package installed was just iterations of sudo apt-get update, sudo apt-get install -f, and once I found the PPA that was updating a broken package I used the code suggested in the terminal (I don't remember it exactly something apt-get fix-broken install)

lsmod | grep nvidia
nvidia_uvm      819200  0
nvidia_drm        45056  0
nvidia_modeset 1114112  1
nvidia           19050496 2

From what has been indicated before this output is not helpful?

Since I got to a terminal if you think of something for me to do let me know.

---

### Post by Dan_Bowser on 2020-02-06
chroot into your installed system to run commands - like package  management or editing files - as if you'd been able to boot normally.

The  one guide I found makes this command look unrelated to what I want to  do. They're talking about protecting the OS from new programs by  isolating a new copy of the OS.

All I want is to copy some files from the primary drive and shift them over to the storage drive. Then I can just 0 out the old OS and install the new version. Is there an easy way to do this?

---

### Post by CatKiller on 2020-02-06
> **Dan_Bowser said:**
> All I want is to copy some files from the primary drive and shift them over to the storage drive. Then I can just 0 out the old OS and install the new version. Is there an easy way to do this?

Sure. Just boot from your live USB, mount the old place and the new place, and copy the files that you want to keep from the old place to the new place. 

For chroot, it just means "change root (directory). So if your old install is mounted at /mnt/blah, say, and you chrooted into that, all the commands would be run relative to that "new" root directory: commands that want to read from or write to /etc, for example, would actually be using /mnt/blah/etc (which you want) rather than the /etc on your thumb drive (which you don't want), and those commands have no idea that's happening; as far as they are concerned they're running perfectly normally.

Since you had a normal command line anyway, it's less useful, but sometimes people have messed things up so that they can't boot at all - broken grub, broken fstab, that kind of thing - and having a working environment that isn't busybox can be very useful. And you can have a browser window open at the same time.

---

### Post by Dan_Bowser on 2020-02-07
Hello,

```
sudo fdisk -l
Disk /dev/loop0: 1.9 GiB, 1987817472 bytes, 3882456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 88.5 MiB, 92778496 bytes, 181208 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 54.4 MiB, 57069568 bytes, 111464 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 42.8 MiB, 44879872 bytes, 87656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 149.9 MiB, 157184000 bytes, 307000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 4 MiB, 4218880 bytes, 8240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 14.8 MiB, 15462400 bytes, 30200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 1008 KiB, 1032192 bytes, 2016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 94311439-EF3A-431A-8BFC-77C568A04629

Device           Start       End   Sectors  Size Type
/dev/nvme0n1p1    2048   1050623   1048576  512M EFI System
/dev/nvme0n1p2 1050624 500117503 499066880  238G Linux filesystem


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000b4287

Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1          63 976773119 976773057 465.8G 83 Linux


Disk /dev/sdb: 28.9 GiB, 31043616768 bytes, 60632064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x28004d46

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 60632063 60630016 28.9G  c W95 FAT32 (LBA)


```

It looks like I got the 500 gig storage drive operational, but I'm having problems mounting the drive with the OS on it.

The code,

```
ubuntu@ubuntu:~$ sudo mkdir /media/nvme0n1p1
ubuntu@ubuntu:~$ sudo mount /dev/nvme0n1p1 /media/nvme0n1p1

```

should mount the old primary drive but instead it's mounting the USB drive I booted from.

When I try 

```
sudo mount /dev/nvme0n1 /media/sda6 
mount: /media/sda6: /dev/nvme0n1 already mounted or mount point busy.
```

So it thinks the drive is already mounted but it's not available in the GUI.

Can someone tell me how to mount this other drive?

---

### Post by CatKiller on 2020-02-07
From your fdisk output you should be trying to mount /dev/nvme0n1p2. n1p1 is your EFI partition.

---

