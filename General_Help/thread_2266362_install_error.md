---
title: "install error"
date: 2015-02-22
forum: General Help
---

### Post by chip5 on 2015-02-22
I get error   d:\document~1\chip\locals~1\temp\wubi-14.04-rev286.log

when I search for this, I am not allowed permission. 

I am using XP pro, I am trying to install Unbuntu into the first volume (nor the MBR volume). I have XP as the boot drive on D: and windows 8 on C: Ubuntu on G: Drive C: is unbootable. I am tryig to install Ubuntu from a disc. I gets right to the end and I get this error message. prompt does not recognize this command.

Sorry, I am trying to install from a USB stick

---

### Post by Impavidus on 2015-02-22
If you want to install Ubuntu from the live disk, you won't need wubi. In fact, it's no longer supported (although it may still work on non-UEFI systems). Linux doesn't use drive letters, those are a Windows thing. Windows doesn't recognise Linux partitions, so it won't assign them a drive letter. Ergo, a Linux partition never has a drive letter. Also, drive letters don't say anything about on which drive any particular partition is, making them useless.

It could help if you post a screenshot of your current partitioning layout and clearly explain what is what and where you want to install Ubuntu.

That error message gives you the location of a log file with more details, but with wubi being the wrong way anyway it won't really matter.

---

### Post by the-tech-kid on 2015-02-22
Use a USB/CD rarther than Wubi (i use it but only because I have no other means of installation)

---

### Post by the-tech-kid on 2015-02-22
Use a USB/CD instead of Wubi (i use it but only because I have no other means of installation).
And remove the dupe [ubuntu] in the title please.

---

### Post by chip5 on 2015-02-22
I will get a sceen shot but meantime, I could not get Ubuntu to load from my USB drive. I used testdisk-6.14 to (I thought) make my USB drive download. No luck, which is why I tried Wubi. I have no installation application in my Ubuntu download. Thanks for the input.

---

### Post by Bucky Ball on 2015-02-22
Try [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") to create the bootable USB with the ISO. As mentioned, forget Wubi. Not supported and if you have troubles you won't find a lot of help here because (almost) no-one uses it anymore. 

Good luck.

---

### Post by chip5 on 2015-02-22
What I hope to eventually accomplish is a multi-boot system; if I just end up with two OS's, I'll be happy. I have XP pro on D and Windows 8.1 on C. From what I understand from reading is that there is a program in Ubuntu that can modify the MBR so that I can actually choose an OS when I boot. I hate 8.1, I've been using XP since it was offered. I use multiple CAD programs and I just do not feel as though 8.1 will handle them well, but since support for XP has terminated, 8.1 will work for operations such as downloading books via Itunes for my ipods, updating my GPS, etc.
I hear that Linux systems are superior but I am too old to want to learn new tricks, so I prefer sticking with what I know. Thanks for the feedback. I will want to move more disk space eventually to D:, I am sure I will need it once I load my CAD programs. I will probably leave only WORD and maybe OUTLOOK and load everything else to C:.

---

### Post by chip5 on 2015-02-22
I hope I did this right...

---

### Post by Impavidus on 2015-02-22
Well, I can't correctly open your .doc. The trick with screenshots is attaching them as a .png file. High quality jpeg also works, but png is clearer.

And if everything works correctly the installer will modify the MBR to install the GRand Unified Bootloader (grub), which will give you a menu where you can choose your operating system.

---

### Post by chip5 on 2015-02-22
Thanks, I'll try and figure out how to paste something. I am really not (obviously) good with computers. After downloading and trying various applications, I am now able to boot from my USB drive. I will next install Ubuntu on the hard drive in the volume I carved out for it, the first physical volume after the little ?boot drive? volume. I assume that will install the GRUB instrument for multiple boot choices.
Thanks again to all of you that have responded.

---

### Post by Bucky Ball on 2015-02-22
Leave free, unallocated space for Ubuntu. You can not create a partition for it with Windows. Ubuntu uses EXT* and Windows can't create that.

---

### Post by chip5 on 2015-02-23
So I now have a bootable USB drive and have installed Ubuntu successfully, I think. Now my issue is that while I have the option of booting 8.1, I still get the same error message as before 'missing ...kernel...'. I can still boot XP and of course Ubuntu. How do I arrange to boot 8.1 as well?
In the first choice  screen, (Ubuntu), I am given the option of loading 8.1 but not XP. In the next choice screen, if I choose 8.1 (in BIOS) I am given the choice between 8.1 and XP. I know you folks are not Windows people but I was under the impression that Ubuntu (GRUB?) did something called a chain boot which applied to all OSs. Guess I got that wrong.... IN the boot menu in start up, I am only given the option of the entire hard drive, not the individual volumes as I had hoped.Thank you for your help.

---

### Post by grahammechanical on 2015-02-23
I cannot comment on the options you get in the BIOS setting utility. In Ubuntu we can run

```
sudo update-grub
```

Watch the screen printout. Does it list both Windows 8.1 and Windows XP boot loaders? If we install Ubuntu after installing a Windows OS then there is a good chance that we will get an option to load Windows in the Grub boot menu. But if Windows 8.1 was installed after Ubuntu then the Ubuntu boot loader does not know of the existence of Windows 8.1. The command that I have given you will tell Grub to probe the disk looking for operating systems.

Regards.

---

### Post by Mark Phelps on 2015-02-23
I'm presuming you installed Win8.1 after you had XP already on the system, and if that is the case, Win8.1 installed its boot loader files into the XP partition that was already there.  SO, when you launch the Windows boot loader, you get an OS selection screen that includes both Win8.1 and XP.

When GRUB found the Windows versions, it created ONE menu entry for the XP partition. Since it saw the Win8 loader, that's what it named it.  When you select that entry, it hands over control to the Windows boot loader (in this case, Win8.1), which then puts up the OS selection screen.

That's how it works when you have more than one Windows OS on the same computer -- unless, when you install a newer OS version, you disconnect ALL the drives containing the older OS version(s).

If Win8.1 is not launching when you select it from the second screen, that is a Windows problem you can't fix from Ubuntu.  Suggest you post that problem to a Windows 8 forum to get detailed help.  Suggest [http://www.eightforums.com](http://www.eightforums.com)

---

