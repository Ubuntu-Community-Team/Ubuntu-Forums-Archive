---
title: "Startup disc creater doesn't bring up iso file(s)"
date: 2022-04-20
forum: General Help
---

### Post by beedee33 on 2022-04-20
This has been driving me mad for hours:  The "startup creator" readily shows my USB drive, but not a file or files to create the iso.  Where the hell is the source disc image to write?  Is it supposed to be on my comp somewhere?  Have I got to download it from somewhere?  Any help really appreciated.

---

### Post by GhX6GZMB on 2022-04-20
Of course you have to download it. Do you think it appears from free air?

---

### Post by grahammechanical on 2022-04-20
> Have I got to download it from somewhere?

To put it simply, the answer is yes. Linux distributions are packed into an archive called an ISO image. The International Organization for Standardization defines the standards for the particular archive standard used by the distributors of Linux. If you told us what particular Linux distribution you wanted to install then we would be able to tell you from where you could download the ISO image.

This is where we download the latest versions of \Ubuntu. If you wait until the end of April this web site will offer Ubuntu 20.04 LTS and Ubuntu 22.04 LTS instead of Ubuntu 21.10 which will reach end of life in a few months although at present it is the "latest" version of Ubuntu.

[https://ubuntu.com/#download](https://ubuntu.com/#download)

And then there are the ISO images of distributions built on Ubuntu but with different desktop environments. Such as Xubuntu, Lubuntu, Kubuntu, Ubuntu Mate and others.

Regards

---

### Post by beedee33 on 2022-04-21
I do not want to install "Ubuntu", I'm already running Ubuntu 20.10.

I eventually want to have a dual boot with Windows 7 (for games), and put in on my single M2 drive.  But I can't make a partition for W7 as my drive is of course "busy".

So I need to make a "startup iso" on a flashdrive with the "startup disc creator" so I can temporarily boot from it enabling me to unmount my M2 drive and make a partition for a W7 install.

But the "startup disc creator" window just shows my USB flashdrive, and the top space entitled "Source disc image (.iso)" is greyed out as is the "make startup Disk".

So my question is: Where do I get the "source" from?  And exactly what is it?

---

### Post by beedee33 on 2022-04-21
Ah!  Do I download the same install as I did for initial install of Ubuntu 20.10, and the "startup disc creator" extracts what it needs from that and makes the startup program?

---

### Post by HermanAB on 2022-04-21
Any Linux installation ISO file can be written to a USB widget and used to boot your machine.  You don’t even need special tools to do that, provided that you have basic knowledge of file and device names, for example:
# cat linux.iso > /dev/sdd

---

### Post by beedee33 on 2022-04-21
I think my last post answered my problem in plain English?

---

### Post by sudodus on 2022-04-23
Please notice that Ubuntu 20.10 has passed end of life and no longer receives any security updates.

Instead I suggest that you download and use a version that is still supported. See [this link](https://ubuntuforums.org/showthread.php?t=2230389&p=13540865#post13540865) and links from it, and

[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)

---

### Post by HermanAB on 2022-04-23
You don’t need to make a special disc.  The normal install disc should have all the utilities you need.  So just make a normal install disc on a usb widget.

---

