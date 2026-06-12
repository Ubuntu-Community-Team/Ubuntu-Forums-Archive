---
title: "No choice of OS on boot. Dual booting W7 and Xubuntu"
date: 2013-04-05
forum: General Help
---

### Post by savi3000 on 2013-04-05
I've installed Xubuntu alongside Windows 7, but when booting, it just goes straight into Windows. Did GRUB just not install or something ?

If it matters, I'm using an ASUS K55VD Laptop.I *think*&#8203; it has UEFI, but I could be wrong.

---

### Post by savi3000 on 2013-04-05
Oops, wrong section. Can a mod move this please ?

---

### Post by oldfred on 2013-04-05
I think it is ok as General question. 

But if UEFI, did you install Xubuntu in UEFI or BIOS/CSM mode? Did you install with 64bit version?

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by savi3000 on 2013-04-05
Ok, so I asked in the IRC channel, and it was determined I do have UEFI enabled. I don't think I installed it in UEFI mode, but it never asked :/

Here's the output of bootrepair: [http://paste.ubuntu.com/5681014/](http://paste.ubuntu.com/5681014/)

What should I do?

---

### Post by oldfred on 2013-04-05
Did you install the 32 bit version. That does not have UEFI support.
> 

you have installed on sda6 a Linux version which is not EFI-compatible.

---

### Post by savi3000 on 2013-04-05
Ah yeah, I did, lol. I stupidly named the iso "xubuntu.iso" a while back and forgot what version it was !

Works fine, except now Windows 7 doesn't work. On boot, it has 2 ubuntu options, then Windows 7 loader and Windows 7 Recovery, and Windows 7 Loader says "invalid efi file" or something like that. :/

---

### Post by oldfred on 2013-04-05
grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)

---

### Post by savi3000 on 2013-04-06
Oh man, thanks !  Works fine now :)

---

