---
title: "UEFI vs. Legacy Boot Questions"
date: 2013-03-19
forum: General Help
---

### Post by cscj01 on 2013-03-19
I am building a new PC with a mobo that has UEFI support.  This is my first encounter with this, so I have a few questions.

[LIST=1]
[*]Are there advantages to UEFI as opposed to Legacy booting?
[*]If I run a 32 bit XP VM in Virtualbox within Ubuntu 12.04 64 bit, must I use Legacy boot?
[*]Is it difficult to convert to UEFI from Legacy if I have started with Legacy and my situation changes?
[*]
[/LIST]
Thanks for your help.

---

### Post by oldfred on 2013-03-19
I do not know if the VM will isolate XP from the gpt partitioning & UEFI?

XP does not know about gpt partitions and cannot read them. So XP does not work with UEFI.

New versions of Windows only boot from gpt partitioned drives with UEFI and UEFI requires gpt partitioning. 
Ubuntu will boot from gpt drives with either UEFI or BIOS.

So converting if dual booting is a big issue as you have to repartition, reformat to go from MBR(msdos) to gpt(GUID) partitioning. Best to plan ahead.

Only the 64 bit versions of Ubuntu work with UEFI.

I finally stopped my XP with my new SSD with gpt partitioning even though I still am in BIOS. To support trim on SSD, you have to have BIOS set to AHCI and XP does not have that driver unless installed during install. And I was not going to reinstall just for that.

XP is missing a lot of the support for new hardware features and you should think about updating to newer Windows if you really need Windows or retiring it. Its support from Microsoft also stops soon anyway.

---

### Post by 3Miro on 2013-03-19
1. UEFI allows for larger HDD and gpt partition table (which means you can have as many primary partitions as you want, no need for the old logical/extended drive).

2. Virtual Box should isolate XP from the hardware that you are using. A Virtual machine should run regardless of whether you are using UEFI.

3. I don't know. I got a UEFI motherboard, I moved half of my drives to gpt and I have had no issues with Ubuntu. I would say, just go with UEFI.

Note that the newest windows machines have locked UEFI, which means that you will very hard time installing Linux. If you can, try finding unlocked UEFI.

---

### Post by Kow on 2013-03-19
Go all-out UEFI. Save yourself the trouble down the line. UEFI will have no effect on VMs. I just finished updating my laptop with 12.04.2 from legacy to uefi - it takes time and will usually require shifting partitions around. Shifting partitions around = risk losing data.

---

### Post by cscj01 on 2013-03-20
Thanks to all who responded.  I plan to go with UEFI.

---

