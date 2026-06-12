---
title: "Installing Ubuntu 18 alongside Windows 10 and access..."
date: 2018-12-14
forum: General Help
---

### Post by concerro on 2018-12-14
Right now I have Ubuntu on a USB stick and I can still access my Windows 10 C drive. 

I know that I can install Ubuntu 18 on an external HD, but I may have to set Secure Boot to disabled according to instructions I found online.
[COLOR=#242729][FONT=inherit]
My question is this. If I disable secure boot, which disables UEFI will I still be able to access files on Windows 10, and have a decent chance at using WINE or PlayonLinux to use Windows based programs?

PS: I did a search, but I didn't find anything. 



[/FONT][/COLOR]

---

### Post by yancek on 2018-12-14
I would suggest you begin by reading the Ubuntu documentation at the link below which explains in detail what you are trying to accomplish.  Much better to go to the actual source for information.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> [COLOR=#242729][FONT=inherit]My question is this. If I disable secure boot, which disables UEFI[/FONT][/COLOR]

Disabling Secure Boot does NOT disable UEFI.  Secure is a small part/option of the overall UEFI system and you should be able to boot windows 10 with Secure Boot disabled and you should be able to access a windows partition.  Not a good idea to access windows system file from Linux nor is the reverse a good option.  Data files should be no problem.

I'm not sure what using wine or playonlinux has to do with UEFI or Secure Boot?

---

