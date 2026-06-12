---
title: "grub2 packaged fails to install"
date: 2018-06-13
forum: General Help
---

### Post by sevenfoxes on 2018-06-13
This is my first post here so apologies if I've got it in the wrong place. I'm not a complete noob either which is why this problem has been so frustrating.

Last night, my computer flashed that there was a new release to upgrade to. I didn't expect any trouble as I had already upgraded to 18 so I figured a 18.0x bump wasn't going to be a problem and clicked "upgrade". About half an hour through the update I stated getting "install failed" notifications for lots of different things including nvidia drivers and libcrypt. I saw libcrypt and I knew something had just gone really REALLY sideways with this upgrade. I got to the end and got a message to the effect of "your system may not be stable" - Well, having exactly no idea how to fix that I... rebooted. That's when things got worse. I couldn't login because libcrypt couldn't load, not even to recovery mode. So, I figured "eh, I've got all my data on external disks anyways. I'll just reinstall". I got a fresh copy of 18.04, booted from the usb and into the installer just fine. clicked erase and install with the right disk (eventually, I sorta knocked out my seperate disk with windows, first, like an idiot and POSSIBLY my data hard drive, but I don't know) and it started going.

Okay, so that brings me to the actual issue. It starts installing fine, but I get to Grub2 and it gives me the most vexing error ever:

```
The `grub-efi-amd64-signed' package failed to install into /target/. Without GRUB boot loader, the installed system will not boot. <OK BTN>
```

pressing <ok> crashes the installer. which then lets me submit a bug report. Then I'll be in the live environment. If I click again to install, it says that "pacman couldn't load" or something to that effect. I've... tried basically everything I could find on google. NO differences. same error every time.


My Drive layout:

250GB NVMe with windows bootloader
250GB SSD (where Linux was)
2 3TB HDD, one for windows, one for linux. (note: this was NOT mounted as home, it's just a plain ext4 disk)
No raids or anything weird going on. 

Computer Specs:
Easiest to just post this lol: [https://pcpartpicker.com/b/ZfxG3C](https://pcpartpicker.com/b/ZfxG3C)

EFI setup:
Windows is installed as EFI, just checked in panther. Indeed, EFI. (interesting it doesn't say uefi...)
```
IBS    Callback_BootEnvironmentDetect: Detected boot environment: EFI
```


What I've tried:

Manually setting up partitions. (the internet seems to like this answer)
unplug the ethernet (seriously, this is an answer someone had)
check the "download updates" box
don't check the "download updates" box
reformat the disk to unallocated space and install again
remove the NVMe drive entirely (I noticed there's a grub on this disk after the above mistake of overwriting windows. I don't know how to get rid of it)
manually setting up partitions with the NVMe removed

I know you probably will want more info, just let me know and I'll do my best, you know... not being able to boot. This was a machine thats been running fine for about 6 months. I also have a server running on 18 that got upgraded a few days back that has no issues. (and really has been running without issue for like a decade)

You guys are my only hope here. Help!

---

### Post by oldfred on 2018-06-17
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Grub UEFI install default is sda or first drive. Those with NVMe or MMC drives seem to work when they are first drive. But if efi partition changes or is not same drive as Ubuntu, it sometimes has issues. Boot-Repair may work by setting correct locations, but best to see configuration first.

The only thing is Boot-Repair uses bootinfoscript for first part of report, and I filed bug, but he needs someone to test finding NVMe drives.
       
 Support NVMe and MMC devices 
[https://github.com/arvidjaar/bootinfoscript/issues](https://github.com/arvidjaar/bootinfoscript/issues)

---

