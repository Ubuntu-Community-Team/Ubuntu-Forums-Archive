---
title: "Running Ubuntu on 16 GB live USB Drive. OpenFOAM error states only 1 GB is available."
date: 2018-08-25
forum: General Help
---

### Post by austincibulka on 2018-08-25
Hello,

I have windows 8.1. I successfully used Rufus to put Ubuntu 16.04 on my brand new 16 GB flash drive. I am running Ubuntu with no apparent problems. I attempted to download the openFOAM installer on [www.cfdsupport.com]("http://www.cfd-support.com"). The installer downloads successfully, but when I attempt to run the installer in the Ubuntu terminal, I get the following error message:

-- Detected GLIBC version 2.23
-- GLIBC's version is >= 2.13
-- Welcome to the installation of OpenFOAM-in-Box-18.06v1!
-- Starting installation from ./OpenFOAM-in-Box-18.06-r989-linux64-install.sh
-- Destination directory is /home/ubuntu
-- Using temp in /tmp
-- Checking destination
-- Calculating free space
-- Available space 1 GiB


** OpenFOAM-in-Box-18.06v1 needs at least 10 GiB of free space!
** Installation FAILED!

I have gone into my disks in Ubuntu and it says that I have 14 GB of 16 GB free on my SanDisk USB drive.

Can anyone help me with this issue?

Thank you,
Austin Cibulka

---

### Post by oldfred on 2018-08-25
On a flash drive you can have a standard live installer, live installer with persistence and a full install.
The standard live installer is a working system where you can test that system works, use as a repair tool or use to do a full install of Ubuntu to another drive. It really is just like the DVD as you cannot update it.
The addition of persistence allows you to save some data with live installer. But it still cannot be updated. Some software may be able to be saved & installed, but you have to reinstall with each reboot.
Full install is the working Ubuntu install, it can be one an internal drive or an external drive.

       Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[URL="http://ubuntuforums.org/showthread.php?t=1655412"]http://ubuntuforums.org/showthread.php?t=1655412

      [/URL]
 Persistent  install
[https://help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)
[https://askubuntu.com/questions/1025847/usb-live-pen-persistent-boot-disk-in-uefi](https://askubuntu.com/questions/1025847/usb-live-pen-persistent-boot-disk-in-uefi)
[https://askubuntu.com/questions/1012717/what-is-a-cheap-simple-way-to-try-out-new-os-releases-without-committing-to-it/1012752#1012752](https://askubuntu.com/questions/1012717/what-is-a-cheap-simple-way-to-try-out-new-os-releases-without-committing-to-it/1012752#1012752) 
    [URL="http://ubuntuforums.org/showthread.php?t=1655412"]
[/URL]

---

