---
title: "Can't find Ubuntu build"
date: 2015-01-13
forum: General Help
---

### Post by Photobug on 2015-01-13
I have an HTPC build that I use to watch TV on.  I heard some clicking last night and thought I was about to loose a HD.  Turn out it was the case fan die-ing.  I swapped it out for a new one and had to remove some hard drives to get to the fan.  

On start up I am having trouble getting back to the Ubuntu 14 build I was using in the past.

I have two HDs and one SSD onboard this computer.  One of the HDs is a 250 GB one that has nothing on it except for some system information.  I was trying to remove it to get some space for the other HD and SSD for cooling purposes.  However when I try starting the computer without it I get a grub error> and can't start up the computer.  

When I plug in the Hard drive in, it then gives me an option to start up with a variety of Ubuntu builds, but not the one I am looking for.  The one at the top of the list is on one of the Hard Drives and is very slow to start.  I am able to open up another Ubuntu build that is on the SDC which is the SSD so I know it is working.

How can I find the other build on the SSD that is Ubuntu 14 and set up how I like?

---

### Post by TheFu on 2015-01-13
Please run boot-repair and post the resulting URL, assuming that doesn't fix the issue. My signature has directions.

---

### Post by ajgreeny on 2015-01-13
Whqt exactly is this system information on the 250GB HDD?  It sounds as if that is a disk which is home to various grub configuration files that the bootloader looks for when you boot at the moment.

How many different Ubuntu installations do you have?  In theory it should be possible to see what all of them are by booting to your current default OS (the one that manages grub and has the grub configuration files) and running sudo update-grub from that; never mind if it's the slow one, as we are merely doing this to try to find the OS you really want to use.

In theory that should update the grub.cfg and the grub menu of the OS you are using which you could then query with command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-82
``` That ought to list every OS on the machine and show you which drive it is on, and then allow you to boot to whichever one you want; all you need to know is which one is which.

Incidentally, when I was running 5 different ubuntu family OSs on one machine a while ago, just to try out the various versions I always edited /etc/default/grub and changed the line ```
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
```to, as an example ```
GRUB_DISTRIBUTOR="Xubuntu-14.04"
``` and ran ```
sudo update-grub
```
This will change the description of the OS displayed in grub menu to **Xubuntu-14.04**, or whatever you put between those double quote marks, which can be very useful if you have a lot of different ubuntu family OSs.

---

### Post by Photobug on 2015-01-13
> **ajgreeny said:**
> 

Incidentally, when I was running 5 different ubuntu family OSs on one machine a while ago, just to try out the various versions I always edited /etc/default/grub and changed the line ```
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
```to, as an example ```
GRUB_DISTRIBUTOR="Xubuntu-14.04"
``` and ran ```
sudo update-grub
```
This will change the description of the OS displayed in grub menu to **Xubuntu-14.04**, or whatever you put between those double quote marks, which can be very useful if you have a lot of different ubuntu family OSs.

So i have found the Xubuntu 14.04 build it is way down the page on the initial startup it resides on sdc5 and by moving the cursor down the page I can get the OS build I want up and running.  Unfortunately I cant get into the terminal from that build.  I might have the wrong password, although i thought I made it simple but it is not letting me log in.


I went into the top OS option which I imagine is part of the grub on the hard drive.  Through there I was able to get into the terminal and ran the first menu 

```
 grep "menuentry" 
```

the results
```

jordan@htpc-H67MA-UD2H-B3:~$ grep "menuentry" /boot/grub/grub.cfg | cut -c 1-82
menuentry 'Ubuntu, with Linux 3.8.0-37-generic' --class ubuntu --class gnu-linux -
menuentry 'Ubuntu, with Linux 3.8.0-37-generic (recovery mode)' --class ubuntu --c
menuentry 'Ubuntu, with Linux 3.8.0-36-generic' --class ubuntu --class gnu-linux -
menuentry 'Ubuntu, with Linux 3.8.0-36-generic (recovery mode)' --class ubuntu --c
menuentry 'Ubuntu, with Linux 3.8.0-34-generic' --class ubuntu --class gnu-linux -
menuentry 'Ubuntu, with Linux 3.8.0-34-generic (recovery mode)' --class ubuntu --c
menuentry 'Ubuntu, with Linux 3.8.0-33-generic' --class ubuntu --class gnu-linux -
menuentry 'Ubuntu, with Linux 3.8.0-33-generic (recovery mode)' --class ubuntu --c
menuentry 'Ubuntu, with Linux 3.8.0-29-generic' --class ubuntu --class gnu-linux -
menuentry 'Ubuntu, with Linux 3.8.0-29-generic (recovery mode)' --class ubuntu --c
menuentry 'Ubuntu, with Linux 3.2.0-60-generic-pae' --class ubuntu --class gnu-lin
menuentry 'Ubuntu, with Linux 3.2.0-60-generic-pae (recovery mode)' --class ubuntu
menuentry 'Ubuntu, with Linux 3.2.0-59-generic-pae' --class ubuntu --class gnu-lin
menuentry 'Ubuntu, with Linux 3.2.0-59-generic-pae (recovery mode)' --class ubuntu
menuentry 'Ubuntu, with Linux 3.2.0-57-generic-pae' --class ubuntu --class gnu-lin
menuentry 'Ubuntu, with Linux 3.2.0-57-generic-pae (recovery mode)' --class ubuntu
menuentry 'Ubuntu, with Linux 3.2.0-56-generic-pae' --class ubuntu --class gnu-lin
menuentry 'Ubuntu, with Linux 3.2.0-56-generic-pae (recovery mode)' --class ubuntu
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Ubuntu, with Linux 3.13.0-35-generic (on /dev/sdc2)" --class gnu-linux 
menuentry "Ubuntu, with Linux 3.13.0-35-generic (recovery mode) (on /dev/sdc2)" --
menuentry "Ubuntu, with Linux 3.13.0-34-generic (on /dev/sdc2)" --class gnu-linux 
menuentry "Ubuntu, with Linux 3.13.0-34-generic (recovery mode) (on /dev/sdc2)" --
menuentry "Ubuntu, with Linux 3.13.0-32-generic (on /dev/sdc2)" --class gnu-linux 
menuentry "Ubuntu, with Linux 3.13.0-32-generic (recovery mode) (on /dev/sdc2)" --
menuentry "Ubuntu, with Linux 3.8.0-44-generic (on /dev/sdc2)" --class gnu-linux -
menuentry "Ubuntu, with Linux 3.8.0-44-generic (recovery mode) (on /dev/sdc2)" --c
menuentry "Ubuntu, with Linux 3.8.0-42-generic (on /dev/sdc2)" --class gnu-linux -
menuentry "Ubuntu, with Linux 3.8.0-42-generic (recovery mode) (on /dev/sdc2)" --c
menuentry "Ubuntu, with Linux 3.8.0-39-generic (on /dev/sdc2)" --class gnu-linux -
menuentry "Ubuntu, with Linux 3.8.0-39-generic (recovery mode) (on /dev/sdc2)" --c
menuentry "Ubuntu, with Linux 3.8.0-37-generic (on /dev/sdc2)" --class gnu-linux -
menuentry "Ubuntu, with Linux 3.8.0-37-generic (recovery mode) (on /dev/sdc2)" --c
menuentry "Ubuntu, with Linux 3.8.0-35-generic (on /dev/sdc2)" --class gnu-linux -
menuentry "Ubuntu, with Linux 3.8.0-35-generic (recovery mode) (on /dev/sdc2)" --c
menuentry "Ubuntu, with Linux 3.8.0-34-generic (on /dev/sdc2)" --class gnu-linux -
menuentry "Ubuntu, with Linux 3.8.0-34-generic (recovery mode) (on /dev/sdc2)" --c
menuentry "Ubuntu, with Linux 3.8.0-29-generic (on /dev/sdc2)" --class gnu-linux -
menuentry "Ubuntu, with Linux 3.8.0-29-generic (recovery mode) (on /dev/sdc2)" --c
menuentry "Ubuntu, with Linux 3.2.0-68-generic-pae (on /dev/sdc2)" --class gnu-lin
menuentry "Ubuntu, with Linux 3.2.0-68-generic-pae (recovery mode) (on /dev/sdc2)"
menuentry "Ubuntu, with Linux 3.2.0-67-generic-pae (on /dev/sdc2)" --class gnu-lin
menuentry "Ubuntu, with Linux 3.2.0-67-generic-pae (recovery mode) (on /dev/sdc2)"
menuentry "Ubuntu, with Linux 3.2.0-65-generic-pae (on /dev/sdc2)" --class gnu-lin
menuentry "Ubuntu, with Linux 3.2.0-65-generic-pae (recovery mode) (on /dev/sdc2)"
menuentry "Ubuntu, with Linux 3.2.0-61-generic-pae (on /dev/sdc2)" --class gnu-lin
menuentry "Ubuntu, with Linux 3.2.0-61-generic-pae (recovery mode) (on /dev/sdc2)"
menuentry "Ubuntu, with Linux 3.2.0-60-generic-pae (on /dev/sdc2)" --class gnu-lin
menuentry "Ubuntu, with Linux 3.2.0-60-generic-pae (recovery mode) (on /dev/sdc2)"
menuentry "Ubuntu, with Linux 3.2.0-58-generic-pae (on /dev/sdc2)" --class gnu-lin
menuentry "Ubuntu, with Linux 3.2.0-58-generic-pae (recovery mode) (on /dev/sdc2)"
menuentry "Ubuntu, with Linux 3.2.0-57-generic-pae (on /dev/sdc2)" --class gnu-lin
menuentry "Ubuntu, with Linux 3.2.0-57-generic-pae (recovery mode) (on /dev/sdc2)"
menuentry "Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuen
menuentry "Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux 
menuentry "Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --
menuentry "Ubuntu, with Linux 3.13.0-32-generic (on /dev/sdc2)' --class gnu-linux 
menuentry "Ubuntu, with Linux 3.13.0-32-generic (recovery mode) (on /dev/sdc2)' --
jordan@htpc-H67MA-UD2H-B3:~$ 

```

---

### Post by Photobug on 2015-01-13
Since I do not see a sdc5 listed on my

```
 "menuentry" 
```

would running a terminal and inputting the following commands:

> **ajgreeny said:**
>  ```
GRUB_DISTRIBUTOR="Xubuntu-14.04"
``` and ran ```
sudo update-grub
```
This will change the description of the OS displayed in grub menu to **Xubuntu-14.04**, or whatever you put between those double quote marks, which can be very useful if you have a lot of different ubuntu family OSs.

Would this move the Ubuntu 14.04 to the default startup location?

---

### Post by TheFu on 2015-01-13
Dude, that's a bunch of kernels.  Having too many **can** be an issue with disk storage on some default setups (lvm or encryption). /boot getting full is bad - big problem, bad.  The default size for /boot is just too small for too many kernels. Running out of storage during an upgrade can be nasty for someone uncomfortable with grub and partitions.

OTOH, if you only have 1 partition and /boot is part of /, then this will almost never be an issue, beyond confusion.  I keep 3 kernels and have a script that helps me keep them clean on all the systems here.

---

### Post by Photobug on 2015-01-13
> **TheFu said:**
> Dude, that's a bunch of kernels.  Having too many **can** be an issue with disk storage on some default setups (lvm or encryption). /boot getting full is bad - big problem, bad.  The default size for /boot is just too small for too many kernels. Running out of storage during an upgrade can be nasty for someone uncomfortable with grub and partitions.

OTOH, if you only have 1 partition and /boot is part of /, then this will almost never be an issue, beyond confusion.  I keep 3 kernels and have a script that helps me keep them clean on all the systems here.


I have a 250 GB HD that is not used at all.  A 500 GB HD for storage, and an SSD that is 128 GB that is partitioned a bunch of times to be used for a variety of Ubuntu OSs.  I am not sure what the kernels are?  Are they the basic linux builds onto which Ubuntu runs?  How do i get rid of the excess ones?  I believe on my myriad of Hard Drives, SSD and partitions I believe I have at least three or four variations of Ubuntu installs, it looks like it  only shows me the sdc2 partition.

How do I clean up the partitions and kernels?

---

### Post by TheFu on 2015-01-13
That list of Ubuntu's to run when you boot is a list of kernels (pri/recovery) ... so it found 10-20 kernels. I didn't count.  Go into whatever you use as a package manager (synaptic?) and search for "kernel" - remove the oldest ones, but keep the last 2 or 3.

You'll want to do that for every Ubuntu installed on all the hdds connected.  Doing it should update grub automatically.

The storage isn't isn't about total storage - it is about storage in specific partitions for each linux install.

Oh - be careful.

What is a linux kernel? Wikipedia has an article or [http://www.howtogeek.com/howto/31632/what-is-the-linux-kernel-and-what-does-it-do/](http://www.howtogeek.com/howto/31632/what-is-the-linux-kernel-and-what-does-it-do/) is fine. Easily found with google.

---

### Post by Photobug on 2015-01-15
> **TheFu said:**
> That list of Ubuntu's to run when you boot is a list of kernels (pri/recovery) ... so it found 10-20 kernels. I didn't count.  Go into whatever you use as a package manager (synaptic?) and search for "kernel" - remove the oldest ones, but keep the last 2 or 3.

You'll want to do that for every Ubuntu installed on all the hdds connected.  Doing it should update grub automatically.

The storage isn't isn't about total storage - it is about storage in specific partitions for each linux install.

Oh - be careful.

What is a linux kernel? Wikipedia has an article or [http://www.howtogeek.com/howto/31632/what-is-the-linux-kernel-and-what-does-it-do/](http://www.howtogeek.com/howto/31632/what-is-the-linux-kernel-and-what-does-it-do/) is fine. Easily found with google.


I used synaptic to remove old kernels and now the 14.04LTS build will not load  I get a message along the lines 'need to load the kernel first' when trying to start up in this OS.  Obviously I screwed up and deleted something important and now the one OS build I want 'sdc5' is no longer working.

So I booted with a live boot via USB and ran the boot repair.  Here is the report [http://paste.ubuntu.com/9756268/](http://paste.ubuntu.com/9756268/).

During the boot repair it asked if the 250 GB HD is removable and I said no because I wanted to not mess with something that is currently working.  If I was to say no would it move the grub to the sdc SSD allowing me to remove the sda?  I can not do much on any of these setups as I can't remember the password for the root, so I am unable to run sudo on anything other than the liveboot from a 

Is it possible to recover the kernel for sdc5?

---

