---
title: "Ubuntu SOULPAD anyone ?"
date: 2006-07-07
forum: General Help
---

### Post by edoardo on 2006-07-07
Has anyone created a 'soulpad' using ubuntu ?
The soulpad is an ultra-cool IBM research project 
[http://www.research.ibm.com/WearableComputing/SoulPad/soulpad.html](http://www.research.ibm.com/WearableComputing/SoulPad/soulpad.html)

this way you could carry your own secure customized desktop anywhere and just borrow s.o.else's hw to run it!

that I would want to create on my external usb drive
now I have found this pointer and one day with enough time I may attempt it
[http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm](http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm)

PS - disclaimer: I work for IBM but this is purely personal stuff :-)

---

### Post by edoardo on 2006-07-14
OK, I made it!
followed pretty much the excellent instructions at:
[http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm](http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm)

except that:
no need for custom kernel, 606 LTS just works
though you need to install squashfs-tools

also the $WORK/ubuntu-livecd/bin 
directory can be deleted to save space (windows stuff!) 

EMPTY FILE MUST BE LARGER!
sudo dd if=/dev/zero of=$WORK/ubuntu-fs.ext2 bs=1M count=3500

in "chroot mode" my customization to the livecd was:
apt-get update
apt-get install build-essential
apt-get install linux-headers-2.6.15-23-386
apt-get clean

cd /root/vmware-player-distrib/
./vmware-install.pl
when asked for header sources:
/usr/src/linux-headers-2.6.15-23-386/include


the step from livecd to "liveusb" is trivial if the usb drive
has grub installed, as it just means copying the content of the livcd (except syslinux and windows stuff) and then a grub config that works can be found at 

[http://www.ubuntuforums.org/showthread.php?t=71567&page=16](http://www.ubuntuforums.org/showthread.php?t=71567&page=16)
e.g.

title		Ubuntu LiveUSB Splash
root		(hd0,0)
kernel /casper/vmlinuz boot=casper ramdisk_size=1048576 root=/dev/ram rw quiet splash --
initrd		/casper/initrd.gz
boot

---

### Post by Lunar_Lamp on 2006-07-14
This looks interesting enough that you may want to lay this out in a more detailed and clear way.

For example - what exactly is it?  Is it just booting a USB hard disk with ubuntu on?  If so that's great, if not - what is it and how does it differ?

---

### Post by edoardo on 2006-07-14
> **Lunar_Lamp said:**
> This looks interesting enough that you may want to lay this out in a more detailed and clear way.

For example - what exactly is it?  Is it just booting a USB hard disk with ubuntu on?  If so that's great, if not - what is it and how does it differ?

booting a ubuntu in live mode from usb
(ie detecting the hw, not as booting from ubuntu installed on a partition on a usb drive) 
and being able to run vmware player from the live system 

so wherever I am, as long as I can boot my customized live ubuntu (from usb or from cd) on some hardware found on the spot, I have my personal ubuntu system there (running inside a VM).

---

### Post by Lunar_Lamp on 2006-07-14
Ah right I get you.  I just use a laptop which I take everywhere with me, so I guess it's not so useful for me - still, I'd recommend you lay out a nice guide for people as this looks like the kind of thing people would find REALLY useful.

---

### Post by edoardo on 2007-03-08
Oh the link was not working ... this should:
[http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm](http://www.atworkonline.it/~bibe/ubuntu/custom-livecd.htm)

---

