---
title: "Ubuntu Server for minimal system setup?"
date: 2014-01-29
forum: General Help
---

### Post by shadowfox1991 on 2014-01-29
Hello,

I would like to install a bare minimum ubuntu system on my computer that I can later customize to my liking (not a fan of Unity and the Amazon stuff included in the newer versions) and I was wondering if installing the Ubuntu Server would satisfy my goal. I am not sure what the differences are between the desktop and server versions, although I've read that there are none and just wanted to make sure that the server is essentially just like the desktop version but minimal.

I am aware that there exists a mini.iso for these types of installations, but I've read somewhere that the mini.iso does not allow for EFI boot, so I guess it is not going to work. :(

Thank you!

---

### Post by Tristan_Williams on 2014-01-30
There are two answers to this:

Yes, the Server editions are ALMOST a bare minimum. 
Ther server editions only contain command-line software, and do not include a desktop environment.
They DO, however, contain various server administration packages, which you probably will not need unless you are running a server.

As for the mini.iso (Ubuntu Minimal)

Ubuntu Minimal is the ABSOLUTE MINUMUM. You can have Ubuntu smaller than this. It only includes the base of Linux, core system utilities, the Dpkg package management system, and the Ubuntu defaults for system files. Presonally, I will never install Ubuntu unless it is Ubuntu Minimal.
But no, it does not support EFI. 
You can use it on an EFI system, but it will be put into BIOS compatability mode.
So if you require EFI compatability, Go with Ubuntu Server.

Also, you said you were tired of Unity...
Have you considered any others, such as Xfce.
I personally recommend Xfce, because it is by far the most customizable, and one of the fastest and most lightweight.

---

