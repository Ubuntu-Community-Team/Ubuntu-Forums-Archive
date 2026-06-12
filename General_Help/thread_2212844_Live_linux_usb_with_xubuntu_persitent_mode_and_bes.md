---
title: "Live linux usb with xubuntu: persitent mode and best installation?"
date: 2014-03-23
forum: General Help
---

### Post by jun5 on 2014-03-23
Hi everyone!

Around two weeks I discovered the magnificent fact that you can have a linux distribution in an USB with persistent mode. I used this program [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) to create my "xubuntu Usb" because my computer it's a little limitated and I only wanted linux for some programming matters, so I though xubuntu would be great taht it's lighter with a pretty nice looking interface. But I have some "problems".

First of all, I seached in internet for information about the annoying "Try/Install Window" and how to quit it but I only found how to do it in ubuntu modifying the syslinux.cfg file. Also, my Usb doesn't save some of my settings (my personal shortcuts for example) and I found that modifying syslinux.cfg this problem is solved too, so, in xubuntu, what can I do for solving these two "problems"?

Another thing that I would ask is if using the "linux Live Usb Creator" I get a nice installation or you recommend me another program or way to create this type of booting usb, because, as I doesn't really installed and configured it too much, I would change it if there is a better way to create it! :KS

Sorry for that large explanation, I'm really a noob on it! Hope someone answer my questions :)

---

### Post by efflandt on 2014-03-23
The live iso on USB is handy for taking Linux with you in your pocket to boot on most any PC. The persistent data can keep timezone and wireless security settings and other programs you install. And it does not take up much space on the USB device.

However, it is not intended to be a regular system. There is no security, the default user ubuntu can do most anything with no password, even if you add another user with password. It takes awhile detecting all hardware each time you boot. You cannot install video drivers or do most system updates (like the kernel) because initial boot is from a fixed squashfs file system before anything else mounts. So if you want an actual system with password and that can do updates it would be better to do an actual install to a USB memory stick, hard drive, or memory card reader for SD, etc. Although that should have at least 8 GB.

---

### Post by jun5 on 2014-03-23
I think I get what are you trying to say to me: having a complete installation in a USB stick intead of a live installation. But, for now, I'm nice with the live version one. What I really want is to save my shortcuts and to quit the automatic "Try/Install" window. 

If I can't really quit it with a live linux version, I would think about having a complete installation in a USB stick :)

---

### Post by superdaveozzborn on 2014-03-23
yes this is not secure method as stated by[**[COLOR=#000000] efflandt[/COLOR]**]("http://ubuntuforums.org/member.php?u=937632") however it is nice to have for convenience.

I did it using Xubuntu 12.04 and RemasterSYS to create a new iso. 

download Xubuntu.iso (live)
install to computer
make persional changes, desktop, links, shortcuts, what ever
install RemasterSYS
save user settings
create new ISO (backup)
plugin USB
open startup disk creator and tell it where the iso file is.
boot to usb and you have all your settings..

if you need help finding/installing remastersys try this  [http://www.distrogeeks.com/install-remastersys-ubuntu/](http://www.distrogeeks.com/install-remastersys-ubuntu/)

---

### Post by jun5 on 2014-03-23
But to use the RemasterSYS I need to have installed Xubuntu in my computer no? 

The reason why I have xubuntu in a pen-drive stick is because my computer came from the factory already with 4 partitions of disk so I could installed in my computer memory. So, if I need a computer with xubuntu, I can't create this new iso T.T 

It possible to do it with my actual Live Bootable usb?

---

### Post by superdaveozzborn on 2014-03-23
hmmmm i have to say that i dont really know, i see no reason why you cant. but i do not know for sure. just make sure you create a backup of your usb first to be safe.

note! i will test this out to be sure....

---

### Post by superdaveozzborn on 2014-03-23
yes it does seam to working fine from the live usb after installing remastersys on it. however how you will need a second usb to install the new iso file to....

hope this helps

---

### Post by superdaveozzborn on 2014-03-23
I stand corrected, after more in depth look into running remastersys straight off the live usb is not working. my apologies ... :(

---

### Post by jun5 on 2014-03-23
[SIZE=1][COLOR=#DD4814][COLOR=#000000][SIZE=2][superdaveozzborn]("http://ubuntuforums.org/member.php?u=1283721") no need of apologies! You take your time only in testing! Thank you very much :)

I've been investigating also in internet and I think I will install xubuntu in a complete way (not the live one) in my USB stick unless someone gives me any other solution. 
[/SIZE]
[/COLOR][/COLOR][/SIZE]

---

