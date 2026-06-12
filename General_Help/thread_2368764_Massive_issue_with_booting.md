---
title: "Massive issue with booting"
date: 2017-08-14
forum: General Help
---

### Post by chaseb1357 on 2017-08-14
So I had antegros installed on my laptops hard drive, and every was customized the way I like it, so I prefer not to reinstall it. I had a USB stick with Linuxmint installed on it and I was adding Ubuntu to that USB to dual boot and went through that installation process. After it finished something changed in my hard drive because I can't boot my computer without the USB plugged in, and when it is plugged in all I have are options for Linuxmint and Ubuntu. It just keeps booting and saying "no such device: 4cc1403b-5210-4b49-9a50-978b6d0dc973.    Entering rescue mode."

---

### Post by arsenic23 on 2017-08-14
Sounds like grub got installed on the USB drive and your MBR is pointing there instead of to your hard drive now.  Do you have multiple drives?  Do you know what drive grub was on to begin with?  Safe bet is sda, but if you have an interesting setup it could be something else.

If you stick the USB drive in and then boot to the OS on your hard drive you can reinstall grub form the terminal:
```
sudo grub-install /dev/$
$ is the drive you want grub on.  more then likely
/dev/sda
```

There's a bunch of guides on recovering a lost grub, most notably you have to do it after installing Windows.  If you need more information, that would be a good place to start looking.

---

