---
title: "Windows XP won't boot after Ubuntu 13.04 installation"
date: 2013-07-12
forum: General Help
---

### Post by Twux245 on 2013-07-12
I've been looking for a solution all over the place and yet no luck in finding a solution. I keep running into broken links and/or no solutions at all.

When the grub menu pops up and I choose Ubuntu it runs smooth. When I choose XP the loading screen pops up and after 3-4 seconds it freezes and I go back to the grub menu. I've tried [this]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") but it didn't work and I don't know what I did with Boot Repair that somehow I messed it up. The grub won't start anymore, I go to straight to a black screen that says:

> Missing operation system
Operating system not found

Dual Boot installation. I have both installation discs. I know it has to do something with the grub installing on windows or something like that.

---

### Post by Twux245 on 2013-07-13
6 hours and yet no replies? Wow...

---

### Post by oldfred on 2013-07-13
Please only bump once per 24 hours. Many that volunteer to help here are in different time zones or just not always available.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Twux245 on 2013-07-14
> **oldfred said:**
> Please only bump once per 24 hours. Many that volunteer to help here are in different time zones or just not always available.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Thanks for notifying me about the 24 hour bump rule. Right now I'm stuck on a black screen that says:

```
Missing operation system
Operating system not found
```

Grub menu doesn't even appear so I can't choose ubuntu.

---

### Post by oldfred on 2013-07-14
That seems like a BIOS error.
Some BIOS have to have a boot flag or they will not let you boot even though grub does not need a boot flag. Make sure you have a boot flag on a primary partition.
Otherwise you may not have a boot loader in the MBR. Boot-Repair can fix that.

---

