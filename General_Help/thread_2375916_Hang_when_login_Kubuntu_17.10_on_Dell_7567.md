---
title: "Hang when login Kubuntu 17.10 on Dell 7567"
date: 2017-10-28
forum: General Help
---

### Post by wilson-leep on 2017-10-28
Hi, i need help and not sure anyone facing the same issue. it hanging when log on, even cant go to terminal mode.i tried install few times are same

Kubuntu 17.10

Computer Information:
    Manufacturer:  Dell Inc.
    Model:  Inspiron 15 7000 Gaming
    Form Factor: Laptop


Processor Information:
    CPU Vendor:  GenuineIntel
    CPU Brand:  Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz
    
Video Card:
    Intel(R) HD Graphics 630
    NVIDIA GeForce GTX 1050 Ti


Memory:
    RAM:  16GB

Disk 
   SSD  256GB
   HDD 1TB

---

### Post by coffeecat on 2017-10-28
Not a Forum Feedback & Help question.

*Thread moved to **General Help**.*

---

### Post by wilson-leep on 2017-10-30
Any one can help?

---

### Post by wilson-leep on 2017-10-31
Hi Dev team, 
   Any solution for Dell 7567 installation?

---

### Post by coffeecat on 2017-10-31
> **wilson-leep said:**
> Hi Dev team, 

Point of information - you won't reach the developer team here. The forum membership consists of volunteers, most of whom are regular users and nothing to do with the development of Ubuntu. I'm sorry that no one has been able to help you so far, but please bump your thread every 24 hours or so until, hopefully, someone will have something to suggest.

---

### Post by vasa1 on 2017-10-31
You could also ask at [https://www.kubuntuforums.net](https://www.kubuntuforums.net) or [https://lists.ubuntu.com/archives/kubuntu-users/](https://lists.ubuntu.com/archives/kubuntu-users/)

---

### Post by linux4me on 2017-11-21
The first thing you need to do is check your BIOS and make sure you have the latest version (1.2.0, released 10/27/2017). If not, flash to the latest version of the BIOS. Doing so seems to have fixed a couple of UEFI errors I was getting, and adds AHCI support if you're using an old version of the BIOS (<1.1, I think). Next, in BIOS setup, make sure you have the SATA mode set to AHCI. 

With those changes, some versions of Ubuntu will install on the 7567 with no issue at all; for example, Ubuntu Mate 16.04.3 works fine. Others, like Ubuntu 17.10 and Ubuntu Mate 17.10, hang at the desktop manager. I was able to get a terminal from there with Ubuntu 17.10, but not with Mate 17.10. The problem seems to be with the video card you have and the nouveau driver in 17.10. 

If you have already installed Ubuntu, and can switch into a terminal from the desktop manager, you don't have to go through the long version below. You can just switch to a terminal and run the following:
```

sudo apt update
sudo apt upgrade
sudo apt install nvidia-384
sudo shutdown -r now

```

Unfortunately, I wasn't able to get a terminal session to come up from the desktop manager. The fix for me was to update the system and install the nvidia-384 driver before rebooting out of the Live session.

I am using full-disk encryption, so my steps are a bit different than what you might use if you aren't using encryption, but here's what I did that worked:
[LIST=1]
[*]Boot with a Live USB, and choose "Try Ubuntu without installing."
[*]Run the installation, but when it finishes, don't restart, choose "continue testing." This way, the encrypted partition is already unlocked.
[*]Open a terminal (Ctrl+Alt+t).
[*]Run ```
sudo fdisk -l
``` to find out the drive designation of your root directory. For me, it was "ubuntu-mate-vg-root".
[*]Mount the root partition using the designation for your installation: ```
sudo mount /dev/mapper/ubuntu-mate-vg-root /mnt
```
[*]Mount the boot partition (if you have one) changing the "sda2" to match your drive designation: ```
sudo mount /dev/sda2 /mnt/boot
```
[*]Mount dev: ```
sudo mount --bind /dev /mnt/dev
```
[*]Run the next line so you have access to the repositories once you chroot: ```
sudo mount --bind /run /mnt/run
```
[*]Chroot and mount the other mount points: ```
sudo chroot /mnt
mount -t proc proc /proc
mount -t sysfs sys /sys
mount -t devpts devpts /dev/pts
```
[*]Update the system with: ```
sudo apt update
sudo apt upgrade
```
[*]Finally, install the nvidia-384 driver: ```
sudo apt install nvidia-384
```
[*]Exit chroot (type exit), then exit the terminal session and reboot.
[/LIST]

I just did this with my 7567 yesterday, and so far, so good. I haven't had any issues.

---

### Post by wilson-leep on 2017-12-23
> **linux4me said:**
> The first thing you need to do is check your BIOS and make sure you have the latest version (1.2.0, released 10/27/2017). If not, flash to the latest version of the BIOS. Doing so seems to have fixed a couple of UEFI errors I was getting, and adds AHCI support if you're using an old version of the BIOS (<1.1, I think). Next, in BIOS setup, make sure you have the SATA mode set to AHCI. 

With those changes, some versions of Ubuntu will install on the 7567 with no issue at all; for example, Ubuntu Mate 16.04.3 works fine. Others, like Ubuntu 17.10 and Ubuntu Mate 17.10, hang at the desktop manager. I was able to get a terminal from there with Ubuntu 17.10, but not with Mate 17.10. The problem seems to be with the video card you have and the nouveau driver in 17.10. 

If you have already installed Ubuntu, and can switch into a terminal from the desktop manager, you don't have to go through the long version below. You can just switch to a terminal and run the following:
```

sudo apt update
sudo apt upgrade
sudo apt install nvidia-384
sudo shutdown -r now

```

Unfortunately, I wasn't able to get a terminal session to come up from the desktop manager. The fix for me was to update the system and install the nvidia-384 driver before rebooting out of the Live session.

I am using full-disk encryption, so my steps are a bit different than what you might use if you aren't using encryption, but here's what I did that worked:
[LIST=1]
[*]Boot with a Live USB, and choose "Try Ubuntu without installing."
[*]Run the installation, but when it finishes, don't restart, choose "continue testing." This way, the encrypted partition is already unlocked.
[*]Open a terminal (Ctrl+Alt+t).
[*]Run ```
sudo fdisk -l
``` to find out the drive designation of your root directory. For me, it was "ubuntu-mate-vg-root".
[*]Mount the root partition using the designation for your installation: ```
sudo mount /dev/mapper/ubuntu-mate-vg-root /mnt
```
[*]Mount the boot partition (if you have one) changing the "sda2" to match your drive designation: ```
sudo mount /dev/sda2 /mnt/boot
```
[*]Mount dev: ```
sudo mount --bind /dev /mnt/dev
```
[*]Run the next line so you have access to the repositories once you chroot: ```
sudo mount --bind /run /mnt/run
```
[*]Chroot and mount the other mount points: ```
sudo chroot /mnt
mount -t proc proc /proc
mount -t sysfs sys /sys
mount -t devpts devpts /dev/pts
```
[*]Update the system with: ```
sudo apt update
sudo apt upgrade
```
[*]Finally, install the nvidia-384 driver: ```
sudo apt install nvidia-384
```
[*]Exit chroot (type exit), then exit the terminal session and reboot.
[/LIST]

I just did this with my 7567 yesterday, and so far, so good. I haven't had any issues.

Thanks, i will try this way and update to here

---

### Post by wilson-leep on 2018-01-07
> **wilson-leep said:**
> Thanks, i will try this way and update to here
Hi, Just to update, it is working, but  notice few things

**Testing BIOS version 1.40, Release Date : 22-Dec-2017**
1. it is still not using Wayland interface, i think this is the reason why don't have issue. because i was try upgrade from 17.04 and it will remain X11 without the issue
2. when using live version, the OS recognize as Virtual Machine and using VM driver for the display,  still not using Wayland

Because i found the point is because of Wayland so the Dell 7567 will hang and unable to login even the terminal

---

### Post by wilson-leep on 2018-01-08
> **linux4me said:**
> The first thing you need to do is check your BIOS and make sure you have the latest version (1.2.0, released 10/27/2017). If not, flash to the latest version of the BIOS. Doing so seems to have fixed a couple of UEFI errors I was getting, and adds AHCI support if you're using an old version of the BIOS (<1.1, I think). Next, in BIOS setup, make sure you have the SATA mode set to AHCI. 

With those changes, some versions of Ubuntu will install on the 7567 with no issue at all; for example, Ubuntu Mate 16.04.3 works fine. Others, like Ubuntu 17.10 and Ubuntu Mate 17.10, hang at the desktop manager. I was able to get a terminal from there with Ubuntu 17.10, but not with Mate 17.10. The problem seems to be with the video card you have and the nouveau driver in 17.10. 

If you have already installed Ubuntu, and can switch into a terminal from the desktop manager, you don't have to go through the long version below. You can just switch to a terminal and run the following:
```

sudo apt update
sudo apt upgrade
sudo apt install nvidia-384
sudo shutdown -r now

```

Unfortunately, I wasn't able to get a terminal session to come up from the desktop manager. The fix for me was to update the system and install the nvidia-384 driver before rebooting out of the Live session.

I am using full-disk encryption, so my steps are a bit different than what you might use if you aren't using encryption, but here's what I did that worked:
[LIST=1]
[*]Boot with a Live USB, and choose "Try Ubuntu without installing."
[*]Run the installation, but when it finishes, don't restart, choose "continue testing." This way, the encrypted partition is already unlocked.
[*]Open a terminal (Ctrl+Alt+t).
[*]Run ```
sudo fdisk -l
``` to find out the drive designation of your root directory. For me, it was "ubuntu-mate-vg-root".
[*]Mount the root partition using the designation for your installation: ```
sudo mount /dev/mapper/ubuntu-mate-vg-root /mnt
```
[*]Mount the boot partition (if you have one) changing the "sda2" to match your drive designation: ```
sudo mount /dev/sda2 /mnt/boot
```
[*]Mount dev: ```
sudo mount --bind /dev /mnt/dev
```
[*]Run the next line so you have access to the repositories once you chroot: ```
sudo mount --bind /run /mnt/run
```
[*]Chroot and mount the other mount points: ```
sudo chroot /mnt
mount -t proc proc /proc
mount -t sysfs sys /sys
mount -t devpts devpts /dev/pts
```
[*]Update the system with: ```
sudo apt update
sudo apt upgrade
```
[*]Finally, install the nvidia-384 driver: ```
sudo apt install nvidia-384
```
[*]Exit chroot (type exit), then exit the terminal session and reboot.
[/LIST]

I just did this with my 7567 yesterday, and so far, so good. I haven't had any issues.


[COLOR=#000000]Hi, Just to update, it is working, but notice few things[/COLOR]

[B]Testing BIOS version 1.40, Release Date : 22-Dec-2017
1. it is still not using Wayland interface, i think this is the reason why don't have issue. because i was try upgrade from 17.04 and it will remain X11 without the issue
2. when using live version, the OS recognize as Virtual Machine and using VM driver for the display, still not using Wayland

Because i found the point is because of Wayland so the Dell 7567 will hang and unable to login even the terminal[/B]

---

