---
title: "Near unreadable blurry/pixelated screen after logging on my Poweredge 1750"
date: 2019-08-26
forum: General Help
---

### Post by ryan123452 on 2019-08-26
Hey All,

I'm trying to repurpose a Dell 1750. This is basically the specs: [https://www.dell.com/downloads/global/products/pedge/en/1750_specs.pdf](https://www.dell.com/downloads/global/products/pedge/en/1750_specs.pdf) except that it has 8GB of RAM.

After logging into Lubuntu, the screen is near unreadable. Any ideas on what the issue can be? I'm going to guess it's a driver issue but I have no idea how to proceed with this project.

Thank you in advance!

---

### Post by oldfred on 2019-08-26
It says on-board video, but what is it?

My desktop shows this:
```
fred@bionic-z97:~/Downloads$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)

```

---

### Post by ryan123452 on 2019-08-26
I'm pretty sure it uses this: [TABLE="width: 70%"]
[TR]
[TD="width: 50%"]ATI Rage XL PCI video controller; VGA connector
[/TD]
[/TR]
[TR]
[TD="width: 50%"]
I'm going to have to confirm it later. Also note that I upgraded the BIOS to A12. [/TD]
[/TR]
[/TABLE]

---

### Post by overdrank on 2019-08-26
> **ryan123452 said:**
> I'm pretty sure it uses this: ATI Rage XL PCI video controller; VGA connector

I'm going to have to confirm it later. Also note that I upgraded the BIOS to A12. 
Pretty old and under powered graphics card. Maybe update
You could also check cable connection and make sure card is seated. If it is a pci graphics card.

---

### Post by CatKiller on 2019-08-26
You haven't said what resolution you're trying to do: the maximum that card supports is 1600×1200.

---

### Post by oldfred on 2019-08-26
You may need to use 16.04 or update video card.

       The stock kernel of Ubuntu 17.04 and later  is doing away with Direct Rendering Manager (DRM) support for a number of ancient graphics processors. 3Dfx Banshee/Voodoo3+, ATI Rage 128, Matrox G200/G400, SIS, VIA, and Savage hardware
This was done because they expose insecure APIs to user-space.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276)
[https://www.phoronix.com/scan.php?page=news_item&px=ATI-RAGE-128-DDX-6.11.0](https://www.phoronix.com/scan.php?page=news_item&px=ATI-RAGE-128-DDX-6.11.0)

---

