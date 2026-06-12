---
title: "VMWare-player"
date: 2007-03-11
forum: General Help
---

### Post by will2301 on 2007-03-11
I am having difficulty in installing Windows XP Home in VMWare-player. I usually use Ubuntu as my standard operating system, but as I need Windows for certain operations(such as homebanking, danish-net-news, and the like) it would be nice to have both systems operating at the same time. This is why I have downloaded VMWare-player.
But my problem is that I haven't the "original" Windows CD - I have only Acer recover CD, that I burned the first time that I booted my new computer. I burnt four CDs.
When I try to install from the Acer recover CD it says "only for Acer computers"(?!?). 
In the bios I can read that the manufacturer is VMWare. So my question is: Is it possible to change my bios to look like an Acer machine? 
Maybe you have suggestions that might be helpful.

Thank you in advance
Jean Gauthier

---

### Post by dexter on 2007-03-11
Seems doubtfull. Those recovery cd's usually only work on the computer it's delivered with. They check the BIOS, but also the hardware configuration. If it turns out that configuration is changed to much, the recovery cd won't work. The VMWare Player doesn't look at all like your laptop, so i don't think this will work.

By the way, if you want to work legal, you should buy a new license for you virtual machine (yeah, stupid...).

---

### Post by will2301 on 2007-03-11
> **dexter said:**
> Seems doubtfull. Those recovery cd's usually only work on the computer it's delivered with. They check the BIOS, but also the hardware configuration. If it turns out that configuration is changed to much, the recovery cd won't work. The VMWare Player doesn't look at all like your laptop, so i don't think this will work.

By the way, if you want to work legal, you should buy a new license for you virtual machine (yeah, stupid...).

Thanks for the reply. I have followed this guide: [http://www.ubuntuforums.org/showthread.php?t=84275](http://www.ubuntuforums.org/showthread.php?t=84275) but instead of creating an iso image of the Windows CD (I also have a 'real' Windows XP cd I use on one of my other computer) I'd create an iso-image of my Windows partition (Using the function "mkisofs"). But when i boot it, it says: "No operating system found".

---

### Post by jimbob on 2007-03-11
If you have a real W$ cd from another computer use that to install in Vmware.

Since you paid for two different copies of XP that should be legal.  Just enter the product authorization code from the acer computer system.  Worth a try.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by calimarno on 2007-03-14
Hello will2310,

You can use the VMWare Converter software to convert your Windows system in a virtual machine file that will run under VMWare-Player.

[http://www.howtoforge.org/vmware_converter_windows_linux](http://www.howtoforge.org/vmware_converter_windows_linux)

Note that your Windows system should be minimal otherwise it will be very slow in the VMWare-Player.

---

### Post by jimbob on 2007-03-14
Which would be better to do on a new install of XP - install it in the standard manner and then make a virtual machine from it using the above link to run under Ubuntu or install it as a VM from scratch on the Ubuntu machine?

How about activation.  If I activate it as a VM will it show any of the hardware devices? Will I have trouble activatiog it later as a normal install on the same machine?
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by calimarno on 2007-03-16
Both are possible... I don't think that one is better, you'll get exactly the same vitrual machine at the end.
For the activation, I don't know... I had to activate the virtual machine and since I didn't reboot my "physical" windows, so I can't help you on this point.

---

### Post by ahmatti on 2007-03-16
Have you given Virtualbox [http://www.virtualbox.org/](http://www.virtualbox.org/)  a try? I find much faster than VMware. You'll need to get install cd or ISO though. I would also probably go with the fresh install, because the hardware in the virtual machine is different from your physical box... Fresh copy of windows is also always faster than one that you have used for a while.

I am currently running WindowsXP under Virtualbox for MSoffice and Acrobat Pro and Photoshop CS.

---

