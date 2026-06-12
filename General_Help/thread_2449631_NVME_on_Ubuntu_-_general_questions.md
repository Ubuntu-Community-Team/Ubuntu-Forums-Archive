---
title: "NVME on Ubuntu - general questions"
date: 2020-08-31
forum: General Help
---

### Post by dpastern2 on 2020-08-31
Hi Guys,

Looking at buying a Seagate firecuda 520 gen 4 pcie SSD and 2 x Samsung 970 Evo Plus SSDs - these will be simply used as cache data drives for a particular application (PixInsight).  

The o/s booting drive will be a Crucial BX500 256GB SSD - so that shouldn't have any issues.  

Some quick googling tells me that NVME PCI-e has been supported in the Linux kernel since v3.3.  Will these drives work out of the box after initial O/S install, or will I have to do additional things to get them working.  If the latter, what will I need to do?  

Motherboard will be a Gigabyte Aorus Master x570, which will have the BIOS updated to the latest version before O/S install.  

NVME drives may have older firmware installed upon purchasing, I'm really new to NVME and don't know much about the tech, so not sure if it's possible to update the firmware before having them in a working O/S install.  

Any advice and help appreciated.

Cheers,

Dave

---

### Post by oldfred on 2020-08-31
My Samsung NVMe had a ISO update file in the Samsung support site. It looked like an old DOS screen, was only for my model and only updated it to version it was as a download.
I believe the Windows app supports more, but the Linux version of the app in the commercial section never worked for updating my old SSD.

How to update Samsung:
[https://wiki.archlinux.org/index.php/Solid_state_drive](https://wiki.archlinux.org/index.php/Solid_state_drive)
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)

to see details (may have to install nvme):
sudo nvme list

---

### Post by TheFu on 2020-08-31
x570 is really new.  Almost still bleeding edge.
The Samsung 970 Evo Plus should be fine. Those are well supported.  

Nobody here will have exactly the same setup as you, so you'll need to research issues yourself.  I'd be most worried about the Gigabyte x570 support and carefully read the different storage connection limitations before buying anything.  There are some things about storage connections that I would never have thought about BEFORE I got a B450. My plans had to change completely due to the way the chipsets disabled and enabled only specific ports/slots.  Also, all the information wasn't in 1 place in the motherboard manual. It was in 3 different places, each with slightly different data. Read carefully.  You didn't mention a CPU, some of the storage capabilities are tied to specific CPUs.  **That x570 has only 2 NVMe m.2 slots.** How will you connect 3 m.2 NVMe storage devices?
[https://www.gigabyte.com/Motherboard/X570-AORUS-MASTER-rev-10/sp#sp](https://www.gigabyte.com/Motherboard/X570-AORUS-MASTER-rev-10/sp#sp)

Some of the x570 boards have some really new ethernet chips that a number of people here have had problems using.  Then there's the entire "Gigabyte doesn't support linux at all" problem.  Not supporting Linux only matters when it matters.  If it doesn't matter (everything works), then it doesn't matter.  For a cheap system, I don't have problems buying Gigabyte. For something where i'm spending over $200, I want all the components from vendors who DO support Linux - or at least try.

---

### Post by Yellow Pasque on 2020-08-31
> **TheFu said:**
>  **That x570 has only 2 NVMe m.2 slots.** How will you connect 3 m.2 NVMe storage devices?

Read it again. It has 3 M.2 slots (1 from the CPU, 2 from the chipset).

> carefully read the different storage connection limitations before buying anything.

The manual's table says the only limitation is that you lose 2 SATA ports if you use the bottom "M2_C" connector with a PCI-e SSD.  Happily, the X570 has more PCI-e lanes than B450, so there's less sharing and caveats.

---

### Post by QIII on 2020-08-31
> **TheFu said:**
> x570 is really new.  Almost still bleeding edge.

This may be an issue.  It takes a bit of time for the kernel to be ready to use the most up-to-date hardware.  You might want to see if [Phoronix]("phoronix.com") has any articles regarding your hardware.

I have three Samsung Evo 970 Plus devices on my board, the OS is installed on one of them, and I have no issues.

---

### Post by Yellow Pasque on 2020-08-31
It has dual LAN ports - a 2.5Gbe (Realtek RTG8125AG) and an Intel i211. The Intel LAN should work without issue. (I have the same thing on my mobo and it's pretty common.)
I have no idea about the Realtek chip.

---

### Post by Yellow Pasque on 2020-08-31
Something else to be aware of: [https://bugzilla.kernel.org/show_bug.cgi?id=205275](https://bugzilla.kernel.org/show_bug.cgi?id=205275)

---

### Post by TheFu on 2020-08-31
> **Yellow Pasque said:**
> Read it again. It has 3 M.2 slots (1 from the CPU, 2 from the chipset).

The manual's table says the only limitation is that you lose 2 SATA ports if you use the bottom "M2_C" connector with a PCI-e SSD.  Happily, the X570 has more PCI-e lanes than B450, so there's less sharing and caveats.

There are caveats about the 3rd m.2 working which may not apply to the OP. We don't know.  He should read and understand any limitations, unless you will buy the MB if it does not work for his needs. 

When it comes to hardware, I'm cautiously optimistic.  I hope for the best, but plan for the worst because I've been burned more than a few times, especially when in a hurry or trusting well-meaning online suggestions. After all, that's what we are here - well-meaning people, but we really don't have any skin in the choices to be made.  It isn't my $180.

---

### Post by Yellow Pasque on 2020-08-31
> **TheFu said:**
> There are caveats about the 3rd m.2 working which may not apply to the OP. We don't know. 

What are you talking about? I already read the manual and pointed out that caveat to the OP. So yes, I/we do know. Is there something specific you have an issue with or do you not trust the manual?

---

### Post by dpastern2 on 2020-09-01
> **TheFu said:**
> x570 is really new.  Almost still bleeding edge.
The Samsung 970 Evo Plus should be fine. Those are well supported.  

Nobody here will have exactly the same setup as you, so you'll need to research issues yourself.  I'd be most worried about the Gigabyte x570 support and carefully read the different storage connection limitations before buying anything.  There are some things about storage connections that I would never have thought about BEFORE I got a B450. My plans had to change completely due to the way the chipsets disabled and enabled only specific ports/slots.  Also, all the information wasn't in 1 place in the motherboard manual. It was in 3 different places, each with slightly different data. Read carefully.  You didn't mention a CPU, some of the storage capabilities are tied to specific CPUs.  **That x570 has only 2 NVMe m.2 slots.** How will you connect 3 m.2 NVMe storage devices?
[https://www.gigabyte.com/Motherboard/X570-AORUS-MASTER-rev-10/sp#sp](https://www.gigabyte.com/Motherboard/X570-AORUS-MASTER-rev-10/sp#sp)

Some of the x570 boards have some really new ethernet chips that a number of people here have had problems using.  Then there's the entire "Gigabyte doesn't support linux at all" problem.  Not supporting Linux only matters when it matters.  If it doesn't matter (everything works), then it doesn't matter.  For a cheap system, I don't have problems buying Gigabyte. For something where i'm spending over $200, I want all the components from vendors who DO support Linux - or at least try.

The board was released over a year ago...that is not bleeding edge or really new.  As others pointed out, the board I have bought has 3 m2 slots.  Slot 1 tied to CPU, slots 2 and 3 off the chipset.  You can use all 3 m2 slots, but using the 3rd will disable 2 of the SATA ports (not an issue, since I will only be using 3 other SATA devices and there are 4 slots left after using the 3rd m2 slot disables 2 SATA slots).  

I would not be using ethernet, but wireless and the wifi chipset should work OOTB with a modern kernel, at least given my research.  

I've used Linux on and off for a long time, probably before some of you were born - I'm long past making manufacturers support Linux  It's nice if they do, but going up in arms with them won't enamour them of the FSF community.  I bought the board for features and performance.  

I'll be using a AMD 9 Ryzen 3900x.  

> **oldfred said:**
> My Samsung NVMe had a ISO update file in the Samsung support site. It looked like an old DOS screen, was only for my model and only updated it to version it was as a download.
I believe the Windows app supports more, but the Linux version of the app in the commercial section never worked for updating my old SSD.

How to update Samsung:
[https://wiki.archlinux.org/index.php/Solid_state_drive](https://wiki.archlinux.org/index.php/Solid_state_drive)
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)

to see details (may have to install nvme):
sudo nvme list

Thanks - this machine wasn't intended to have Windows on it at all, and I'm not quite sure how I can update the firmware on Linux without Windows...none of my other computers support NVME PCIe M2 drives at all.  Let's hope the Linux version of Samsung's software works.  I will pose a support question to Seagate.  Sadly, it is unreasonable to expect major companies to support an operating system with =< .7% global user base.  

> **Yellow Pasque said:**
> Read it again. It has 3 M.2 slots (1 from the CPU, 2 from the chipset).



The manual's table says the only limitation is that you lose 2 SATA ports if you use the bottom "M2_C" connector with a PCI-e SSD.  Happily, the X570 has more PCI-e lanes than B450, so there's less sharing and caveats.

Correct.  Many people have demonstrated what happens when you plug in the 3rd m2 device (albeit using Windows).  Since this is driven by the motherboard's chipset/BIOS, the changes should be automatically provided to the O/S kernel.  That is if the kernel can interpret the device interrupts correctly...

> **Yellow Pasque said:**
> Something else to be aware of: [https://bugzilla.kernel.org/show_bug.cgi?id=205275](https://bugzilla.kernel.org/show_bug.cgi?id=205275)

An interesting read.  It seems audio should work, providing you run a kernel which has the patch, or patch the kernel with said patch.  I wasn't intending to be running Windows on said machine (as a dual boot), so there should be no funny business with Windows putting the hardware into light sleep etc.  I would expect that it should work, having read through the entire thread.  I kind of want audio to work, as I intended to listen to my music library when working on images in PixInsight.  If I can't get audio to work, it's a deal breaker for me and I guess I'll buy a Windows licence and go that route and lose 5% performance with PixInsight as a result.  

> **TheFu said:**
> There are caveats about the 3rd m.2 working which may not apply to the OP. We don't know.  He should read and understand any limitations, unless you will buy the MB if it does not work for his needs. 

When it comes to hardware, I'm cautiously optimistic.  I hope for the best, but plan for the worst because I've been burned more than a few times, especially when in a hurry or trusting well-meaning online suggestions. After all, that's what we are here - well-meaning people, but we really don't have any skin in the choices to be made.  It isn't my $180.

What caveats?  If you are referring to the 3rd m2 slot disabling 2 SATA ports, that is not an issue as I stated above ^^^

> **Yellow Pasque said:**
> What are you talking about? I already read the manual and pointed out that caveat to the OP. So yes, I/we do know. Is there something specific you have an issue with or do you not trust the manual?

I've also done my research regarding the m2 slots/SATA issues.  

I simply posted this thread because I have zero experience with NVME PCIe m2 drives (Linux or Windows or MacOS) and was curious as to what to expect given the normal speed of development that the Linux Kernel usually sees, especially with major hardware changes.  

I guess if I can't get it to work on Linux, I'll just bypass it and return to Windows land.  It's not a massive issue for me.  It'll be disappointing, but not the end of the world.  

Thanks for all the replies guys, much appreciated.

---

### Post by dpastern2 on 2020-09-01
Just an addendum, found this helpful askabuntu topic on Samsung's magician:

[https://askubuntu.com/questions/537471/samsung-magician-on-ubuntu-14-04#:~:text=Samsung%20(Disk)%20Magician%20is%20a,data%20and%20total%20bytes%20written](https://askubuntu.com/questions/537471/samsung-magician-on-ubuntu-14-04#:~:text=Samsung%20(Disk)%20Magician%20is%20a,data%20and%20total%20bytes%20written)

and Seagate seems to have Linux CLI and GUI versions of its software here:

[https://www.seagate.com/au/en/support/internal-hard-drives/ssd/firecuda-520-ssd/](https://www.seagate.com/au/en/support/internal-hard-drives/ssd/firecuda-520-ssd/)

Can't tell if any of it is good not.  Given that I'm new to NVME in Linux, and really haven't played with SSDs in Linux (trim, etc), I have some reading to do!

---

### Post by Yellow Pasque on 2020-09-01
> **dpastern2 said:**
> I simply posted this thread because I have zero experience with NVME PCIe m2 drives (Linux or Windows or MacOS) and was curious as to what to expect given the normal speed of development that the Linux Kernel usually sees, especially with major hardware changes.

*Shrug* I have NVMe drives, Sabrent Rocket and Intel 660p. They work just fine. I run trim once in a while. (IIRC, Ubuntu does this automatically as a cron job). But that's about it as far as difference from a normal drive.
For firmware, maybe Samsung and Seagate will dive in the fwupd pool one day instead of sticking their toes in the water: [https://fwupd.org/lvfs/vendors/](https://fwupd.org/lvfs/vendors/)

---

### Post by dpastern2 on 2020-09-02
> **Yellow Pasque said:**
> *Shrug* I have NVMe drives, Sabrent Rocket and Intel 660p. They work just fine. I run trim once in a while. (IIRC, Ubuntu does this automatically as a cron job). But that's about it as far as difference from a normal drive.
For firmware, maybe Samsung and Seagate will dive in the fwupd pool one day instead of sticking their toes in the water: [https://fwupd.org/lvfs/vendors/](https://fwupd.org/lvfs/vendors/)

I see no real reason why all NVME drives shouldn't work, but I've seen stranger things happen in my time...

---

### Post by mastablasta on 2020-09-02
i installed in june to nvme that came in laptop. so far so good.

---

### Post by dpastern2 on 2020-09-03
> **mastablasta said:**
> i installed in june to nvme that came in laptop. so far so good.

Awesome, which brand/model may I ask?  Did it work OOTB?

---

### Post by kurt18947 on 2020-09-05
I have an NVMe 512 GB branded HP, actually provided by MultiPointe Systems if memory serves. The firmware update utility is Windows only. It was plug 'n' play for me. I did lose access to one of 4 SATA ports due to shared PCIe lanes. Another thing to be aware of - M2 SSDs can be either NVMe or SATA. They're not interchangeable.

---

### Post by dpastern2 on 2020-09-05
> **kurt18947 said:**
> I have an NVMe 512 GB branded HP, actually provided by MultiPointe Systems if memory serves. The firmware update utility is Windows only. It was plug 'n' play for me. I did lose access to one of 4 SATA ports due to shared PCIe lanes. Another thing to be aware of - M2 SSDs can be either NVMe or SATA. They're not interchangeable.

yeah that caught me out initially - was simply thinking if it said m2 it was nvme.  Thankfully, taking my time and researching the subject properly allowed myself to realise this and I was able to select nvme pcie m2 slots.  It really hasn't been kept simple at all - pcie or sata.  m2, b2 or m2/b2 notches.

---

