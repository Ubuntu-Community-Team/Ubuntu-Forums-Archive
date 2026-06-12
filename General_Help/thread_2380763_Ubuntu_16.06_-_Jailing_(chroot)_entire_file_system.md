---
title: "Ubuntu 16.06 - Jailing (chroot) entire file system residing on separate existing HDD"
date: 2017-12-21
forum: General Help
---

### Post by circlex on 2017-12-21
[LEFT][COLOR=#222222][FONT=&amp]I have an old hard drive that has Ubuntu 10.04 LTS desktop  installed with LAMP, a python game server and dnsmasq.  It was originally set up on a 2 drive dual boot PC with Windows 10 on the master drive.  The PC that it was installed in had died and I&#8217;ve recently purchased a new PC.  I am unable to boot or dual boot with this old drive because the new PC is UEFI and the old drive was legacy BIOS; so the new PC doesn't recognize it.  I  can, however, access it via [LEFT][COLOR=#222222][FONT=Verdana]Ubuntu desktop 16.04 as [/FONT][/COLOR]a hyper-v guest on Windows 10 and have found the file system to be intact. 
[/LEFT]

As a work around I would like to try and place the Ubuntu 10.04 OS on the old drive inside Ubuntu 16.04 as a jailed chroot and have it operate as it did on the old PC, i.e. run the servers and communicate through certain ports with clients on the internet and a LAN.  I have reviewed several chroot threads but they only cover chroot and debchroot from scratch.  I need to implement the same concept but with the existing file system as I have described.

[/FONT][/COLOR][COLOR=#222222][FONT=&amp]Can anyone explain how I should approach this if it is indeed a workable solution?[/FONT][/COLOR][/LEFT]

---

### Post by TheFu on 2017-12-21
I wouldn't use a chroot.  I'd just virtualize the old OS, then migrate it into a 16.04 VM as I can.  10.04 cannot be on the interent - not safe, as you know. If a VM was determined to be "too heavy" - which I doubt - then move it into a container (docker, lxd, lxc).  Containers do what chroot does and so, so, so, much more.

IMHO.

---

### Post by circlex on 2017-12-21
"virtualize the old OS, then migrate it into a 16.04 VM" How is this done?

---

### Post by TheFu on 2017-12-28
> **circlex said:**
> "virtualize the old OS, then migrate it into a 16.04 VM" How is this done?

That answer is beyond what can be explained here. Sorry.  Hopefully, you've kept going.

Did some research. Did some testing and got everything solved. If you get stuck, ask specific questions.  

Much will depend on the hypervisor you choose and the settings you go with whether anyone can help.  We all have different requirements, so we make different choices.  Linux is extremely flexible.  I use KVM + libvirt + virt-manager.

---

### Post by circlex on 2018-01-01
I am looking into placing the applications into Docker containers within the Ubuntu 16.04 Guest on Hyper-V.  I will return to ask questions when necessary.  Your suggestions were very appreciated as I now have a path to blaze.

---

### Post by TheFu on 2018-01-01
Most people here won't be able to help with hyper-v, as you might imagine.

---

