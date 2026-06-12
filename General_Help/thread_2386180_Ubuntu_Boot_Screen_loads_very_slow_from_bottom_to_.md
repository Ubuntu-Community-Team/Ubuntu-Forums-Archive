---
title: "Ubuntu Boot Screen loads very slow from bottom to top-Tri Boot"
date: 2018-03-01
forum: General Help
---

### Post by asharpjr on 2018-03-01
I just installed Ubuntu for a tri-boot system. I had Windows 10 x64, then installed Windows 7 x64, then I installed Ubuntu. I've done this in the past successfully, however, this time I had issues installing Ubuntu. I had to hit F5 or F6 when installing and then I had to choose nomodeset (See link below). Now when Linux Boot Screen loads, it loads very slowly (like not enough ram) and from bottom of monitor to the top. This can take up to 30 seconds or so. I never noticed this on other installs, only this one.
My system specs are as follows:
Asus Rampage II Extreme MOBO 
Intel i7 920 
12 GB of RAM 
Nvidia 970GTX Video card 
Samsung Evo 840 Pro 1TB (Roughly Partitioned+ 600gb windows 10, 350gb Windows 7 and 50GB Ubuntu. give or take a few.)

I followed this link to install, as I had this exact issue when installing Ubuntu: [https://askubuntu.com/questions/9478...-from-live-usb](https://askubuntu.com/questions/9478...-from-live-usb)

Thanks in advance! 

PS: I'm kinda new to Ubuntu so be gentile when asking specific questions...(give directions)

---

### Post by oldfred on 2018-03-02
With your nVidia card you will need nomodeset to install & boot actual install until you install nVidia driver from Ubuntu repository. Do not install a driver directly from nVidia.

You link does not work. Did you copy from another thread, as then it is shortened (the ... ) and cannot be directly copied.

Are your installs in BIOS mode? Looks like an early UEFI system, first gen Intel i series chips were first that used motherboards with UEFI.

Do you have Windows fast start up off? That is really hibernation which Linux will not correctly see nor use.
But installer may search drive for partitions and take a while to time out on hibernated Windows partitions.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

Which version of Ubuntu.

Nvidia driver issues:
[https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959](https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959)

---

### Post by asharpjr on 2018-03-02
Hi Oldfred! 
Thanks for your help! 

Here is the link that was Broken.. Sorry about that.. 
[https://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics](https://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics)

I'll look at your links over the weekend.

---

### Post by asharpjr on 2018-03-04
> **oldfred said:**
> With your nVidia card you will need nomodeset to install & boot actual install until you install nVidia driver from Ubuntu repository. Do not install a driver directly from nVidia.

You link does not work. Did you copy from another thread, as then it is shortened (the ... ) and cannot be directly copied.  

Are your installs in BIOS mode? Looks like an early UEFI system, first gen Intel i series chips were first that used motherboards with UEFI.

Do you have Windows fast start up off? That is really hibernation which Linux will not correctly see nor use.
But installer may search drive for partitions and take a while to time out on hibernated Windows partitions.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

Which version of Ubuntu.

Nvidia driver issues:
[https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959](https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959)

Hi, Here is the link, sorry about that..  [https://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics](https://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics)

I don't know what you mean about installs in BIOS mode?....???? I had windows 10 then I installed 7, then Ubuntu 16.04 LTS using a bootable USB using Rufus. 

I also have fast start up turned off in Windows side.

---

### Post by oldfred on 2018-03-04
If Windows 10 is directly from PC vendor on newer systems, it must be UEFI.
But almost all Windows 7 systems are BIOS installs and DVD is BIOS only and must be modified on flash drive for UEFI install.
And if a user installs Windows 10, it may be UEFI or BIOS depending on how installer is booted, if system is newer UEFI hardware.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by asharpjr on 2018-03-05
This PC was a self built PC for gaming. I just use this one as a  secondary one now, with a Tri-boot system. It works fine if I put in an  old Video card (AMD) I now have an Nvidia GTX970. I believe it's a  driver issue, but I can't quite figure it out....

---

### Post by oldfred on 2018-03-06
If nVidia you have to boot with nomodeset until you install correct nVidia driver from repository.
You may want to add ppa to get newest driver, but do not download from nVidia directly.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]https://wiki.ubuntu.com/Kernel/KernelBootParameters

      [/URL]
 [https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959](https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959) by 1fallen
> EDIT: This seems to work for my card here, instead of using "nomodeset" I am using this "nogpumanager"
And I have to watch carefully any changes made to "/etc/X11/xorg.conf" 
   nVidia must Purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351) 

    [URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]
[/URL]

---

### Post by asharpjr on 2018-03-07
> **oldfred said:**
> If nVidia you have to boot with nomodeset until you install correct nVidia driver from repository.
You may want to add ppa to get newest driver, but do not download from nVidia directly.

Sorry, I don't really know what you mean. I"m kinda new to Linux. I want to learn..I'm great with Windows, but it's a terrible OS....lol

---

### Post by oldfred on 2018-03-07
See links in post #7, they also show screen shots so you can know better what you are doing.

---

### Post by asharpjr on 2018-03-10
Are you taking about this post/link?

How to add boot parameters, grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

Sorry, been checking this update on my phone. I'll be in my pc again soon. I'm just so confused..

---

### Post by oldfred on 2018-03-10
That shows grub menu.
You may have to press escape to get grub menu after UEFI but before boot starts. And if UEFI fast boot is on, you may not have time, and even then you have to be quick.
Then replace quiet splash with nomodeset.

---

