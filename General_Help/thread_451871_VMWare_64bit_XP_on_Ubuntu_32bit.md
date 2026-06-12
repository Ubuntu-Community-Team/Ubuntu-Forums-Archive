---
title: "VMWare 64bit XP on Ubuntu 32bit?"
date: 2007-05-22
forum: General Help
---

### Post by elfstone214 on 2007-05-22
Hi all,

I have been wondering if it is possible to run Windows 64bit XP through VMWare from Ubuntu 7.04 (32bit). I tried it once and it gave me an error saying basically it could not run because Windows was 64bit (I cant remember the exact error). Is there any way around this?

Thanks!

---

### Post by MetalMusicAddict on 2007-05-22
I thought you could *if* you have a 64bit processor.

---

### Post by elfstone214 on 2007-05-22
> **MetalMusicAddict said:**
> I thought you could *if* you have a 64bit processor.

I have a Core 2 Duo which is a 64bit processor, I can run Windows X64 fine as a dual boot but VMWare will not let me run it from Ubuntu (32bit). I am wondering if it is related to trying to run a 64bit OS with 32bit application?

---

### Post by lintoolman on 2007-05-23
AFAIK all VMWARE products are 32bit. :(   

I've run 64bit Linux distro's with no problem on computers with 64bit processors using 32bit vmware server, workstation and ESX.  I don't think you can run 64bit os's on 32bit CPU. 

Another consideration, I run Vmware server at home on Feisty x64.  The last time I checked Ubuntu was not on the supported host os list.  VMware server runs fine on my server (no X), but is not usable on my Feisty x64 desktop (gnome).  I installed the console to connect to my server and everything runs as great as expected.  

I think in your case you should be able to run any 64bit windows as long as it's supported by the vmware version you are running.  You might poke around the vmware forum for better info.

---

### Post by elfstone214 on 2007-05-28
I ditched Windows x64 and installed XP 32bit, works just fine now ;)

---

