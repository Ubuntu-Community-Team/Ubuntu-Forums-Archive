---
title: "Change Bootsplash Image"
date: 2022-01-23
forum: General Help
---

### Post by subcook on 2022-01-23
Hello all,

It's been quite awhile since I've both been around, and played w linux.  Currently using Ubuntu 20.04 LTS.  (Currently dual booting Win 11 with it off of my hard drive)

I can't quite remember how to apply my own picture for the bootsplash image.  I do remember that it's no longer as easy as editing the grub.cfg file.  All results I search for want me to install plymouth themes, which is not what I want, I just want to use an already existing pic

Little help ?

---

### Post by tea for one on 2022-01-24
For Grub version 2.04, open a terminal and navigate to the directory where your image resides:-
```
sudo cp [COLOR="#0000FF"]image.png[/COLOR] /boot/grub
```
```
sudo update-grub
```

---

### Post by subcook on 2022-01-26
I'm not sure what I'm doing wrong :

```
pleh@Laptop:~$ cd /boot/grub
pleh@Laptop:/boot/grub$ ls
fonts  gfxblacklist.txt  grub.cfg  grubenv  Ubuntu.jpg  unicode.pf2  x86_64-efi
pleh@Laptop:/boot/grub$ sudo update-grub
[sudo] password for pleh: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.11.0-46-generic
Found initrd image: /boot/initrd.img-5.11.0-46-generic
Found linux image: /boot/vmlinuz-5.11.0-43-generic
Found initrd image: /boot/initrd.img-5.11.0-43-generic
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings
done
pleh@Laptop:/boot/grub$
```

This does not seem to change the white on black screen (background) when selecting the OS.  I am attempting to apply the file/image Ubuntu.jpg
Grub 2.04

I thought maybe it may be a resolution issue, but have tried many.

---

### Post by tea for one on 2022-01-26
It looks like Grub is ignoring your Ubuntu.jpg image for some reason.
> GRUB 2 can use PNG, JPG/JPEG and TGA images for the background. The image must meet the following specifications:

[LIST]
[*]    JPG/JPEG images must be 8-bit (256 color). Else you will get errors saying "Too many Huffman tables". Since most of the time you will not want to limit yourself to 256 colors (which is totally yesteryear) you will probably find PNG much preferable.
[*]    Images should be non-indexed, RGB.
[*]
[*]    The GIMP image editor is one application which can edit images to conform to the GRUB 2 standards. Use the Image > Mode menu options to set the properties to RGB and ensure the mode is not set to Indexed. 
[/LIST]

Info from here [https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

I use png for my Grub splashscreen as below

```
edited@edited:/boot/grub$ ls
fonts             grub.cfg  [COLOR="#0000FF"]hummingbird01.png[/COLOR]  x86_64-efi
gfxblacklist.txt  grubenv   unicode.pf2
edited@edited:/boot/grub$
```
Updating Grub should then find the background image.

```
edited@edited:~$ sudo update-grub
[sudo] password for edited: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found background image: [COLOR="#0000FF"]hummingbird01.png[/COLOR]
Found linux image: /boot/vmlinuz-5.13.0-27-generic
Found initrd image: /boot/initrd.img-5.13.0-27-generic
Found linux image: /boot/vmlinuz-5.13.0-25-generic
Found initrd image: /boot/initrd.img-5.13.0-25-generic
Found linux image: /boot/vmlinuz-5.11.0-46-generic
Found initrd image: /boot/initrd.img-5.11.0-46-generic
Found Ubuntu 21.10 (21.10) on /dev/sda2
Adding boot menu entry for UEFI Firmware Settings
done
edited@edited:~$
```

---

### Post by subcook on 2022-01-27
Thank you, your initial answer worked.

I'm convinced that my issue was that I was not using an 8 bit 256 color picture

Thanks again

---

### Post by tea for one on 2022-01-27
Splendid - pleased to have helped.

If you mark the thread as solved, other users/searchers may find it useful.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

