---
title: "Live USB vs Bootable USB?"
date: 2017-12-10
forum: General Help
---

### Post by alright2 on 2017-12-10
I followed this tutorial from the ubuntu website:
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0)

It says to use Rufus.
I grabbed the Ubuntu 16.04.3 LTS image and ran the tool.

Is there a difference between a Live USB and a Bootable USB?
What I'm really trying to to do is create a Live USB with persistent data.

Other websites say to use UNetbootin or LinuxLive USB creator and other sites say not to.
I've tried both and they don't seem to work for me.

---

### Post by DuckHook on 2017-12-11
> **alright2 said:**
> …It says to use Rufus… Other websites say to use UNetbootin or LinuxLive USB creator and other sites say not to.
I've tried both and they don't seem to work for me.
Try Rufus first. If you can get to a Linux-based computer, [mkusb]("https://help.ubuntu.com/community/mkusb") is much the best LiveUSB tool in my opinion, but it only runs on Linux. There is a method using a self-extracting Windows file that I am frankly completely unfamiliar with (haven't used Windows in years), so you must experiment with it on your own: [https://help.ubuntu.com/community/mkusb#Windows](https://help.ubuntu.com/community/mkusb#Windows)
> Is there a difference between a Live USB and a Bootable USB?
What I'm really trying to to do is create a Live USB with persistent data.
A LiveUSB installs a read-only image (like the one you would get on a DVD), but creates and sets aside one additional partition for the storage of data. Since the read-only image is compressed, it can take up little space and the rest of the USB stick can be used for persistent data. This is necessary because a *non*-persistent LiveUSB works by first creating a RAMdisk, then loading the whole OS into this volatile virtual disk. Upon shutdown, your data would be lost. A *persistent* LiveUSB works the same way except that /home is mapped to the USB partition set aside for data. The whole OS still loads into RAM, but your data is on the separate partition in your USB stick.

A bootable USB is an altogether different animal. It is basically a conventional and fully functional installation residing on a USB stick. It does not load the whole OS into RAM. It uses the USB stick like a standard HDD, pulling only what routines it needs (leaving the rest on the stick), using the USB for swap, etc. It is built by using a LiveUSB/DVD and then making a typical install onto *another* blank USB stick instead of a HDD. The advantage is that you have what is basically a fully functional OS on a USB stick. The disadvantages are that USBs tend to be a lot slower, more fragile, and more unreliable than a HDD/SSD.

If you want a LiveUSB with persistence, try Rufus and if that doesn't work either, try mkusb.

---

### Post by alright2 on 2017-12-11
I tried Rufus. It doesn't have an option to create space for persistent data.
Although I did remember hearing that if you run Linux, or Ubuntu in this case, off a USB, that it would ask you to save any changes on shutdown, in effect making the USB persistent. I tried this but there was no option.


When I restart the PC with the Rufus made USB, it has a few options. One is to try out Ubuntu, and another is to install Ubuntu. If I accidentally pick to install Ubuntu, will it write over my Windows OS just like that? Or will it give me a couple prompts before actually going through with it? I wouldn't want the former to be so easily done and out in the open like that.


So to make a persistent LiveUSB, use mkusb?
And to make a bootable USB, what do I do?

---

### Post by alright2 on 2017-12-11
One of the reasons I wanted to use Linux was because I had heard that it's better at data recovery than Windows.

Do you know if there would be any difference in using the Linux version of Test Disk and Photorec and the Windows version?

When I chose "try out ubuntu", it loaded the desktop, and I could see the USB drives connected on the left side bar. But for some reason I couldn't see a SATA connected internal SSD which houses the Windows OS. Once I get my persistent data enabled, I'd like to connect an old SATA 3.5 HDD, and I was wondering if I have to do something special for Ubuntu to be able to see it so I can run Test Disk/Photorec.

---

### Post by dragonfly41 on 2017-12-11
> [COLOR=#000000]One of the reasons I wanted to use Linux was because I had heard that it's better at data recovery than Windows.[/COLOR]
Horses for courses.
Use Windows recovery tools to recover windows data. But often they come at a price tag.
Use Linux recovery tools to recover linux data.

Exceptions:
Testdisk and Photorec work on both Windows and Linux.
Another cross platform recovery tool which I have used is R-Linux.
[http://www.r-tt.com/free_linux_recovery/](http://www.r-tt.com/free_linux_recovery/)

Search "forensic data recovery".

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by C.S.Cameron on 2017-12-11
UNetbootin will make a drive with 4GB persistence max, (unless you are also using a home-rw file).
YUMI can use any size persistence file if installing NTFS.
Mkusb uses a casper-rw persistence partition of whatever size will fit on the drive.
If the drive is 8GB or larger you can do a Full install to it just like to an internal drive.

You can use Disks to mount your internal drive if it is not already mounted

---

### Post by DuckHook on 2017-12-13
> **alright2 said:**
> …If I accidentally pick to install Ubuntu, will it write over my Windows OS just like that? Or will it give me a couple prompts before actually going through with it?
It will not just automatically overwrite your whole disk without further warning. However, when doing such things, you are very close to the danger line. You should heed the warning in my signature. Monkeying around with USBs capable of installing OSes is a serious business. Make sure you have Windows recovery disks and all of your data backed up. Though I don't want to be alarmist, still, it's better to be safe than sorry.
> So to make a persistent LiveUSB, use mkusb?As C.S.Cameron has stated, at this point, yes.
> And to make a bootable USB, what do I do?Instead of defining your install medium as your resident SSD/HDD, install to another plugged in USB stick. You can also use an external USB drive (which I've done a number of times). It's just a matter of carefully selecting the external media instead of the internal one. But **BE CAREFUL**. Obviously, selecting the wrong media could hose your Windows install, hence the need for recovery disks and backups.
> **alright2 said:**
> One of the reasons I wanted to use Linux was because I had heard that it's better at data recovery than Windows.Not true. Linux is better at recovering Linux HDDs. Windows is better for Windows HDDs. Note what dragonfly41 says.
> …I could see the USB drives connected on the left side bar. But for some reason I couldn't see a SATA connected internal SSD which houses the Windows OS…
Not all of your disks will show up in the launcher. It is a very unreliable guide for what disks your system recognizes. A far better guide is an app specifically designed for reading and manipulating partitions, like *gparted*. Command line jockeys will use CLI tools like *fdisk* or *parted*. The upshot is that you shouldn't rely on the launcher ("the left side bar") as a proper indication of anything. It will often assume that you want access only to removable media.

---

