---
title: "System Configuration Question"
date: 2017-05-04
forum: General Help
---

### Post by randomfluker4000 on 2017-05-04
[TABLE="class: grid, width: 1000"]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[/TR]
[TR]
[/TR]
[/TABLE]

                        [TABLE]
[TR]
[TD]             [CENTER]System Configuration,             AMIBIOS Version 4.6.5.1[HR][/HR]
[/CENTER]
[/TD]
[/TR]
[TR]
[TD]             CPU type            : Interl( R ) Pentium             ( R ) CPU G640  @  2.80GHZ , 2000 MHz[HR][/HR][/TD]
[/TR]
[TR]
[TD="width: 100%"]             [TABLE="width: 500"]
[TR]
[TD]   Build Date          : 03/19/2012[/TD]
[TD]   System ROM : E000 &#8211; FFFF[/TD]
[/TR]
[TR]
[TD]   System Memory : 634 KB[/TD]
[TD]    Extended Memory : 1988 MB[/TD]
[/TR]
[TR]
[TD]   Total Memory     : 2048MB (DDR3 1067) [/TD]
[TD]   COM Ports  : None[/TD]
[/TR]
[TR]
[TD]   PS/2 Mouse        : Installed   [/TD]
[TD]    Display Type : EGA\VGA[/TD]
[/TR]
[/TABLE]
[HR][/HR][/TD]
[/TR]
[TR]
[TD="width: 100%"]             USB Mass Devices:
[TABLE="width: 500"]
[TR]
[TD]USB MASS #1:Generic-Multi-Card 1.00[/TD]
[TD]                        USB MASS #2:LG USB Drive 1100[/TD]
[/TR]
[/TABLE]
[HR][/HR][/TD]
[/TR]
[TR]
[TD="width: 100%"]             PCI Devices: (I won&#8217;t list em because             the list is long and I believe it is unnecessary for my question)[/TD]
[/TR]
[/TABLE]


Does any one see something weird (out of ordinary) ? Don't quite understand computers but why is extended memory 1988 MB when the total is 2048 ? And why does the ROM read only E000-FFFF sector ? Can some one explain ?

Side note: I have a weird SYSLinux 6.03 installed and running  when I never Installed SYSLinux in my life.Heck I don't even understand what SYSLinux is. How can that happen ?

---

### Post by #&amp;thj^% on 2017-05-04
Looks fine to me.
BTW SYSLinux is installed from the install process.
```
apt policy syslinux
syslinux:
  Installed: 3:6.03+dfsg-14.1
  Candidate: 3:6.03+dfsg-14.1
  Version table:
 *** 3:6.03+dfsg-14.1 500
        500 http://us.archive.ubuntu.com/ubuntu zesty/main amd64 Packages
        100 /var/lib/dpkg/status


```

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.8G     0  3.8G   0% /dev
tmpfs           770M   10M  760M   2% /run
/dev/sda1       293G  9.2G  269G   4% /
tmpfs           3.8G     0  3.8G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.8G     0  3.8G   0% /sys/fs/cgroup
tmpfs           770M   16K  770M   1% /run/user/120
tmpfs           770M  4.8M  766M   1% /run/user/1000


```

And your memory:
```
free
              total        used        free      shared  buff/cache   available
Mem:        7883212     1256804     5375416      214816     1250992     6141084
Swap:       2097148           0     2097148


```

---

### Post by randomfluker4000 on 2017-05-04
so ... SYSLinux install its self randomly even when you are using Windows 7 or 10 ?????

---

### Post by wildmanne39 on 2017-05-04
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

### Post by #&amp;thj^% on 2017-05-04
[h=4]Using a Linux boot loader[/h] You may use [GRUB]("https://wiki.archlinux.org/index.php/GRUB#Dual-booting") or [Syslinux]("https://wiki.archlinux.org/index.php/Syslinux#Chainloading"). 

You will have to do some reading here.

---

### Post by randomfluker4000 on 2017-05-04
> **1fallen said:**
> **Using a Linux boot loader**

 You may use [GRUB]("https://wiki.archlinux.org/index.php/GRUB#Dual-booting") or [Syslinux]("https://wiki.archlinux.org/index.php/Syslinux#Chainloading"). 

You will have to do some reading here.

OK ... Let me put this time the questions this way : How to uninstall SYSLinux ? Like I said I never Installed SYSLinux - don't know what that is even.I'm a casual Windows user but Windows start giving blue screens of death and now it ruins my HDD.It corrupts it - dont know how but that happens.I had to start using Ubuntu on a USB stick ..... the point is I never Installed SYSLinux I was never using Linux in my life until this point.One day out of the blue sky my Win 7 start giving Blue Screens and after the first one I had SYSLinux installed that was running after boot - HOW - I DON'T EVEN KNOW .... SO Just tell a windows user how to uninstall  SYSLinux witch he have on his computer but never installed .... a user who never used Linux until this time of "need" ..... gee I don’t wanna read and learn how to use a Linux or computer deeper than clicking Microsoft made icons...

---

### Post by ian-weisser on 2017-05-04
> **randomfluker4000 said:**
> Side note: I have a weird SYSLinux 6.03 installed and running  when I never Installed SYSLinux in my life.Heck I don't even understand what SYSLinux is. How can that happen ?

What makes you believe that you have SYSLinux installed?
Do you believe it to be installed on your hard drive, or on your USB stick?

Syslinux is a common bootloader used on bootable USB sticks.
Did you perhaps boot from a USB stick to work around your Windows problem?

---

### Post by #&amp;thj^% on 2017-05-04
> **randomfluker4000 said:**
> OK ... Let me put this time the questions this way : How to uninstall SYSLinux ? Like I said I never Installed SYSLinux - don't know what that is even.I'm a casual Windows user but Windows start giving blue screens of death and now it ruins my HDD.It corrupts it - dont know how but that happens.I had to start using Ubuntu on a USB stick ..... the point is I never Installed SYSLinux I was never using Linux in my life until this point.One day out of the blue sky my Win 7 start giving Blue Screens and after the first one I had SYSLinux installed that was running after boot - HOW - I DON'T EVEN KNOW .... SO Just tell a windows user how to uninstall  SYSLinux witch he have on his computer but never installed .... a user who never used Linux until this time of "need" ....._** gee I don&#8217;t wanna read and learn how to use a Linux or computer deeper than clicking Microsoft made icons...**_


As you wish:

You can restore the Windows bootloader with a Windows 7/8/8.1/10 DVD.

  1)  Put the DVD in your optical drive and boot from it.

  2)  Press a key when it displays Press any key to start from CD or DVD.

  3) Select your language etc. and click Next.

  4)  Click Repair your computer.

  5)  Click Troubleshoot.

  6)  Click Advanced Options.

  7)  Click Command Prompt.

  8)  In the command prompt window, type bootrec /fixmbr

  9)  Click the red X to close the command prompt.

    Click Turn off your PC.

    Turn the PC back on and it should boot directly into Windows.

This leaves the Ubuntu partition on your hard drive/USB or SSD. To remove it:

    Hit Windows+X and select Disk Management.

    Find the Ubuntu partition. It will probably be a large partition without a drive letter.

   **[COLOR=#ff0000] ***Be sure you have the correct partition!***[/COLOR]**

    Right-click the partition and delete or reformat it with a Windows filesystem.

There you go...and happy windowing.
Tip: before you go exploring different OS's like linux....best to know what you are doing beforehand.

**And before you undergo my instructions...Please read and answer ian-weisser Post**
And happy Trails

---

### Post by randomfluker4000 on 2017-05-04
> **ian-weisser said:**
> What makes you believe that you have SYSLinux installed?
Do you believe it to be installed on your hard drive, or on your USB stick?

Syslinux is a common bootloader used on bootable USB sticks.
Did you perhaps boot from a USB stick to work around your Windows problem?

There is black screen with two _ _ that shows up like this after the BIOS screen: 
"
_
_
"
I used camera to record what is shows and for less than a second there was: 

"
SYSLinux 6.03 EDD 2012-10-06 Copyright ( there is more things here but my camera didn't capture them)
Loading boo logo
_
Initializing gfx code
_
"

Edit: it is "Loading boot logo" made a typo.

---

### Post by ian-weisser on 2017-05-04
> **randomfluker4000 said:**
> "
SYSLinux 6.03 EDD 2012-10-06 Copyright ( there is more things here but my camera didn't capture them)
Loading boo logo
_
Initializing gfx code
_
"

Edit: it is "Loading boot logo" made a typo.

You are booting a Linux system when that occurs. Syslinux is the bootloader for that Linux system.
If you wish to stop using Syslinux, then cease using bootable USB stick that you created.

---

### Post by randomfluker4000 on 2017-05-04
> **1fallen said:**
> As you wish:

You can restore the Windows bootloader with a Windows 7/8/8.1/10 DVD.

  1)  Put the DVD in your optical drive and boot from it.

  2)  Press a key when it displays Press any key to start from CD or DVD.

  3) Select your language etc. and click Next.

  4)  Click Repair your computer.

  5)  Click Troubleshoot.

  6)  Click Advanced Options.

  7)  Click Command Prompt.

  8)  In the command prompt window, type bootrec /fixmbr

  9)  Click the red X to close the command prompt.

    Click Turn off your PC.

    Turn the PC back on and it should boot directly into Windows.

This leaves the Ubuntu partition on your hard drive/USB or SSD. To remove it:

    Hit Windows+X and select Disk Management.

    Find the Ubuntu partition. It will probably be a large partition without a drive letter.

   **[COLOR=#ff0000] ***Be sure you have the correct partition!***[/COLOR]**

    Right-click the partition and delete or reformat it with a Windows filesystem.

There you go...and happy windowing.
Tip: before you go exploring different OS's like linux....best to know what you are doing beforehand.

**And before you undergo my instructions...Please read and answer ian-weisser Post**
And happy Trails

hm.... you don't quite understand what I'm telling you.Some one did install SYSLinux on the Motherboard or BIOS space or ROM on the computer(I don't quite understand if that is even possible.Like I said I don't understand how computers work).The SYSLinux is not installed on HDD or USB stick.You don't understand that even if I pre-install windows the SYSLinux will still boot AFTER BIOS and before WINDOWS.You are missing the point.

---

### Post by randomfluker4000 on 2017-05-04
> **ian-weisser said:**
> You are booting a Linux system when that occurs. Syslinux is the bootloader for that Linux system.
If you wish to stop using Syslinux, then cease using bootable USB stick that you created.

Yeah but the same happens when I boot Windows 10 on HDD - this two
" 
_ 
_ 
"
show after the BIOS screen and before the WIndows LOGO . Even if I don't use the UBUNTU on the USB stick IT still SHOWS. IT feels like the SYSLinuxs is installed on the Motherboard - BIOS reserved part or ROM or I don't quite understand.

---

### Post by #&amp;thj^% on 2017-05-04
Oh but I do understand.;)
Not sure who's really missing the point here...but it's not me.:)
As we have tried and failed to explain here.... it is merely a boot loader.
Perhaps the tool you used to burn/install your ubuntu on the USB use's syslinux as default.
But we"ll never know because you don't answer the questions we ask you.
But I'm done here...and best of luck sorting it out.
Regards

---

### Post by ian-weisser on 2017-05-04
We gently suggest you consult your hardware manufacturer or vendor.
You paid them for support on your hardware, after all.

Syslinux is a wonderful bootloader, put together by some very nice people. It is most certainly not a virus.
We have no idea how you managed to install syslinux onto your hardware.
We don't understand either.
We have nothing to do with either the syslinux project, nor your hardware vendor.

---

### Post by randomfluker4000 on 2017-05-04
> **1fallen said:**
> Oh but I do understand.;)
Not sure who's really missing the point here...but it's not me.:)
As we have tried and failed to explain here.... it is merely a boot loader.
Perhaps the tool you used to burn/install your ubuntu on the USB use's syslinux as default.
But we"ll never know because you don't answer the questions we ask you.
But I'm done here...and best of luck sorting it out.
Regards

OK thanks for the Help.I wish I never got the SYSLinux "Virus" .... I would still be using Windows 7.... oh well ... once again it is proven that those who have knowledge rule over those who don't :D

---

### Post by #&amp;thj^% on 2017-05-04
Could you change the term Virus to something else _**not appropriate **_here.
You do have the instructions to remove syslinux from your system...if you choose.

---

### Post by randomfluker4000 on 2017-05-04
> **ian-weisser said:**
> We gently suggest you consult your hardware manufacturer or vendor.
You paid them for support on your hardware, after all.

Syslinux is a wonderful bootloader, put together by some very nice people. It is most certainly not a virus.
We have no idea how you managed to install syslinux onto your hardware.
We don't understand either.
We have nothing to do with either the syslinux project, nor your hardware vendor.

Anyways ... I guess I have to read a lot of books about computer Hardware and Software before I understand how computers work.Thanks for the help - Ubuntu is a great community .... you did try but my almost 0 knowledge of computers systems failed me.Thanks for the help once again !

Side note for this forum Moderators: Any moderator reading this can delete this Thread or put the status - Solved.

---

