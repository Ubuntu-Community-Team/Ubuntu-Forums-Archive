---
title: "Understanding wubi offering - my brain hurts!"
date: 2008-01-23
forum: General Help
---

### Post by candtalan on 2008-01-23
The wubi install went well, from XP, which itself was originally installed as FAT32 not ntfs (another story).

I am trying to understand where windows stops and (wubi) ubuntu starts......

I did a normal wubi install with the exe file, so at that stage it felt like I was putting stuff into a windows file (in my case fat32 file system). And I was running windows at that stage anyway.

After install, I am not apparently running windows when I choose ubuntu from the boot loader. And I am also not running windows after booting up.

I think I saw something in the user guide about initially a windows loader is used  (as normal for windows) then if wubi is chosen, a hand over is made to a wubi file? Is part of this process run by a wubi script? Presumably windows is not running(?)

However since I installed into a fat32 (ntfs for most other people) file system, am I running ubuntu on the fat 32 FS? In a virtual file or something?

I guess that I am not running windows in any way when I am in ubuntu (?) 

If I am using a web browser, email or other facility, in ubuntu now, will I be vulnerable to windows malware? Am I correct in thinking that since I am running ubuntu, then windows malware is not going to be any problem, similar to use of ubuntu after a conventional partition install?

Thanks for your patience

---

### Post by ago on 2008-01-23
> **candtalan said:**
> 
After install, I am not apparently running windows when I choose ubuntu from the boot loader.
That is NTLDR which is the windows bootloader not windows itself
If you choose "Ubuntu" NTLDR then passes the ball to grub4dos another bootloader which in turns starts Linux-Ubuntu. So windows is out of the loop.

The first time you run Ubuntu, there will be another stage of installation for about 10-30 minutes. The second time you can boot into Ubuntu normally.


> However since I installed into a fat32 (ntfs for most other people) file system, am running ubuntu on the fat 32 FS? In a virtual file or something?
Yes, think of wubi as a virtual hard disk, as opposed to a virtual machine. All is real except the hard disk.

> I guess that I am not running windows in any way when I am in ubuntu (?)
Yes

> If I am using a web browser, email or other facility, in ubuntu now, will I be vulnerable to windows malware?
If you are in windows yes. A windows virus has cannot execute under Ubuntu.

> Am I correct in thinking that since I am running ubuntu, then windows malware is not going to be any problem, similar to use of ubuntu after a conventional partition install?
Yes. But if you get a virus when you are in windows, such virus might wipe out the C: drive and wubi with it...

---

