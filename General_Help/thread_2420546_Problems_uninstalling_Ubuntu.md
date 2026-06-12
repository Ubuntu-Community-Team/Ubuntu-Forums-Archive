---
title: "Problems uninstalling Ubuntu"
date: 2019-06-06
forum: General Help
---

### Post by urbanfish99 on 2019-06-06
Hi guys, wondering if anyone could offer some help.

I recently switched from Windows vista to Ubuntu on an OEM Acer aspire laptop. I then decided to switch back to windows as I was having trouble using Ubuntu. Managed to somehow mess the laptop up. When I boot I get a message now that says something about the grub file missing. I also stupidly managed to lose the usb boot of Ubuntu I had. I do have the windows vista cd boot but when I run that from the bios setup I get the message "fail to get disk 0 partition 1 drive letter". Then it restarts. All in all there seems to be no way to get past either of these two screens.

Ultimately I'd like to get back on to windows. Then from there upgrade the vista. Also another issue I was having was finding difficulty upgrading this OEM laptop. It's as if it's limited to vista only!

Any help at all would be widely appreciated. Thanks so much in advance.

Alex

---

### Post by Autodave on 2019-06-06
Were you trying to dual boot or did you just want to install 'buntu in place of Windows?

Since that machine was running XP, it is obviously an older machine.  What version of 'buntu did you install?  What kind of problems were you having?

Assuming that you installed the Ubuntu desktop, I can understand why you would have problems with that: that desktop is probably way to heavy for that machine.

Can you give us some specs on your Acer?

---

### Post by Impavidus on 2019-06-06
The trouble you had using Ubuntu can probably be solved. Whether you'll like Ubuntu, we cannot say. You don't have to be a programmer to run Linux, but it's not for everyone.

I guess you deleted the Ubuntu partition on the hard drive. Grub (the bootloader) is still installed in the master boot record, but can no longer find its files, which were in the Ubuntu partition. That gives the error message. I think the Windows installer gets confused by seeing a formatted hard drive without a Windows partition. Wiping the first megabyte of the drive may help. It's easy to do from an Ubuntu live disk.

So, do you want to get back to Windows right away, or do you give Ubuntu a second chance? Of course, on this forum, we all like Ubuntu or its various flavours. In any case, you may need an Ubuntu live disk to wipe the first megabyte of the hard drive, or you could take it out of the computer, plug it into a different computer and use that to wipe it.

If you consider giving Ubuntu a second chance, show us some system specs, so we can tell wether it will run Ubuntu or needs one of the lighter flavours. Most important are CPU, RAM and graphics.

---

### Post by HermanAB on 2019-06-06
Howdy,

Vista... that must have been the saddest version of Windows, ever.  The problem with your very old computer is that it won't run the latest version of either Windows or Linux properly - it is too slow and has too little RAM.

If you really want to go back to some kind of Windows, then you could zero the first part of the disk drive, so that the Windows install CD will think that it is a new computer system - then it will install.  Being an old computer, you should get a copy of Windows 7 or 8.1 maybe, rather than XP or Vista, but no matter which, the machine will not last very long, before it will be infested with malware, since the old versions of Windows are not supported anymore.

Your best bet would be to install a light weight system, such as Xubuntu, Lubuntu, Slackware or OpenBSD.  With any one of those, the machine will work properly again and it will be practically immune to malware.  Compared to vista, it will zoom like a new machine.

Of all the Linux distributions, Slackware is the fastest.  Of the BSDs, the best one for an older laptop is OpenBSD.
[https://www.aeronetworks.ca/2016/06/slackware-linux.html](https://www.aeronetworks.ca/2016/06/slackware-linux.html)
[https://www.aeronetworks.ca/2017/02/openbsd-on-netbook.html](https://www.aeronetworks.ca/2017/02/openbsd-on-netbook.html)

---

