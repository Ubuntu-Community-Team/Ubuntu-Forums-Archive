---
title: "[SOLVED] flashdrive install hardy. grub booting when its not supposed to."
date: 2008-05-21
forum: General Help
---

### Post by werries on 2008-05-21
So before, i had a quick install of Damn Small Linux on my 2gb cruzer flash drive.

I decided to follow [this guide]("http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/").
With this configuration it makes the partition ubuntu8 and the partition casper-rw. It is supposed to use the syslinux boot loader.
However, upon startup i get a grub terminal. looks like this:
[IMG]http://users.bigpond.net.au/hermanzone/p15/fig2grub.gif[/IMG]

So I'm not quite sure why its doing that when I boot from it at startup. It may be leftover from the dsl install but i had made new partitions on the flashdrive and there should be nothing left. Maybe I have to do a full wipe? and how would i go about that?
Other important info: I have a dell xps laptop, dualboot of windows xp and ubuntu 8.04. i installed the usb from the .iso using ubuntu, just like the guide told me to.

So. why is grub there?

---

### Post by meierfra. on 2008-05-21
> It may be leftover from the dsl install but i had made new partitions on the flashdrive and there should be nothing left


That would not erase the MBR. But you just need to fix the MBR of the flash drive. If you have  a working ubuntu you can follow this howto from pendrivelinux: 

[http://www.pendrivelinux.com/2007/03/07/install-a-new-mbr-to-your-usb-flash-device/]("http://www.pendrivelinux.com/2007/03/07/install-a-new-mbr-to-your-usb-flash-device/")

You should also be able to boot into the ubuntu on your flash drive by typing the following at  "grub>" prompt 


```

root (hd0,0)

chainloader +1

boot

```

---

### Post by werries on 2008-05-21
Ah, thank you so much! I thought it would have to be the mbr, i just had no idea how to go about fixing that...for...a flash drive....
thank you! successfully reset w/ syslinux booting.

---

