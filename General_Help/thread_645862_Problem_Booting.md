---
title: "Problem Booting"
date: 2007-12-20
forum: General Help
---

### Post by Silenus on 2007-12-20
I have brought up this issue before, and have found no help I use ubuntu/debian/windows on a computer with
1 gb ddr2 ram
ati radeon 9250 gfx card/intel 915 intergrated
2.93 Ghz Cpu
My problem is that when I try to boot any linux distro, except knoppix-std it gives me a kernel panic error, but it works fine with Windows on the ati radeon. To boot linux I must switch to onboard. This is the kernel panic error:
```
Kernel Panic - Not syncing: Fatal exception in interrupt
<1> BUG: Unable to handle kernel paging request at virtual address ffffd370 printing eip:
c0110ae2
*pde = 00004067
*pte = 1f116021
Ooops: 0003 [#38]
SMP
Modules linked in: Intel_agp agpgart evdev ext3 jbd mbcache sd_mod ide_cd cdrom ata_piix 9139too libdata usb_storage scsi_mod 8139cp mii generic piix ide_core elci_hcd uhci-hcd usbcore thermal processor fan
cpu: 0
EIP: 0060:[<c0110ae27>] Not tainted VLI
EFLAGS: 00010006 (2.6.18-5-686#1)
EIP is at clear_local_apic+0xc/0xt4
```

Help is appreciated.

---

### Post by logos34 on 2007-12-20
here are some links that might help or at least point you in the right direction:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/Radeon%209200/9250%20(RV280)%20and%20DVI](https://help.ubuntu.com/community/Radeon%209200/9250%20(RV280)%20and%20DVI)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Silenus. hmm...reminds me of the wisdom of Silenus (Nietzsche's Birth of tragedy)...

---

### Post by Silenus on 2007-12-20
That's where the name is from. lol.

---

### Post by logos34 on 2007-12-20
yeah, linux can be such a pain sometimes it makes you wish you'd never been born!

---

### Post by Silenus on 2007-12-22
I think I know a way to fix this now, a long time ago I used knoppix-std, I believe it has the 2.4.21 kernel, the only problem is I don't know how to find and compile it myself, as I have never done this. I know that knoppix-std worked with my system, and allowed the ati radeon card to boot, so if anyone can help me, it would be appreciated.

---

### Post by Silenus on 2007-12-22
linux-2.4.2.tar.bz2       linux-2.4.2.tar.gz       linux-2.4.2.tar.sign
linux-2.4.2.tar.bz2.sign  linux-2.4.2.tar.gz.sign
george@Picasso:~$ 

are the kernel files I have downloaded.

---

### Post by logos34 on 2007-12-22
maybe something on this page will help:
[https://help.ubuntu.com/community/Kernel/Compile?highlight=%28kernel%29](https://help.ubuntu.com/community/Kernel/Compile?highlight=%28kernel%29)

---

