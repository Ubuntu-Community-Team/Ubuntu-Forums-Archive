---
title: "Installing programs on a persistent live usb"
date: 2016-12-27
forum: General Help
---

### Post by t0p on 2016-12-27
**[This is a duplicate thread.  I don't know how to destroy it.  Sorry! (Donno why *I'm* saying sorry, it was the stupid site with its unresponsiveness and latency that caused the duplication...]**
Is it possible to permanently install programs onto a persistent live usb of ubuntu?

The reason I ask is: I made a persistent live usb of ubuntu 14.04.1, and it didn't recognize my laptop's wifi stuff.  So I used a different computer to install **bcmwl-kernel-sourse**, a bunch of error messages were thrown up in the terminal, but the end result was that the live usb stick now sees and uses my laptop's wireless.  But when I tried to install other stuff to the stick, the apps stayed as long as the live session: use the stick later and the apps have gone.

So: how come the effects of **bcmwl-kernel-source** have lingered, when other program installs haven't?  Is there a way to make other apps stay on the stick?

I made my live usb using **Universal-USB-Installer 1.9.6.2 exe** (a Windows app, of course).

Cheers!

---

### Post by bashiergui on 2016-12-30
Search the file system for a file called ```
casper-rw
``` If that file doesn't exist then the usb drive is not persistent.

---

### Post by sudodus on 2016-12-30
You can install and update/upgrade program packages in a persistent live drive. But programs that are called before the overlay structure is activated will not work - the original program version will be used, for example the linux kernel.

[mkusb](https://help.ubuntu.com/community/mkusb) can create persistent live systems of Ubuntu and the Ubuntu family (Kubuntu, Lubuntu ... Xubuntu) and Debian Jessie. See [this link](http://ubuntuforums.org/showthread.php?t=2230389) for more details.

A persistent live system is sensitive to corruption of the file system, so it is a good idea to take frequent backups, which is possible with a backup tool in the system made with mkusb.

---

