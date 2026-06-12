---
title: "transferring folders to windows"
date: 2022-03-15
forum: General Help
---

### Post by Caril Chasens on 2022-03-15
I need to transfer some folders from an old computer with Ubuntu 14.04 to a Windows 10 computer using a usb external drive. The windows computer sees the folders but will not download them. Tried a couple of drives.. with one of them I get error 0x80004005 and with the other, nothing happens. What do I need to do?

---

### Post by dragonfly41 on 2022-03-15
Just one way that I have used before. There are other methods.
R-Linux can install on Windows and Ubuntu.
R-Linux on Windows can view and manage Ubuntu files such as saving to USB or DropBox.

But look around other ideas posted here before jumping to R-Linux.

[P.S.] Another thought.  

Launch "Try Ubuntu" in LiveUSB plugged into old 14.04 laptop and transfer files to DropBox or another USB drive.

Create an NTFS formatted partition in Windows to receive files. I use this partition in Windows to share files between Ubuntu and Windows. Be alert to permissions required if other than say *.doc files.

---

### Post by HermanAB on 2022-03-16
TIMTOWTDI:
The easiest way would be by using a freshly NTFS formatted USB widget.

However, note that Windows natively supports FTP.  With Windows file browser, you can connect to a remote FTP server or use the command line FTP utility, although the third party FileZilla or WinSCP are a little easier to use.

Therefore you could install an Anonymous FTP server on either Linux or Windows (FileZilla) and copy the files over the network.

A third way is to install OpenSSH server on Linux and use WinSCP or FileZilla to copy the files over the network.

---

### Post by Impavidus on 2022-03-16
It looks like filessytem damage on the usb drive.

You can use either Windows or Ubuntu to format the usb drive as ntfs. Always make sure you unmount the usb drive before removing it. It's called eject or savely remove or something like that. Many Windows users don't, which usually works on Windows as Windows flushes writes to usb drives pretty quickly, but Ubuntu doesn't, to prolong drive life. So on Ubuntu, you really have to savely remove the drive or you'll have a partial write.

---

### Post by Caril Chasens on 2022-03-18
thank you

---

