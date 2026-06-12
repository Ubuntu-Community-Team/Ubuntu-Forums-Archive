---
title: "corrupt BIOS, cannot install ubuntu or any OS"
date: 2012-12-19
forum: General Help
---

### Post by pgar23 on 2012-12-19
Hi,
I am working on a Dell Latitude D630 laptop with intel motherboard. This was a previously-working machine that dual-booted Win 7 and ubuntu. The other day I booted the laptop, GRUB2 came up with list of OSs, I chose Win7 and it could not load the OS so I rebooted and chose Ubuntu the next time and could not load that either. Gave it a final reboot, selected Win 7 again, and Win 7 detected a disk error and said it needed to repair. I selected the recovery option but it failed. When I tried to boot the computer again: Error: hd0 out of disk. Then I tried to install fresh copy of ubuntu from 12.04 LiveCD and seen a little message at the bottom "Linux detected corrupt BIOS, kernel something, blah..."  I did a little research. Came across some posts that recommend Boot repair, tried that but boot repair never fixed it (Ran it over-night, checked in the morning and it still show no progress). I thought about trying to flash the BIOS but Dell manufacturer website only offers .exe files that only run when you are capable of loading an OS. This is my dilema...
Can anyone provide assistance, please?? Thanks in advance

P.s. any additional info needed I will provide asap

---

### Post by RedRat on 2012-12-19
Some time ago, Dell used to offer a disk with a skeleton version of DOS that could be loaded on boot. But this sort of implies that you have viable BIOS up and running, that is the first thing that is loaded. If you can't get the BIOS loaded you are pretty much SOL, it is BIOS that loads the initial drivers for the CD and HD in your system, even the memory. You just may have to go to your local computer repair shop and get a replacement BIOS chip. It will have to be compliant with your motherboard. Frankly, it might be far easier to just swap out your current motherboard with a new one, far less hassle.

---

### Post by pgar23 on 2012-12-19
> **RedRat said:**
> Some time ago, Dell used to offer a disk with a skeleton version of DOS that could be loaded on boot. But this sort of implies that you have viable BIOS up and running, that is the first thing that is loaded. If you can't get the BIOS loaded you are pretty much SOL, it is BIOS that loads the initial drivers for the CD and HD in your system, even the memory. You just may have to go to your local computer repair shop and get a replacement BIOS chip. It will have to be compliant with your motherboard. Frankly, it might be far easier to just swap out your current motherboard with a new one, far less hassle.

Thanks RedRat. BIOS is loading but the UbuntuLive CD detected corrupt BIOS and continue to boot into the live cd but couldnt install the OS. So I am only suspecting it is the BIOS...??

---

### Post by Bashing-om on 2012-12-19
pgar23; Hi !

Let's assume the disk is full, thus no operating overhead is available.
Look and see, from the liveCD, activate "disk usage analyzer" .(launcher->search term "disk"->icon beneath->click on "disk usage analyzer")..
[INDENT][INDENT][INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pgar23 on 2012-12-19
> **Bashing-om said:**
> pgar23; Hi !

Let's assume the disk is full, thus no operating overhead is available.
Look and see, from the liveCD, activate "disk usage analyzer" .(launcher->search term "disk"->icon beneath->click on "disk usage analyzer")..[INDENT][INDENT][INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT][/INDENT][/INDENT]
Hi Bashing-om,
Thank you for your reply. The OS is 320GB, 100GB allocated to Windows(NTFS) and 120GB to Ubuntu(EXT4) and nearly 100GB unallocated space so no overheads is unlikely. I just installed the extra HDD I had and am installing fresh copy of Ubuntu as we speak. Hopefully all goes well. Thanks again.

---

### Post by pgar23 on 2012-12-19
Finished installing the HDD and Ubuntu and all is well again. Cheers.

-Thanks

---

### Post by Bashing-om on 2012-12-19
Hey, You do good work !
Please enumerate the steps you took to resolve, to assist next person seeking a similar solution-> and mark this thread as solved.

[INDENT][INDENT]happy ubuntu'n <== BDQ

[/INDENT][/INDENT]

---

### Post by pgar23 on 2012-12-19
> **Bashing-om said:**
> Hey, You do good work !
Please enumerate the steps you took to resolve, to assist next person seeking a similar solution-> and mark this thread as solved.

[INDENT][INDENT]happy ubuntu'n <== BDQ

[/INDENT][/INDENT]

Sure. Good idea. My first post indicates the steps I took before posting here. After posting in the forum, I downloaded "Ultimate Boot CD" iso from google search, used a program named "Unetbootin" to load the iso to my 2GB usb drive, booted the computer and selected HDD (hard drive), then selected the VIVARD option at the bottom to run the diagnostic. The diagnostic came back ok but I ran the error detection and it detected over 320 errors. That immediately indicated to me that there was my problem and I had the extra HDD lying around so thought I would give it a try. Turns out it worked. TA-DA!

---

