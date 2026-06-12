---
title: "Install iso to flash drive"
date: 2016-07-12
forum: General Help
---

### Post by 4kh3RAm on 2016-07-12
I have tried  both unetbootin and universal installer to install an iso to a flash drive.

None of them work.

Any recommendations as to what does work ?

---

### Post by sudodus on 2016-07-12
Check with ***md5sum*** that the download was successful. See this link: [UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Try with ***mkusb*** according to this link. It uses the cloning method to install from iso files (and other image files) to flash drives (and other mass storage devices). The cloning method is very reliable.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

The fastest way to start making USB boot drives is to install the mkusb PPA, install and update the mkusb package like all the other program packages.

If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb
```

-o-

***Edit:*** If you install from ubuntu-mate-16.04-desktop-amd64, you can use ***usb-creator-gtk version 0.3.2***, which comes with 16.04. But if you install from a previous version, it is better to use mkusb, which works in all current versions of Ubuntu and Ubuntu flavours (including 12.04, 14.04, 15.10, 16.04 and Yakkety Yak).

---

### Post by 4kh3RAm on 2016-07-12
Thanks a lot.

hashes were o.k. for isos.

---

### Post by sudodus on 2016-07-12
Please let us know if it works or not. In both cases details are valuable.

A. If it works, your description can help other users.

B. If it fails, please specify your computer to help us help you:

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Also, please tell us if you install alongside Windows, in that case which version, and if you install in UEFI or BIOS mode.

Finally, please describe what happens when you try to boot from the flash drive.

---

### Post by HermanAB on 2016-07-12
Howdy,

For the last two or three years already, the Ubuntu ISO files are prepared as 'multiboot', so you don't need any special software to prepare a bootable USB stick.  You can just write the ISO file to the stick using dd (or even cat).

Put the USB thingy in.
$ dmesg

Note the device name, prolly sdb.

Write the ISO to the thingy:
$ sudo dd if=filename.iso of=/dev/sdb

Long wait...

$ sync

Remove it.

La voila.

---

### Post by 4kh3RAm on 2016-07-12
> **sudodus said:**
> Please let us know if it works or not. In both cases details are valuable.

A. If it works, your description can help other users.

B. If it fails, please specify your computer to help us help you:

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Also, please tell us if you install alongside Windows, in that case which version, and if you install in UEFI or BIOS mode.

Finally, please describe what happens when you try to boot from the flash drive.

Makeusb worked great.

It produced a boot able flash drive from a clonezilla iso.

AMD A8-7600 Radeon R7, 10 Compute Cores 4C+6G

8 Gb RAM

Radeon R7 Graphics

I have a Tp-Link wireless card which lsusb does not detect.
But I use a direct Ethernet cable from my modem.

---

### Post by sudodus on 2016-07-12
Thanks for sharing your result, and if you think that the original problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED :-)

-o-

If you need help getting your wireless card working, please create a new thread in the [network forum](http://ubuntuforums.org/forumdisplay.php?f=336). It will increase your chances to get help by people who know about that kind of problems.

---

