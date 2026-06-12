---
title: "Installing Ubuntu without optical drive"
date: 2008-06-30
forum: General Help
---

### Post by J Christopher on 2008-06-30
I recently purchased a used server with the following specs:

[INDENT]2 x single core Xeon 1.8 GHz processors
4 GiB RAM (of which only 3.5 GiB are visible from the OS -- 32 bit CPU's? 32 bit OS? 512 MiB RAM dedicated for video? other?)
3Ware IDE RAID controller card (supports up to 12 drives)
9 x ~160 GB HDD's (configured in RAID 5)
1 Compact Flash port (I think -- I don't have a CF card to verify)
5 x gigabit ethernet ports (1 port on motherboard + 1 x 4 port NIC)
2 x USB ports (have not determined what version of USB)
PS/2 keyboard and mouse ports
1 x VGA video port
1 x port labeled "management" (looks like pin side of a VGA connector, although I haven't compared pin count)[/INDENT]

The machine does not have an optical or floppy drive, nor do I have external units to attach. I do have a Dell USB Bluetooth adapter, and my working machine has internal Bluetooth. I've not tried the adapter on any machine.

To the machine I have connected 1 VGA monitor, 1 USB keyboard, and 1 two button rollerball mouse with scroll wheel, all Dell brand.

The machine currently has Fedora (freshly) installed.

My intended uses for the machine are:

[INDENT]1) RAID NAS
2) Router
3) Gigabit ethernet switch[/INDENT]

The latter two uses will ideally be temporary, only until such time I can afford an 802.11n wireless router and an 802.3ad compatible gigabit switch. However, right now I only have one internet port, and my working machine has only one ethernet port, so I need to take advantage of the multiple ports on the server.

**Here's the problem:**

The seller, who installed Linux on the machine, did not offer the root password. I have also been unable to access the machine's BIOS by pressing and holding *delete* during the boot process. I've also tried multiple other key combinations instead of *delete*, although I don't remember exactly what they were, without success. The machine appears to be completely unresponsive to the keyboard during the first portion of the boot sequence.

Following the instructions of pressing alt-3 doesn't enter into 3ware configuration screen while that prompt appears on the screen, nor does pressing any key work to enter the (Fedora) menu when "press any key to enter the menu" appears on the screen.

The boot sequence appears to go properly, except I do see:

[INDENT]..MP BIOS bug: 8254 timer not connected to IO-APIC
ACPI: wrong _BBN value, reboot and use option 'pci=noacpi'[/INDENT]

I also get failures when determining each of the ethernet ports' IP address, but I am currently assuming that is due to them not being connected to anything.

There comes a point in the boot sequence when I see:

[INDENT]Red Hat nash version 6.0.19 starting[/INDENT]

At that point, if I'm holding the delete key key down, there is a repeat of "^[[3˜" until I release the key. That's the first indication I get of the keyboard being recognized and working.

Thus far, my initial impression of Fedora is not that great. I would like to replace it with some version of Ubuntu, although I'm not sure which one (Kubuntu? Xubuntu? Server? Desktop? 64 bit? 32 bit?). 

[COLOR="Red"]**Can I install Ubuntu (whichever version I use) on the server without an optical drive or floppy drive?**[/COLOR] I can't afford to add any peripherals right now. I have at my disposal a 4 GiB iPod Nano (2nd generation) that I can use as a flash drive.

I have extremely limited experience with Linux, and only a little bit more experience with the UNIX command line. My working machine is a MacBook running 10.5.3, if that offers any insight.

Any help is greatly appreciated. :)

---

### Post by WRDN on 2008-06-30
[http://help.ubuntu.com/community/Installation/Netboot](http://help.ubuntu.com/community/Installation/Netboot)

Using this guide, you may be able to download and install Ubuntu Desktop/ Server Edition using only the internet connection.

Its also possible to install it using Wubi without needing a LiveCD.

EDIT: Which version are you wanting to install? I guessed that, as you bought a server, you would want to install the server edition.

---

### Post by J Christopher on 2008-07-01
> **WRDN said:**
> [http://help.ubuntu.com/community/Installation/Netboot](http://help.ubuntu.com/community/Installation/Netboot)

Using this guide, you may be able to download and install Ubuntu Desktop/ Server Edition using only the internet connection.

Its also possible to install it using Wubi without needing a LiveCD.

EDIT: Which version are you wanting to install? I guessed that, as you bought a server, you would want to install the server edition.

Thanks. :)

I was looking through that method, and some similar methods. They all seem to require a root password and/or access to the BIOS.

I am assuming that the *sudo* command prefix requires an admin/root password in Linux as it does in the shells available in OS X.

---

### Post by soccerboy on 2008-07-01
try using a ps/2 keyboard.  Some machines don't use usb controllers on boot until the os loads.  So using a ps/2 keyboard might let you into the bios.

---

### Post by J Christopher on 2008-07-01
> **soccerboy said:**
> try using a ps/2 keyboard.  Some machines don't use usb controllers on boot until the os loads.  So using a ps/2 keyboard might let you into the bios.

Thanks. :)

I was wanting to avoid more hardware, but it looks like I won't be able to. Hopefully the used computer store down the street will sell one inexpensively.

---

### Post by adewale on 2008-07-01
I just hope this isn't late, but take a look at this [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by soccerboy on 2008-07-01
you don't have a ps/2 keyboard laying around that you could check it on?  I am not positive if that is indeed your problem, that is why I am saying that.

---

### Post by J Christopher on 2008-07-01
> **adewale said:**
> I just hope this isn't late, but take a look at this [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Not too late, thanks. :) I will look into it as soon as I get a little bit more free time tonight.

---

### Post by cariboo on 2008-07-01
Why not reset the bios, there should be a jumper on the MB very close to the battery, or pull the battery for a couple of hours. You can use john aka John The Ripper to carak the admin password. Howto here:

[http://osix.net/modules/article/?id=455](http://osix.net/modules/article/?id=455)

Remember Linux is not Windows, not everything has to be done the windows way.

Jim

---

### Post by J Christopher on 2008-07-01
> **soccerboy said:**
> you don't have a ps/2 keyboard laying around that you could check it on?  I am not positive if that is indeed your problem, that is why I am saying that.

No. I've been using laptops exclusively for a few years now until I bought this server (which was cheaper than a 1 TB NAS and router, which I was in serious need of), so I don't have any desktop parts laying around. I was given the monitor, and borrowed the keyboard and mouse. To say I am on a budget is a *extreme* understatement, which is why I'm trying to avoid more hardware.

Once I get everything up and going as I want it, I plan to set up VNC to control it from my laptop.

---

### Post by J Christopher on 2008-07-01
> **cariboo907 said:**
> Why not reset the bios, there should be a jumper on the MB very close to the battery, or pull the battery for a couple of hours. You can use john aka John The Ripper to crack the admin password.

Thanks for that tip. It's another possibility I can investigate. :)

> **cariboo907 said:**
> Remember Linux is not Windows, not everything has to be done the windows way.

That it isn't Windows is the best thing about Linux, IMHO. :-D I gave up on Windows 3-4 years ago because I didn't like the Windows way. I've been happily using Macs since then, and will continue doing so. (I'm not trying to imply that OS X is better than Linux, just that it suits my own needs for my primary machine.)

I don't expect Linux to be just like OS X, either, and for my present needs, Linux is a much more practical solution. It offers the security I'm looking for at a price I can afford. I do expect to have to overcome a learning curve. I am actually looking forward to exploring a new operating system, despite he anticipated growing pains.

---

### Post by J Christopher on 2008-07-07
> **soccerboy said:**
> try using a ps/2 keyboard.  Some machines don't use usb controllers on boot until the os loads.  So using a ps/2 keyboard might let you into the bios.

A PS/2 keyboard did indeed help. I also figured out the root password.

> **adewale said:**
> I just hope this isn't late, but take a look at this [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Thanks for the link. I did end up having to buy a PS/2 keyboard in order to select the net install from the menu during boot-up, but it seems to be working well. I'm doing an install right now, although I did end up opting for CentOS. :redface: (The install seems to be hanging about halfway through the filesystem format, but hopefully it's my imagination, since it has 1.25 TiB to format.)

Thanks for the suggestions. :)

---

