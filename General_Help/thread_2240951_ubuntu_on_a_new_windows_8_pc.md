---
title: "ubuntu on a new windows 8 pc"
date: 2014-08-23
forum: General Help
---

### Post by peterinmalaga on 2014-08-23
Hi, I bought a new pc 2 months ago from the UK (HP Pavilion 15 notebook pc) with Windows 8.1 installed. You may well have guessed that I hate windows 8.1 like many others. I have an old pc with Ubuntu installed and that works fine, though it has a few minor faults (the key for the letter V is missing!) My question is: I have persevered with Windows 8 for 2 months and it is very slightly better now but it still irritates me and I can't help feeling that there's a shedload of stuff going on in the background that I do not need. Should I install the latest version of Ubuntu or buy a copy of Windows 7 on ebay?
I would really appreciate your opinion and advice.
Thanks.
Peter

---

### Post by cbraxton on 2014-08-23
> **peterinmalaga said:**
> ... Should I install the latest version of Ubuntu or buy a copy of Windows 7 on ebay?
I would really appreciate your opinion and advice.
Thanks.
Peter

Obviously here people are going to lean towards advising you to use Ubuntu. ;)

You should be aware though that some newer laptops are very unfriendly to Linux. I just went through this with an Acer 43BC. It had two problems that were deal breakers. Firstly, for dual-boot purposes the keyboard would not operate the bootloader menu; it would not work at all for anything but UEFI options until the OS loaded up. (This was the case with both Linux and Windows boot managers! And there were no UEFI options regarding legacy USB for keyboard operation.) Secondly, although Linux ran OK from a flash drive it crashed when installed on the hard drive. The inoperative keyboard made it impossible to switch to a virtual screen to see what might be going on. So I gave up on that and got an Asus X200MA instead, which is not quite as nice a machine overall but has no serious issues running Linux. (I'm dual-booting since I have occasional need to test things under Windows. Secure boot is disabled.)

The point for you is that you can't assume Linux will work, you need to research what issues your laptop may have if you're looking to move in that direction. One thing you might want to do is to use Clonezilla or the like to do a full image backup of your hard drive first so you can get back to where you were if there are serious problems.

---

### Post by peterinmalaga on 2014-08-23
Thanks for that. It's very helpful. I shall check out if other people here have any experience with my HP Pavilion PC.

---

### Post by oldfred on 2014-08-23
All you can do is try.
Windows 8.1 does make it even more difficult as it resets itself to default all the time. But there are some work arounds.
And HP makes it that any new entries must say Windows to boot. But you can change the drive default file bootx64.efi to really be grub and then boot hard drive in UEFI. They have not yet modified that to only be Windows (yet). 

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by fantab on 2014-08-23
Windows8 can be tweaked to look and feel like Win7 and underneath its as good as Win7. One of my friend uses '[classic shell]("http://classicshell.net/")', and it makes Win8 so much better for me. I wouldn't spend anything on a new copy of an 'old' OS.

Keep Win8 and also have fun with Ubuntu - dual boot.

---

### Post by Mark Phelps on 2014-08-23
Most people who hate Win8 really dislike the Tiles interface, not the underlying OS.  I've been using it since the preview, and one of the first things I did was install Start8 from Stardock -- and use the Desktop interface all the time. So, as fantab mentioned, you can easily make Win8 look and feel much like Win7 -- without having to buy and install Win7.

---

### Post by peterinmalaga on 2014-08-24
Thanks very much for your advice. I shall try the classic shell solution. I don't use a mouse as the table top for my PC is small. I find that the screens open and close and overlap one another almost randomly, even though I touch the touchpad with the very lightest touch. Hopefully the classic shell will not let that happen.

---

