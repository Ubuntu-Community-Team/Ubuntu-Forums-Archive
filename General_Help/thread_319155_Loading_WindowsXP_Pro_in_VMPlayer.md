---
title: "Loading WindowsXP Pro in VMPlayer"
date: 2006-12-15
forum: General Help
---

### Post by coolboarderguy on 2006-12-15
Hi All,

I created an .iso from the Windows XP Pro files stored on a hidden partition on my Toshiba Tecra A7. I then placed it in my .vmware directory where it is referenced in my .vmx file but when running vmplayer, it tells me it cannot find an OS. Is it possible that the .iso file needs to be a bootable one? If so, how is that done?

---

### Post by PilotJLR on 2006-12-15
Yes, it needs to be bootable. I don't think you can make this work, though, because hidden partitions usually include OEM restore tools, not complete os's. Even if you could somehow get it to install, the vmware virtual chipset is different from the OEM chipset, so it wouldn't work for both technical and licensing reasons.
I think your only real option is a full XP CD... or a copy of the Vista RC1 from last month, if you can still find one.

And also - VMplayer won't work for this. Need Workstation or Server.

---

### Post by AndyCooll on 2006-12-15
This is an excellent thread for getting XP to work with VMware: [ HowTo: Windows (XP) on Ubuntu with VMWare Server]("http://ubuntuforums.org/showthread.php?t=183209")

:cool:

---

### Post by useResa on 2006-12-15
> **AndyCooll said:**
> This is an excellent thread for getting XP to work with VMware: [ HowTo: Windows (XP) on Ubuntu with VMWare Server]("http://ubuntuforums.org/showthread.php?t=183209")

:cool:
I am with you AndyCooll on the fact that VMWare Server is great for running other OS's (even WinXP if you so please ;)), however I think the question was about getting it running in VMPlayer.

[color=red]@coolboarderguy:[/color] Although you may have noticed let me please stress that the link relates to VMWare Server and not VMPlayer

---

### Post by dmartinsca on 2006-12-15
You'll need an actual windows xp cd. I have heard it is legal to download a copy of the cd if you have a valid product key for that version. Can anyone clarify this?

---

