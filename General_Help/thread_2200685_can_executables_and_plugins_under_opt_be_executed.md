---
title: "can executables and plugins under opt be executed?"
date: 2014-01-20
forum: General Help
---

### Post by leonbravo on 2014-01-20
Hi, I'm using ubuntu 12.04  currently, I'm expiencing troubles for using the gtalk pluging in firefox and chromium.

I tried installing Chrome, but as all executables are installed in /opt/... all these files seem to be banned for execution. I tried all flavours of commands to allow execution, but It only can be accessed for sudoers. 


other words:  If I try /opt/google/chrome$ ./google-chrome
I get a permission denied

and with sudo ./google-chrome

nothing happens.

---

### Post by TheFu on 2014-01-20
Linux uses file permissions to determine if a file can be "executed" or not.  Extensions mean next to nothing at all, except to a few GUI programs. 
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) will explain things better than I can.

---

### Post by leonbravo on 2014-01-20
Apparently, /opt mounted in a different partion creates conflicts with executing programs from there.

I changed my mounting point reinstalled my programs and plugins to /opt in the file system and that solved my problem

---

### Post by steeldriver on 2014-01-20
I can only think of a couple of cases where that would happen

1. if the partition containing /opt was mounted explicitly without execute permissions (with the 'noexec' mount option for example)

2. the partition was formatted with a filesystem that does not support full *nix style permissions/ownerships (such as FAT or NTFS)

---

