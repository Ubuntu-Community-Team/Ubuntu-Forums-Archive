---
title: "Segmentation Fault error during boot"
date: 2007-08-05
forum: General Help
---

### Post by Nomad60 on 2007-08-05
I've seen other threads on this but so far, no answer. I'm using XP Pro, and have 2 IDE drives. Tried to install Ubuntu via the installer on my D: drive. After installation, I rebooted and saw the dual boot screen, and selected Ubuntu. I received this error as Ubuntu was trying to load :

17.942710 Segmentation fault

And that's as far as it gets. I'm stumped...

---

### Post by ago on 2007-08-06
It might be that your hardware is not compatible, try to boot the live CD and see if you have the same issue

---

### Post by Nomad60 on 2007-08-07
I booted with the live CD and it worked fine.

---

### Post by azagorath on 2007-08-08
iam also getting this error 
 buffer I/O error 
i think it got somthing to do with NTFS format or the partition has errors or its fragmented :guitar:

---

### Post by ago on 2007-08-08
Yep that is likely to be an ntfs issue. You may want to uninstall, defragment, run chkdisk, then try again possibly with smaller virtual disks.

---

### Post by Nomad60 on 2007-08-08
I'll try your suggestions and let you know.  BTW - I have 2 300 gig IDE drives in my system.  Disk 1 has 2 partitions - 40 gig for C:, the rest for D: and disk 2, E: has 1 partition.  When I try to install to E:, I get a different error...that menu.1st can't be found.  I thought that may be due to the size of the partition so I tried to install on D: and that's where I get the segmentation fault error.

**Update** - I tried the above suggestions (uninstalled, defragmented, ran chkdisk, smaller vitrual disk) and still the same problem.  For what it's worth, these are the last two lines:

[17.366001] EIP: [<f8871625>] sis_init_one+0x75/0x3c0 [pata_sis] SS:ESP 0068:df979e0c

[17.366132] Segmentation Fault

Blah!

---

### Post by Nomad60 on 2007-08-12
Ok, I give up.  I installed another hard drive (120 gig) and made 2 partitions, one of which was 25 gig for the Wubi install.  Still the same problem - segmentation fault.

---

### Post by Nomad60 on 2007-08-12
Well, I ended up doing it the hard way.  I deleted Wubi, downloaded the Live CD, and did a full install of Ubuntu as a dual boot with my XP.  As I type, I'm in Ubuntu (no problems at all, btw) and am downloading the updates.

---

