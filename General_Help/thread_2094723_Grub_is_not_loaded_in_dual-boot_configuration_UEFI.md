---
title: "Grub is not loaded in dual-boot configuration UEFI"
date: 2012-12-14
forum: General Help
---

### Post by bj44 on 2012-12-14
Hi,                                                                I installed Ubuntu 12.10 (EFI) on my ASUS laptop along side Windows 7 from a UEFI USB. Actually laptop came with  preinstalled Windows 7 (with EFI partition) and a partitions for recovery purposes which I  want to preserve. 
  
But when I restart the machine  - Windows 7 loads as normal, without any sign from grub. I can only boot to Ubuntu  by going to BIOS boot menu. No error whatsoever in either OS.

Any suggestions on how to get the grub menu back? Would Boot-Repair be an option here?

TIA

---

### Post by oldfred on 2012-12-14
If UEFI, you have to in UEFI menu set ubuntu as default to boot. Then from grub menu you can chain load back to the Windows efi boot. But grub has a bug and currently does not create a correct chain entry. Boot-Repair can fix that.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by bj44 on 2012-12-14
What do you mean by **UEFI menu set**? Are you referring to BIOS boot menu and selecting "ubuntu" there instead of "Windows Boot Manager"?

---

### Post by oldfred on 2012-12-14
Yes.

With UEFI it is not really a BIOS anymore, although most new UEFI systems have a fallback to BIOS mode.

So from UEFI/BIOS you should have a menu to boot both Windows & ubuntu. Then from Ubuntu you can also chain load back to the Windows entry without going back into UEFI menu to boot. So you can leave Ubuntu as default boot.

---

### Post by bj44 on 2012-12-14
Thank you,
Are there any instructions on how to chain load back to the Windows entry? May be a url that I can read, since I have no idea at this point. I guess it is all new to me...

---

### Post by oldfred on 2012-12-14
Grub's os-prober automatically creates entries, but they are the old style BIOS type which do not work with UEFI.

       Wrong style chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Any entry refering directly to a partition is the old style incorrect entry.
'Windows ...) (on /dev/sdXY)'

You can manually add a correct entry, I think bug report may have examples or just use Boot-Repair as it will update and add the correct entry.

Links to Boot-Repair posted above.

---

### Post by bj44 on 2012-12-14
Thank you oldfred,

I ran the Boot-Repair and that took care of this issue...

---

### Post by oldfred on 2012-12-14
Glad you got it working. :)

---

