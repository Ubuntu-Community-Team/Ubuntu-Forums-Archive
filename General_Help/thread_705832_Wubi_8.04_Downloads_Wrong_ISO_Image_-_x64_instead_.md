---
title: "Wubi 8.04 Downloads Wrong ISO Image - x64 instead of x32 / x86"
date: 2008-02-23
forum: General Help
---

### Post by joethecomputer on 2008-02-23
I have wubi 8.04 on my windows vista operating system with an **Intel Quad Core Q6600** and wubi always downloads the x64 verison of the alpha5 iso instead of the x32/x86 version. is there any way that i can get wubi to download the x32 or any other workaround?

Cheers,

---

### Post by Derek Chai on 2008-02-23
download it manually

---

### Post by joethecomputer on 2008-02-23
> **Derek Chai said:**
> download it manually
is it really that simple?
so just place it in the same directory as the wubi installer?

---

### Post by Derek Chai on 2008-02-23
Yeah that's what I do.

---

### Post by ago on 2008-02-24
amd64 is ok for all 64 bit CPU, both intel or amd. I concur that the amd64 name is misleading. Anyway core duo, core quad and so on are 64 bit cpu. Anyway you can either pre-download a 32 bit ISO, if that is what you want, or run wubi with "--32bit" argument.

---

### Post by gluko on 2008-04-04
> **ago said:**
> Anyway you can either pre-download a 32 bit ISO, if that is what you want, or run wubi with "--32bit" argument.
I wanted to install the x86 version instead of the amd64 one. i used the --32bit command but uname -a reports that i the x86-64 version is installed. nevertheless the iso in the ubuntu-backup folder after uninstall ist named "hardy-desktop-i386.iso".

Edit: Yesterday, i also downloaded the x86 iso of hardy and copyed it in the same folder as the wubi.exe (nothing else in the folder), but it still installed the x86_64 version of hardy (at least after uname -a).

i know my english is horrible -.-

---

### Post by ago on 2008-04-05
If it finds the amd iso around it will still use it (bug). You can simply change the extension of the 64bit iso and run wubi again

---

### Post by crimsontime on 2008-04-25
I used Wubi to install on my dell inspiron 1525 and it also downloaded the wrong iso.  I'm on 32 bit and it downloaded ubuntu-8.04-desktop-amd64.iso.

---

### Post by ago on 2008-04-26
You might have a 64 machine after all... Check that.

---

### Post by GeckoPie on 2008-04-26
I had this same problem, I've only just realized after rebooting from a failed install (just produced a black screen).  I looked in C:\ubuntu and saw that theres an amd64 iso in there; I'm 100% sure this isn't a 64bit laptop...its running a 32bit AMD Sempron.
Anyhow, am downloading the correct 32bit iso via torrent now to try.

---

### Post by ago on 2008-04-26
ok let me know if that fixes it

---

