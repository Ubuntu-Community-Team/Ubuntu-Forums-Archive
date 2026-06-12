---
title: "Boot-able USB Drive"
date: 2015-01-11
forum: General Help
---

### Post by trackmagic on 2015-01-11
I am trying to make a bootable USB drive. Everything I found via google is for making a bootable Ubuntu OS from a USB drive.

I am trying to make a bootable drive to install Liberte on. The format disk utility I used for formatting does not give a "bootable" option like I am used to from my Windows days.

---

### Post by Z80A on 2015-01-11
Wouldn't you just download the ISO image file from [http://dee.su/liberte](http://dee.su/liberte)[COLOR=#a9a9a9] and use the normal Ubuntu Startup Disk Creator (link)? You can use it with any ISO image you like and no other tool is needed and you will have a bootable USB drive right away[/COLOR].

Edit: as pointed out by ajgreeny below, Ubuntu Startup Disk Creator indeed only works with Ubuntu based distros; UNetbootin is the way to go, sorry...

---

### Post by trackmagic on 2015-01-11
I tried that. When I select the ISO file to use in the Startup Disk creator nothing happens. Have you ever seen this before? By the way I am using 14.04.

---

### Post by ajgreeny on 2015-01-11
The ubuntu-startupdisk-creator works with ubuntu, or ubuntu based .iso files only, so may not work with liberte.

However, unetbootin which is available in the repos will make a bootable usb from any iso; that is the application to use, I think, though the website mentioned by Z80A may tell you how they recommend you to do it.

---

### Post by trackmagic on 2015-01-11
I have never used unetbootin until now. It did appear to load the liberte ISO image onto the thumb drive, but when I tried to boot it it booted some unetbootin screen that looked like it was written in code and expected me to type something.

A friend of mine made me a liberte usb install once. He claims all I should need to do is make the USB drive bootable and copy and past the install files onto the drive. I guess it goes through the install process the first time you boot from the device.

Is there a way to just make a bootable USB drive? It seems like this should be easy.

---

