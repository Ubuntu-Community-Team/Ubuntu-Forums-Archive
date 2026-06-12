---
title: "Persistent problem"
date: 2013-06-15
forum: General Help
---

### Post by Lloydb39 on 2013-06-15
Someone got their knickers in a twist because I accidentally posted this problem twice, and closed the thread. (I would delete the posts, if I knew how.) But the problem remains if anyone would like to take a crack at it.
I have a ten-year-old Dell laptop I'm trying to keep running. It is original except for added memory. It has been working pretty well with Xubuntu 11.04 but for some reason it decided to quit booting. I tried to boot with the original disk but no go. Finally, I got it to boot to a Puppy Linux disk but Puppy wouldn't install on the hard drive and I still don't know why. If I thought it was just the drive I would get a new, bigger one but I don't want to spring for that if it is something else that I might not be able to fix. Can/would anyone tell me know to diagnose the problem? Or should I just retire the Dell for good?

---

### Post by dino99 on 2013-06-15
so the bios seems to works, right ?
have you tried with the boot option ?  [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
maybe also check the partitions, with gparted or partedmagic on a cd/usb about possible partition(s) errors.

---

### Post by Lloydb39 on 2013-06-15
Thank you. I'll explore that. I did get gparted running and changed the main partition to ext2 instead of ext4 and -- I think -- I got Puppy installed. Testing it now. If Puppy will boot and run, maybe I can get it back to a late version of Xubuntu at some point and I'll mark this solved.

---

### Post by Lloydb39 on 2013-06-15
Well, it is installed but I can't get on the net. The network wizard won't work unless I tell it "auto DHCP" and when i do it tells me I'm connected, but I'm not and I can't download a browser or do anything else via the Web. (It did connect previously with Xubuntu without any problem. At one point it also connected from the live CD! Very irritating...

---

### Post by UltimateCat on 2013-06-15
With Puppy Linux try running:
```
lspci

```
Read through that output and look for your NIC network interface card. If you have access to another computer go online and look for the driver for your NIC-
That; theoretically; should help--

If lspci is to hard to read thru try:
```
lspci | grep -i network

```

Hope that helps-;)

---

### Post by Lloydb39 on 2013-06-16
Thank you both. The boot options info was helpful. Here's the update in case anyone has a similar problem. Xubuntu 12.04 is installed, booting and running. The only glitch is that it WILL not work with the Broadcom STA driver it wants to install. That crashes and breaks the system and I had to reinstall. I have the Broadcom 4306 which apparently needs the B43 driver and fwcutter installer but, guess what, those don't work anymore. It fails when they try to fetch the driver that works with this antique network card. The workaround is that I just stick a Belkin USB device in and it instantly hooks up to my network. Would like to keep using the old network card if anyone knows how to make it work, but if necessary I can keep running as is.

---

### Post by carboi82 on 2013-06-16
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902) That might help you with your network card issues

---

