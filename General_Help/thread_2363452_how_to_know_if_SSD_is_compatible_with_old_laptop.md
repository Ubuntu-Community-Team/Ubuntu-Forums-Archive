---
title: "how to know if SSD is compatible with old laptop?"
date: 2017-06-10
forum: General Help
---

### Post by ardouronerous on 2017-06-10
Dell Inspiron E1505

[LIST]
[/LIST]
    Intel Core 2 Duo Processor T7200 at 2.0 GHz per core.
    15.4&#8243; Ultrasharp WSXGA+ display with TrueLife
    1GB DDR2 667MHz RAM in dual channel mode
    ATI X1400 256MB graphics card
    120GB 5400RPM SATA Hard Drive
    8X DVD +/- dual layer recorder
    9-cell lithium-ion battery
    Microsoft Windows XP Media Center Edition
    Dell Wireless 1500 (802.11n)

We bought this laptop in 2007. Originally it had Windows XP Media Center Edition, but I recently installed Lubuntu 16.04 on it and it runs great, however, the hard drive has bad sectors.

The hard drive is limited only to 120 to 160 GB, a friend of mine came over and we tried to install a WD 500GB HDD on it, the BIOS wouldn't detect it, we even tried 320GB, no cigar, but it detected 160 and 120GB HDDs just fine.

With that, would Solid State Drives be compatible with this machine?

---

### Post by Dennis N on 2017-06-10
I have a Dell 1505N, also bought 2007. This was the model that came with pre-installed Ubuntu 7.04. I replaced the HD with a 250 GB SSD about 2 years ago and it is working fine with it.

The previous HD was a standard 5400 rpm SATA,  500 GB capacity.

---

### Post by ardouronerous on 2017-06-10
Well mine won't accept any HDD higher than 160GB.

---

### Post by Autodave on 2017-06-10
I am assuming that you had the jumper on the new HDs set correctly? Probably it would be "master" and the cd/dvd as "slave". Again, assuming that it is an older non-sata drive, it could also be set to "cable select". Best thing would be to check the jumper on the working drive and make sure that the new one is set the same way.

---

### Post by oldfred on 2017-06-10
XP often had drives set in BIOS to the old IDE.
If BIOS has AHCI then you need to change to that. And SSD will need that to support trim.

My old XP would not boot with AHCI on, and with XP you just about had to slipstream the AHCI driver into the system while installer and it was just about impossible to add later. Newer Windows let you add it or have AHCI driver.
So when I installed my first SSD I changed to AHCI. Then to boot XP I had to change to IDE. It was such a hassle that XP was soon retired.

---

### Post by efflandt on 2017-06-10
I would think that a laptop from that era would use SATA1. The newest laptop I have that used PATA (IDE) was a "very" low end Compaq (with 32-bit Sempron CPU) from 2005 which I got back when I got that person a newer laptop. When I originally used a Toshiba laptop from 2006 to install Ubuntu to an old 80 GB Intel SSD on SATA1, it was 4 times faster than that laptop's original 5400 RPM (which was no faster than external portable USB 2.0 drive). And when I moved that Intel 80 GB SSD to my desktop to my desktop, it was twice as fast on SATA2 than its 7200 RPM hard drive (8 times as fast as 5400 RPM hard drive on laptop). That laptop with dual core 1.66 GHz Celeron (slow Intel graphics) had no trouble booting 64-bit Ubuntu 16.04 on 512 MB mSATA SSD in SATA adapter and neither does a better dual core 1.66 GHz Dell Inspiron from 2007 (AMD X1300 graphics). Although both of those had been upgraded to 2.5 GB RAM.

So I don't know why your Dell laptop, apparently better than the old work laptop I have, would not be able to use SSD greater than 160 GB. But as a side note, my Dell XPS 8100 desktop PC from 2010 can boot fine from USB connected 160 GB drive, but grub cannot find its files if I attempt to boot it from a USB 500 GB drive that boots fine on those older Toshiba and Dell laptops, even though the desktop boots fine from its 1 TB internal drive or that 512 GB mSATA SSD in SATA adapter internally that I am running 16.10 from right now.```
~$ sudo fdisk -l
[sudo] password for efflandt: 
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x2fb1db22

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1               63     112454     112392  54.9M de Dell Utility
/dev/sda2           112455   24788294   24675840  11.8G  7 HPFS/NTFS/exFAT
/dev/sda3         24788295 1072880064 1048091770 499.8G  7 HPFS/NTFS/exFAT
/dev/sda4  *    1072880065 1953524596  880644532 419.9G 83 Linux


Disk /dev/sdb: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x7e78a7d3

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdb1  *     2048 1000214527 1000212480  477G 83 Linux
```Maybe it has something with "Sector size (logical/physical): 512 bytes / 4096 bytes", your BIOS being unable to cope with 4096 physical sector size (have you checked if there is a BIOS update for your laptop?)

---

### Post by ardouronerous on 2017-06-10
On updating the BIOS, I not sure I want to go down that route though, I've heard so many horror stories of people bricking their PCs and laptops when they try to flash their BIOS, so no, I don't want to risk it, I don't have the money to brick my laptop.

I've found this;  Kingston SSDNow V300 Series 2.5" 60GB SATA III MLC Internal Solid State Drive (SSD) SV300S37A/60G ([https://www.newegg.com/Product/Product.aspx?Item=9SIA6232GM5752](https://www.newegg.com/Product/Product.aspx?Item=9SIA6232GM5752))

Would this SSD be compatible with my laptop seeing that it's lower in GB than my original HDD which is 120GB?

---

### Post by QIII on 2017-06-10
Hello!

The level of detail you are getting in to now may be more on the level of a question to ask of the engineers who designed the board.  What you can get here is, at best, an anecdotal account or two -- hardly the sort of thing to go on if spending money is an issue.

I don't want to spend your money for you, but I think the least expensive route would be to find a used or "close-out" HDD of the right size and use that.  You won't get the performance of an SSD, but you will sure bypass the risks that worry you.

---

### Post by kurt18947 on 2017-06-10
> **QIII said:**
> Hello!

The level of detail you are getting in to now may be more on the level of a question to ask of the engineers who designed the board.  What you can get here is, at best, an anecdotal account or two -- hardly the sort of thing to go on if spending money is an issue.

I don't want to spend your money for you, but I think the least expensive route would be to find a used or "close-out" HDD of the right size and use that.  You won't get the performance of an SSD, but you will sure bypass the risks that worry you.

That may be the wiser course of action. I wonder if the ROI would be better getting a different conventional hard drive and upgrade the RAM from 1 GB to 2 GB or more. OTOH it's hard to find a new conventional hard drive for less than $45-$50 and there are plenty of 120 GB. SSDs for <$60. If the notebook has SATA1 it won't be able to take advantage of the SSD's throughput (the rest of the machine - processor, data bus may not be able to either) but for $10 - $15 more and from all reports SSDs are more reliable, especially in portables it's not a cut and dried decision.

---

### Post by gordintoronto on 2017-06-10
In my mind, the bigger question is, why can't you install a larger hard drive in this 11-year-old computer?

I popped a 60 GB Intel SSD into a nine-year-old Lenovov laptop with a Centrino processor, installed Mint Mate, and it flies!

---

### Post by ardouronerous on 2017-06-11
> **gordintoronto said:**
> In my mind, the bigger question is, why can't you install a larger hard drive in this 11-year-old computer?

I popped a 60 GB Intel SSD into a nine-year-old Lenovov laptop with a Centrino processor, installed Mint Mate, and it flies!

It's the BIOS, the BIOS on my laptop cannot handle larger drives, and updating the BIOS isn't really an option for me, because I might brick the laptop.

---

### Post by him610 on 2017-06-11
```
hard drive is limited only to 120 to 160 GB
...
would Solid State Drives be compatible with this machine?
```

If limitations are true, then SSD in capacity described would more than likely be compatible.

Price on SSD has come down greatly over last few years. You could always order an SSD (as low as $42), within your system limitations from Amazon, or other online seller to try. Oftentimes, one can obtain good serviceable components from Ebay.

 I have replaced all of my electro-mechanical boot drives with SSDs.

---

### Post by ardouronerous on 2017-06-11
> **him610 said:**
> ```
hard drive is limited only to 120 to 160 GB
...
would Solid State Drives be compatible with this machine?
```

If limitations are true, then SSD in capacity described would more than likely be compatible.

Price on SSD has come down greatly over last few years. You could always order an SSD (as low as $42), within your system limitations from Amazon, or other online seller to try. Oftentimes, one can obtain good serviceable components from Ebay.

 I have replaced all of my electro-mechanical boot drives with SSDs.

I found a Kingston 60GB SSD.

My question is, is there a difference between 120GB SSD and 120GB HDD? Is there a difference in capacity where the BIOS might reject it?

---

### Post by Dennis N on 2017-06-11
What BIOS version do you have? I looked at the BIOS on my Inspiron E1505 (model number shown on case above keyboard) and the BIOS is version A14 (4/2/2007). I have no apparent disk size limit.

One correction to my previous post #2: I checked my maintenance records, and the previous disk drive was 320 GB, not 500.

Even though these machines are I believe SATA 1, I found a large improvement in performance with an SSD. Well worth the modest investment.

---

### Post by ardouronerous on 2017-06-11
A08.
Like I said, I have zero experience in updating the BIOS, I'm afraid of bricking my laptop.

---

### Post by kurt18947 on 2017-06-17
> **ardouronerous said:**
> A08.
Like I said, I have zero experience in updating the BIOS, I'm afraid of bricking my laptop.

I think the risk of bricking a machine while updating the BIOS issued by the manufacturer is overstated but still real. There are 3rd party BIOSs (Thinkpads have them, perhaps others) that I would be more concerned about. Just make sure there's no power interruption; power interruption while writing will brick things unless there's a dual BIOS setup. I personally would have no reservation about installing a 120 GB. SATA drive for Operating System and some storage. There's enough capacity on a 120 GB SSD (likely 105 -110 GB. available) to dual boot with Windows if you need it. I find 30-40 GB plenty for an Ubuntu install, leaving 50-60 GB. for Windows. If you have large files such as HD videos, would external storage such as an external HDD be an option?

---

