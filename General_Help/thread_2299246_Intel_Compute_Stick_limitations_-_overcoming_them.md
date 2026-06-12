---
title: "Intel Compute Stick limitations - overcoming them"
date: 2015-10-16
forum: General Help
---

### Post by gary68 on 2015-10-16
I just got a new Intel Compute Stick, updated the software, and loaded Mozilla and Thunderbird.
This quickly filled the storage space (~5GB available) on the stick and it became unusable, hanging while booting.

I do have a 128GB Micro SD card installed, does anyone know how I can use this to supplement the internal storage for loading applications?

---

### Post by tgalati4 on 2015-10-17
Welcome to the forums.  What operating system are you using?  Embedded hardware usually needs a lightweight OS and careful management of RAM and storage space.  An SD card is not suited to multiple small file writes and will wear out quickly.  You could use symbolic links to move system directories to the SD card.  Of course /home/user can be moved or set up as a separate partition on the SD card.

---

### Post by gary68 on 2015-10-21
The unit comes with Ubuntu 14.04, 1GB RAM, 8GB storage
Yes the RAM and storage is the problem, mostly the storage. Every time updates are downloaded I lose more space, down to <300MB now!
I have found how to move /home, but this is only a few kB freed up.
A friend told me that the system could be set up so the OS resides on the SD card, leaving the swap partition and others on the internal storage.
From what I have found on this subject it seems moving the root to a partition on the SD card is what I am looking for?
1. does this sound practical, considering your  comment above on writing to the SD card a lot?
2. if so,  is there a guide to doing this somewhere?

I used to play with PCs a lot back in the days of DOS but have not done so for many years now, and I'm quite new to linux having become sick of winblows over a year ago.
I really appreciate any guidance you can give me.

p.s. to anyone thinking of getting one of these compute sticks - buy the windows version (wth 2GB RAM & 32GB storage) then wipe it and load Ubuntu :)

---

### Post by tgalati4 on 2015-10-21
I would follow your own advice.  Get the 2 GB version with 32 gigs of storage.

You can move one system directory at a time to the SD card.  For instance, /usr is about 3.9 GB.  Make a symbolic link to the new location.

```
sudo cp -R /usr /media/SDCARD
```

Wait 10 minutes.  Then verify that every file is there.  Use the correct SD card location--it is probably not /media/SDCARD.

Now for the dangerous part.  Delete the /usr directory to free up some space.  Don't reboot or loose power during this part.

```
sudo rm -rf /usr
```

Make a symbolic link to the new /usr location.

```
cd /
sudo ln -s /media/SDCARD/usr
ls -la
```

You should now have a symbolic link for /usr which saves you about 4 GB of internal storage.  Reboot and hope your system comes up OK.  

Run for a week with this configuration.  If you need more space, pick another directory.  Leave /boot, /bin, and /var alone.  Do only one directory each week until you are satisfied you have a stable system with enough internal storage for future updates.

---

### Post by mastablasta on 2015-10-22
start form Ubuntu minimal and install only what you need. maybe also another desktop environment. anyway... I am not sure why thunderbird and mozila would take up so much space uleess you are downloading emails to your system disk. 

you can also free up some space by using the "sudo apt-get autoremove" command. it will remove old kernels.

I used minimal iso and installed xfce on 8 Gb virtual drive. /swap was minimal, I think 512 MB, ram on virtual machine was set at 1 GB. I was left with between 5 or 6 Gb occupied disk space. so about 2-3 Gb free disk space. this free space can be increased if you install less applications.

you can leave root on internal disk but move installed applications to external SD card. whatever you want. but like I said 8 Gb from what I tried is enough for a working system. so I would leave the applications on system disk if it's faster.

---

### Post by gary68 on 2015-10-22
Cheers tgalati4, this sounds like what I am looking for. If I can move the /usr folder and free up ~4GB that will certainly be enough for what I need.

Thanks for the reply mastablasta.
I'm too much of a newb to Linux to try installing the distro from scratch and customising the install. Also the Compute Stick came with the distro preloaded, and I don't want to risk not having the specific drivers for it, or having to find the drivers on the recovery partition (being a Linux newb and all :) ).

I have run the 'sudo apt-get autoremove' once, and I have been doing a 'sudo apt-get clean' after every OS update to remove the package files.


If I do want to move apps to the sd card, what is involved? i.e. a command list like tgalati4 gave me?
Thanks again

---

### Post by mastablasta on 2015-10-22
> **gary68 said:**
> Thanks for the reply mastablasta.
I'm too much of a newb to Linux to try installing the distro from scratch and customising the install. Also the Compute Stick came with the distro preloaded, and I don't want to risk not having the specific drivers for it, or having to find the drivers on the recovery partition (being a Linux newb and all :) ).

forgot to add this link: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

you don't actually install from scratch you just install in a different way. build the instalation from ground up. as you can see in the link the text based install is quite similar to desktop install with a bit more options present. it still has only a couple of steps.

in the end you get command line interface. you can then just install the whole desktop with "sudo apt-get install *whateveryouneed"*. install lightdm (or gdm) for example, configure it and and you are good to go. you will then boot like you would normally but the desktop will have just basic apps needed to run the desktop efficiently. e.g. file browser, network manager.... it wont have any firefox, Libre office and such. you can also just use a window manager as is done in the link. depends on your goals.

you then add what you want and need. it reduces the size of the OS quite a bit since the default install are deliberately made a bit more full so that users installing the first time have what they usually need and can start with working. but maybe all you want is browser and email application.

my point here is that minimal/netinstall is not as scary as it seems. you can try it in virtual box without worries you would mess things up: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

and it is the basic principle of Linux - it's modular. so you can add, move, remove, replace, modify various components of the OS.

> 
If I do want to move apps to the sd card, what is involved? i.e. a command list like tgalati4 gave me?

yes.

---

### Post by tgalati4 on 2015-10-22
I'm surprised that the Compute Stick came with 14.04; someone did not do the hard work of coming up with a slimmed down distro that really works on this platform.

---

### Post by gary68 on 2015-10-23
Thanks again guys for your help, really appreciated.
I'll give all these things a try when I get the time, and will let you know how successful I've been. Don't hold your breath I only get an hour or two occasionally after work, so it may be a week or two before I have managed to work through these suggestions.

I have VirtualBox on my laptop so that would be a good platform to try out the minimal install method.

Started moving the /usr folder method but got a lot of errors 'can't copy symbolic link' or similar message and when I 'sudo diff -r' on the two folders there seemed to be a lot of differences so I stopped there, I would post the details from the terminal window but there are so many they overflowed the terminal and were lost. here are a few of the diff results, there are literally hundreds of them!

Only in /usr/src/linux-headers-3.16.0-50-generic/arch/x86/tools: Makefile
Only in /usr/src/linux-headers-3.16.0-50-generic/arch/x86: um
Only in /usr/src/linux-headers-3.16.0-50-generic/arch/x86: vdso
Only in /usr/src/linux-headers-3.16.0-50-generic/arch/x86: video
Only in /usr/src/linux-headers-3.16.0-50-generic/arch/x86: xen
Only in /usr/src/linux-headers-3.16.0-50-generic/arch: xtensa
Only in /usr/src/linux-headers-3.16.0-50-generic: block
Only in /usr/src/linux-headers-3.16.0-50-generic: crypto
Only in /usr/src/linux-headers-3.16.0-50-generic: Documentation
Only in /usr/src/linux-headers-3.16.0-50-generic: drivers
Only in /usr/src/linux-headers-3.16.0-50-generic: firmware
Only in /usr/src/linux-headers-3.16.0-50-generic: fs
Only in /usr/src/linux-headers-3.16.0-50-generic/include: acpi


Also, once I have sufficient free space I think the Swap Partition could do with a size increase as I've noticed the system lags quite a bit occasionally if I open too many browser tabs. Will get back to that in due course.

btw, "oooh shiny" wouldn't be a reference to Sluggy Freelance? I used to love that comic strip :)

---

### Post by tgalati4 on 2015-10-23
Yes, I forgot about the symbolic links that don't get copied.  Flip the problem around, copy the binaries to SD and make symbolic links for each one.  Start with the biggest binaries.  Use the 80/20 rule.  80% of the space will be saved with 20^% of the files, so only move the top 20^% in /usr/bin.

---

### Post by zain3 on 2016-01-06
> **gary68 said:**
> Thanks again guys for your help, really appreciated.
I'll give all these things a try when I get the time, and will let you know how successful I've been. Don't hold your breath I only get an hour or two occasionally after work, so it may be a week or two before I have managed to work through these suggestions.

I have VirtualBox on my laptop so that would be a good platform to try out the minimal install method.

Started moving the /usr folder method but got a lot of errors 'can't copy symbolic link' or similar message and when I 'sudo diff -r' on the two folders there seemed to be a lot of differences so I stopped there, I would post the details from the terminal window but there are so many they overflowed the terminal and were lost. here are a few of the diff results, there are literally hundreds of them!

Only in /usr/src/linux-headers-3.16.0-50-generic/arch/x86/tools: Makefile
Only in /usr/src/linux-headers-3.16.0-50-generic/arch/x86: um
Only in /usr/src/linux-headers-3.16.0-50-generic/arch/x86: vdso
Only in /usr/src/linux-headers-3.16.0-50-generic/arch/x86: video
Only in /usr/src/linux-headers-3.16.0-50-generic/arch/x86: xen
Only in /usr/src/linux-headers-3.16.0-50-generic/arch: xtensa
Only in /usr/src/linux-headers-3.16.0-50-generic: block
Only in /usr/src/linux-headers-3.16.0-50-generic: crypto
Only in /usr/src/linux-headers-3.16.0-50-generic: Documentation
Only in /usr/src/linux-headers-3.16.0-50-generic: drivers
Only in /usr/src/linux-headers-3.16.0-50-generic: firmware
Only in /usr/src/linux-headers-3.16.0-50-generic: fs
Only in /usr/src/linux-headers-3.16.0-50-generic/include: acpi


Also, once I have sufficient free space I think the Swap Partition could do with a size increase as I've noticed the system lags quite a bit occasionally if I open too many browser tabs. Will get back to that in due course.

btw, "oooh shiny" wouldn't be a reference to Sluggy Freelance? I used to love that comic strip :)

A very simple solution for this is to downloading a copy of ubuntu and manually install in on a micro sd card, make sure you mount your entire OS on this sd card, now you have the freedom of having you OS disk size be the size of an sd card.


tip. Make sure you use a good quality with fast read and write access micro sd card


i run my compute stick of a physical usb hard drive enclosure without any issues.

---

### Post by Puls8 on 2016-02-04
> **zain3 said:**
> A very simple solution for this is to downloading a copy of ubuntu and manually install in on a micro sd card.
Strange, I've read that the compute stick has UEFI 32-bit bios and that's not the 'natural habitat' Ubuntu. Also the wifi drivers (and sound drivers?) are not available. On the other hand, there is a guy who has made an ubuntu iso for the Compute stick...

BTW: Unity is way too much for the stick, but replacing it with lubuntu makes it shine!:D

---

### Post by C.S.Cameron on 2016-02-04
I purchased the Windows version of Compute Stick for the same reason you suggest.
I love it, but mainly use it for my entertainment center and have not gotten around to installing Ubuntu on it yet.
I also have an old EEEPC with 4GB memory.
I installed Ubuntu to a SD card and ran the EEE from that.
Speed is not an issue if only a few programs are running, as they should be running in RAM.
Only booting should take a little longer.
A proper SD card should have wear leveling and be able to last many years if not decades.
You should not have to worry about messing up the current install, pressing [F8] during boot will activate "Operating System Recovery" and you can reset the stick to Factory spec's.

---

### Post by alex_stathopoulos2 on 2016-05-20
Hello,

I'm encountering the same issue. I followed the steps and noticed that upon deleting the usr folder, sudo (that apparently is included in the bin folder) no longer exists so there is no way to create the link needed for the final step. Apart from that, I'm still trying to figure a way to use the SD for expansion of the system partition as the 8GB are not sufficient, not even for using the system without any extra installations (upon the first update the free space comes down to 50MB). Any recommendations?

Thanks!

---

### Post by dennis_iversen on 2016-05-23
Moving the /usr dir is a good idea. I used rsync and followed this askubuntu guide for moving the usr dir to another partition: 

[http://askubuntu.com/a/668](http://askubuntu.com/a/668)

Please read the comments to the answer, as many says it is better to use rsync than cp (e.g. rsync -aH src dest) as this moves everything correct, e.g. hard links and symbolic links. 

It worked flawless, and I now have 3.9 GB free :)

---

### Post by vmunoz on 2016-06-09
Ubuntu and variant ISOs specifically for Intel Compute Sticks:

[http://linuxiumcomau.blogspot.com.au/2016/06/running-ubuntu-on-intel-compute-stick.html](http://linuxiumcomau.blogspot.com.au/2016/06/running-ubuntu-on-intel-compute-stick.html)

[updated link: 6/26/16]

Just installed Lubuntu on STCK1A8LFC, 1GB RAM, 8GB Storage. Works.

---

