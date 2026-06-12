---
title: "Why is my installtion stalling when I install grub?"
date: 2005-10-26
forum: General Help
---

### Post by cesiel1990 on 2005-10-26
When I try to install Breezy I get to the grub install and it just stalls does anyone now why this is happening and if so how can I fix it.


Thx for the help

---

### Post by wallijonn on 2005-10-27
What type of mobo? Are you using PATA or SATA? Is it an AMD or Intel proc? IS WXP already on it? Did you change the boot priority to HDA upon the first reboot?

---

### Post by cesiel1990 on 2005-10-27
Im using a Biostar mobo with an Amd dual core 4400+, and yes it has WXP already on it. I have one SATA drive with windows on it and im trying to put breezy my second SATA drive. No I did not change the boot priority, but I dont need to do I with the SATA drives?

---

### Post by ember on 2005-10-27
I had a similar problem when I tried to boot from my PATA drive and my root partition ended on a cylinder over 100 GB. If you can, try creating a smaller root (boot should be suffiecient - but I didn't try) partition and one or maybe two others for the rest of the system.

HTH,
ember

---

### Post by cesiel1990 on 2005-10-27
Well I used the same hdd on my last system booting hoary.  What do you have for system specs ember?

---

### Post by ember on 2005-10-27
I didn't try hoary on it, but I've seen other people reporting problems in these forums too.

I have an Shuttle SN85G4v2, Nforce 3 Chipset, 160 GB Samsung Harddisk (Part. 1: Windows XP, 56 GB; Part. 2: 30 GB, Ubuntu Root-Partition; Part. 3 Ubuntu Home-Partition, 61 GB; Part. 4: Rest (~1,5 GB), Swap

I have deactivated the SATA adapter, so I have only the harddisk on primary IDE and my NEC DVD-writer on secondary IDE.

---

### Post by janwijbrand on 2005-11-12
[QUOTE=cesiel1990]When I try to install Breezy I get to the grub install and it just stalls does anyone now why this is happening and if so how can I fix it.

Thx for the help[/QUOTE]

I experienced exactly the same problem. It wasn't a complete hang BTW, I could still switch to a second console for example.

After some Googling I found a hint (somewhere on these forums :) about SATA settings in the BIOS. The hint suggested setting the SATA mode to 'enhanced'. 

That's what I did and the Grub boot loader did install. The remainder of the installation process finished just fine too and I had a perfectely running Breezy!

Some more details about my hardware: Shuttle SB61G2V4, Intel 865G, 1024MB RAM, 80GB Mactor SATA HDD. I found the specific setting called 'On-Chip Serial  ATA' in the 'Advanced Chipset Features' BIOS section.

---

