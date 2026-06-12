---
title: "New install 12.04 and will only boot to Wiundoes 7"
date: 2013-08-15
forum: General Help
---

### Post by aviator1 on 2013-08-15
Hello Everyone:

I just got a new computer with Windows 7.  I downloaded 12.04 LTS (64B) last night and attempted a dual boot installation.

The process went well right up until the end, and the disk was kicked out due an error on the disk.

I downloaded a fresh one this morning, burned to a new disk and did a verification. All looked good.

I did an uneventful install, but now whenever I boot up, I do not get a menu to select 12.04. It only boots to windows.

I tried holding down the shift key with no luck.

I was able to get to 12.04 by using the install disk and a few selections at the first prompt, so it is installed and working.

Any help would be greatly appreciated.

Thanks,

Dave

---

### Post by carl4926 on 2013-08-15
Try installing again and make sure grub is set to sda
see this: [https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/5.png](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/5.png)

---

### Post by oldfred on 2013-08-15
Boot-Repair may fix it without the reinstall.

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

### Post by aviator1 on 2013-08-16
Thanks for the answers. I was out all of yesterday, and could not respond.

I did a reinstall, but did not uninstall first if that makes a difference.

I will give the boot loader repair a shot.

Thanks very much for the responses.

Dave

---

### Post by aviator1 on 2013-08-16
> **oldfred said:**
> Boot-Repair may fix it without the reinstall.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

I was able to use boot-repair and it fixed the problem..

Thanks very much for your help.

Regards,

Dave

---

