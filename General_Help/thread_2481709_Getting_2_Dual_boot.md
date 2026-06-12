---
title: "Getting 2 Dual boot?"
date: 2022-12-07
forum: General Help
---

### Post by daanheuvelbeuk on 2022-12-07
Recently I got myself a superfast configured Windows 11 gaming system. I thought to build in my Ubuntu hard drive and continue with dual booting. But alas, my "MSI Click BIOS 5" is configured to 'fast boot'. And I do not have a way to configure a boot delay, or even to show the Boot window all the time. So now I have problems accessing my Ubuntu distribution. 

At the moment I have installed 'Oracle VM VirtualBox' where I can boot Ubuntu. But I cannot access my Ubuntu drive, as VirtualBox uses Windows Explorer to look for drives, and Windows is unable to see EXT formatted drives. 

I installed "[Windows Subsystem for Linux]("https://learn.microsoft.com/nl-nl/windows/wsl/setup/environment#set-up-your-linux-user-info")", have no idea what drive it uses, tried lsblk and got the following output:
```
thor@Odin:~$ lsblk
NAME MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda    8:0    0   256G  0 disk
sdb    8:16   0 339.8M  1 disk
sdc    8:32   0   256G  0 disk /
```

So, anyone know what I can do?

---

### Post by tea for one on 2022-12-07
> **daanheuvelbeuk said:**
> But alas, my "MSI Click BIOS 5" is configured to 'fast boot'. And I do not have a way to configure a boot delay, or even to show the Boot window all the time. So now I have problems accessing my Ubuntu distribution.
This is probably a UEFI setting?
Can you not access the UEFI settings and disable it?

---

