---
title: "Can I run Ubuntu from an external device"
date: 2015-05-25
forum: General Help
---

### Post by Jonatan Formentera on 2015-05-25
Hi, I bought a few weeks ago an HP computer with Windows 8.1. I'm been told It's not very advisable to install  Ubuntu in it. I'd like to know if I can run Ubuntu from an external devise: maybe a DVD disk or an external hard driver by USB
Thanks

---

### Post by monkeybrain20122 on 2015-05-25
Probably not if you have secure boot on.

---

### Post by Jonatan Formentera on 2015-05-25
Yes, I have a security boot on. Does somebody know if there is a possibility? It's very unpleasant for my to work with Windows

---

### Post by monkeybrain20122 on 2015-05-25
I don't know if you can turn secure boot off if Windows is installed, or maybe you have to manually turn it off and on? Sorry, can't help, my experience with Windows ended basically with XP. :)

---

### Post by cmcanulty on 2015-05-25
i believe the bios will let you turn secure boot off

---

### Post by monkeybrain20122 on 2015-05-25
> **cmcanulty said:**
> i believe the bios will let you turn secure boot off

Yes but wouldn't he be able to boot Windows then?

---

### Post by pfeiffep on 2015-05-25
We have an expert moderator on the forum, oldfred, who has written numerous posts. I respectfully suggest bypassing afore mentioned comments and start form [here]("http://ubuntuforums.org/showthread.php?t=2147295")

additional [link]("https://help.ubuntu.com/community/UEFI")

---

### Post by Griffin_ on 2015-05-25
If you want to run just a "Live CD" version of Ubuntu, then all you need is a DVD/USB and a ISO image (Which you can get from Ubuntu.com) But if you want full Ubuntu externaly, I would recommend using a Live CD to install ubuntu to a external hard drive. You can easily manage partitions and filesystems in Ubuntu's built in installer.

---

### Post by Vladlenin5000 on 2015-05-25
Only a few HP models come with a non-standard UEFI implementation, "tweaked" to boot Windows only, but even for those there are workarounds.With that in mind you can install Ubuntu in any HP.
Whether the drive is internal or external doesn't matter. The differences - if any - is speed and an eventually more complex setup but it requires the same workarounds in those non-standard few models.

---

### Post by Jonatan Formentera on 2015-05-26
I tried to install Ubuntu by the classical method using a pendrive from an usb port, but the BIOS didn't allow it. I been told I have to do a virtual box, but it's a little risky for a computer I bought recently. If I manipulate the machine, I will lose the guarantee of the provider in case I had any problem with the computer.

---

### Post by Jonatan Formentera on 2015-05-26
Perhaps the most interesting way is Griffin's method, but I don't know how to do so. I just know the method of booting the computer from the BIOS to an external device and it install it in the hard driver of the computer

---

### Post by Francesco_Verlato on 2015-05-26
I don't think that virtual box void your warranty..

---

### Post by cmcanulty on 2015-05-26
No virtual box just runs as a program it doesn't do anything to your windows setup. I run win 7 in virtual box, quite easy to set up a ubuntu virtual box. You just need a bootable usb flash drive or a dvd burn the image boot up to windows and install virtual box and then your buntu of choice inside the virtual box

---

### Post by Vladlenin5000 on 2015-05-26
> **Jonatan Formentera said:**
> I tried to install Ubuntu by the classical method using a pendrive from an usb port, but the BIOS didn't allow it. I been told I have to do a virtual box, but it's a little risky for a computer I bought recently. If I manipulate the machine, I will lose the guarantee of the provider in case I had any problem with the computer.

Actually it's the other way around.
As already commented, a virtual machine is just software that you can install like any other then use it to create, manage and run one or more virtual machines. As such, it has nothing to do with warranty.
A dual-boot also has no implications. You keep the original OS that can be used by the official tech support for troubleshooting when needed.
A different scenario is when the original OS is replaced by something else entirely different (ex: Linux). Downgrading or upgrading a Windows version is often allowed and the service will be provided without further requirements. If you install Linux in a PC with factory installed Windows, then - at most - the tech service can and will ask you to reinstall the original OS to perform the troubleshooting. Even so it doesn't limit your warranty in any way.

So, one more piece of misinformation you got there...

Why it didn't boot properly from the USB can have many causes. Unless you're willing to give us some additional information, at least the model name or number, and unless you really decide what do you want to do, I don't see how can we help you beyond what we already did, i.e., correcting the misinformation.

---

### Post by Jonatan Formentera on 2015-05-26
Thank you for your information
the charateristics of my computer are:

Notebook Model: HP 255 G3 Notebook pc
System Board ID : 21 F7
Product configuration ID: 096B100000405F00051660181
System Board CT number: PEHERF21W7SCNX
BIOS Version F.23
Processor Type: AMD E1-2100 APU with Raedon(TM) HD Graphics
Processor speed: 1000 Hz

---

### Post by Vladlenin5000 on 2015-05-26
HP 255 G3 is the easiest to install Ubuntu, single OS or dual-boot.
You've been really misinformed about all this. Your notebook is actually Ubuntu CERTIFIED and the same model is sold (not worldwide) with factory installed Ubuntu.
I've installed dozens of those.
The only thing recommended to do after installation is to go to System Settings > Software & Update and, at the rightmost tab "additional drivers", select the recommended *fglrx* (AMD proprietary drivers, a must for all AMD APU based computers).

In a nutshell, if you want Ubuntu only, just go ahead and install. I personally guarantee you everything will work. However, it's advisable to create the set of Windows recovery DVDs before removing it. You may want to resell it later and your customer might want the original OS. And that Windows is yours, you already payed for it (OEM license with Bing - no, you can't use it anywhere else, it's tied to that PC), so why not keep, just in case? You may also need it for tech support oriented troubleshooting. Again, they can and will ask you to do that, for obvious reasons.


Now, please tell me/us what do you really want to do, so I can help you.

---

### Post by Jonatan Formentera on 2015-05-26
I just would like to install ubuntu because I feel uneasy with Windows, but as I said before, I tried it with a live usb and I wasn't allowed to
Thanks

---

### Post by Vladlenin5000 on 2015-05-26
First of all you need to make sure your USB has been correctly done. Then, you need to turn off secure boot in UEFI.
Whenever you need to access UEFI settings you should pres ESC during the initial splash screen. There, also, you should change the boot order to allow boot from USB first (always the entry preceded by UEFI: ...). Optionally, after pressing ESC you can choose F9 for the one time boot menu where you can select the USB (again, the UEFI entry only).
Done!

---

### Post by Jonatan Formentera on 2015-05-27
Hi Vladlenin, I followed your steps but it didn't work. I went to the configuration system in the BIOS and disable the security boot. Then I turned the computer off and switched it on again to access the BIOS (F9). I couldn't install it. When I tried it through UEIF, there appeared just the files in the Pen, but I couldn't install it. After restarting the computer, the security boot had been enable by itself. I tried it otherwise. I went to F10 (Configuration system) disable the security boot, went down to *boot order* and selected *usb drive* in order to boot the system from it. After that, a screen appeared saying to me I had to introduce a code to change the system. I pressed the keys but no code appeared. 
I don't know what to do.
Thanks

---

### Post by Vladlenin5000 on 2015-05-27
How did you produced the USB Flash drive you're trying to boot with?

---

### Post by Jonatan Formentera on 2015-05-27
I passed an ubuntu iso image 64 bytes through a windows installer and located it in a pen drive

---

### Post by Vladlenin5000 on 2015-05-27
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

^^^^
Like this? There are a few other tools and if I were to choose I would vote for [Rufus]("https://rufus.akeo.ie/") which gave us excellent results for many different distros, although we usually do it in Ubuntu or OpenSuSe with Linux tools.
Using Rufus and for newer machines like yours GTP+UEFI is the best option.

The one mentioned in the Ubuntu official document above or Unetbootin should be fine.

ESC, then F9 should show you the boot menu where it must have two entries for the USB drive. Most pens work but there are some that don't work as bootable devices even when the tool says it's OK, i.e., finishes without errors.

---

### Post by Jonatan Formentera on 2015-05-29
Hi, Vladlenin. I tried it again using Rufus but the result was the same. I think the problem is windows protection. I will make it with my all-life system. I will put another hard driver in the machine and install it
Thank you anyway
By the way, do you know how I can access the hard driver in this machine. I think I will have to remove the keyboard

---

### Post by C.S.Cameron on 2015-05-29
The official help page for installing to a uefi device is here:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
The first step I would recommend is to try to boot another computer with your external device.
A faulty install to USB device is often the problem.

---

