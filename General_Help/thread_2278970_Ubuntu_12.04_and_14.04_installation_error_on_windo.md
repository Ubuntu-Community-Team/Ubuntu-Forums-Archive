---
title: "Ubuntu 12.04 and 14.04 installation error on windows 8.1.?"
date: 2015-05-20
forum: General Help
---

### Post by Akash_Pathak on 2015-05-20
I am having Windows 8.1 pre-installed 

I have tried every possible way....

So here is what all i did
1.created bootable pendrive and booted normal way didnt worked
2.Disabled secure boot,fast boot,quiet boot form BIOS didnt helped
3.trying to install ubuntu 14.04 mounted it from iso and started wubi it installed boot screen got option like ubuntu and windows but when i click ubuntu it give me a error i have attached a file what i get error for
4.Went to windows 8.1 and clicked change PC settings and went to recovery and tried booting from there like UEFI-CD/DVD, UEFI-Removable Disk, UEFI-PMAP
5.Ubuntu is working fine on my other windows XP PC just changing boot order from 1st to USB-HDD and 2nd Hard disk
6.I have tried boot order in BIOS on my windows 8.1 laptop 1.USB PMAP and 2nd Windows boot manager

I was trying to install directly clicking wubi it gives me options like where to install then it gives error to check logs......

Need Help

---

### Post by westie457 on 2015-05-20
Hello and welcome to UF.
FYI Wubi installation will not work with Windows 8 or newer. Your options are either a dual-boot system or run Ubuntu as a virtual machine inside Windows.

This link provides a run-through on dual-booting [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

When you need more specific help with this post back here.

---

### Post by Akash_Pathak on 2015-05-20
Alright the link you have provided, i have already went throught that and i think u have read that what all steps i have tried and that link covers all of those and i know i can run ubuntu on a virtualbox but i think you know that running a full OS and running through a virtualbox has its own limitations is there other linux OS that i can install directly on my hard drive throught windows 8.1 without making a bootable USB pendrive or CD ?

---

### Post by sudodus on 2015-05-20
You can install a very light linux operating system in VirtualBox. It will probably run quite well. If you computer is powerful enough standard Ubuntu will also run well in Virtualbox. There are also other systems for virtual machines, for example KVM + virt-manager.

There is also the option to boot from an iso file via grub, but it is easier to flash the iso file to a USB pendrive and boot from the pendrive. It makes things easier, when you boot from one drive and install to another drive (drive = physical device: disk, flash-drive ...).

Wubi was designed to make it easy to test Ubuntu. A wubi installed system was never intended to be used as a permanent system. It has limitations compared to a regular installed system (dual boot with Windows).

See this link and links from it

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Akash_Pathak on 2015-05-20
So i think i have only 1 option left and that's using Ubuntu in a virtualbox because as i posted i have tried all the steps tried each and everything to make my laptop dual boot Ubuntu and Windows 8.1 but i don't think any of the suggestion's is working else i need to try a different linux OS

---

### Post by Vladlenin5000 on 2015-05-20
Make and model of the notebook?
Some have non-standard UEFI, designed to boot Windows only and as such require tweaks.

---

### Post by Akash_Pathak on 2015-05-20
Micromax LT666
Here is the Link for Product Description:-
[http://www.amazon.in/Micromax-Canvas-Laptab-LT666-Touchscreen/dp/B00WJPUDCE](http://www.amazon.in/Micromax-Canvas-Laptab-LT666-Touchscreen/dp/B00WJPUDCE)
Thanks for Helping

---

### Post by Vladlenin5000 on 2015-05-20
So it's an (in)famous 'Bay Trail' based notebook... You couldn't have picked worse hardware. It's possible to install Ubuntu but it requires a very advanced user. Just do a quick Google search and you'll know what I'm talking about.

---

### Post by Akash_Pathak on 2015-05-20
So can you give me a link for that i see you are a Ubuntu addict and i am a advanced user so please provide me a link or steps to do that are you saying there is a different way of dual booting on a Bay Trail notebook ?

---

### Post by Vladlenin5000 on 2015-05-20
I'm sure you found a lot of information already if you followed my suggestion in post #8. You can search this forum as well. Likewise I'm sure you're already aware that the main issue, apart WiFi, sound and other small details, is a 64-bit CPU with a 32-bit UEFI for which Grub has to be compiled. That's the advanced part, not that the other post-install issues are less advanced but booting in itself is a challenge.

---

### Post by monkeybrain20122 on 2015-05-20
Need at least 4G ram to run VB smoothly. You can do with less, but it won't be very smooth.

---

### Post by Akash_Pathak on 2015-05-22
Am i half way through of dual booting i can see 2 OS choice like i tried with Ubnuntu and Linux Mint but when i select either of them i get this error like a black screen with these message File: \ubuntu\winboot\wubildr.mbr  Status: 0xc000000f error can anyone help

---

### Post by sudodus on 2015-05-22
Wubi is old, and no longer developed and supported. It does not work with Windows 8 and newer versions of Windows. You are trying wubi in vain.

---

### Post by Akash_Pathak on 2015-05-22
So i have no options left i guess ?

---

### Post by sudodus on 2015-05-22
VirtualBox is an option if you have or get enough RAM. 2 GB would be an absolute minimum, but as said by *monkeybrain*, you need at least 4 GB RAM to run smoothly in VirtualBox.

---

### Post by Akash_Pathak on 2015-05-22
I Think Virtualbox is the last and only option for me.....:(

---

### Post by sudodus on 2015-05-22
Well, at least you should try it. You might be surprised how well it works.

How much RAM is there in the computer?

---

### Post by Akash_Pathak on 2015-05-22
2GB i tried giving Ubuntu 1 GB of Ram for 32 bit it was working fine can you tell me how to install guest extension in Ubuntu ?

---

### Post by sudodus on 2015-05-22
You can find help via the internet, for example this link

[https://askubuntu.com/questions/22743/how-do-i-install-guest-additions-in-a-virtualbox-vm](https://askubuntu.com/questions/22743/how-do-i-install-guest-additions-in-a-virtualbox-vm)

---

