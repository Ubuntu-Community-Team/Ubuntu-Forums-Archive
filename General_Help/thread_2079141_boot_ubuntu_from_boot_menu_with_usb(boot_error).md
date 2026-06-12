---
title: "boot ubuntu from boot menu with usb(boot error)"
date: 2012-11-01
forum: General Help
---

### Post by blubl on 2012-11-01
(I'm using a Phenoix BIOS on a 32 bit dell inspiron 530)

well my os has failed im using windows vista on a dell inspiron 530 hdd,im trying to boot ubuntu from a usb stick but when i do it just tells me boot error??

my bios boot priority is set to removable then hard disk then cd rom



and my removable device priority is set too - USB-ZIP0 : Make of USB 1GB

can anyone please help,should i change my bios settings? or should i just try with a cd

btw is their any other way besides using ubuntu that i can retrieve my date from my hdd(windows vista) and safe mode is not an option as i cannot access that either

my computer knowledge is only ok(if anyone could explain it a little simpler) thanks this means alot

---

### Post by oldfred on 2012-11-01
My Desktop has a variety of USB boot options. And I tried everyone. I tested my USB flash drive on my laptop and it only had one option which worked. I assumed BIOS issues.  Then one day with flash drive plugged in I was testing booting from a different hard drive and there was USB flash drive.

If you have a one time boot key (f12 on my system) try booting from hard drive and see if flash drive is there. It does have to be configured correctly as a bootable device or it will not show.

---

### Post by efflandt on 2012-11-01
How did you put Ubuntu live/install iso on the USB stick?  Startup Disk Creator in Unbuntu usually works best for that as long as you put it on the FAT/FAT32 partition and do not try to format or use the entire device, instead of a partition.  Does it successfully boot on any other computer?

For Dell you often have to hit F12 at BIOS splash screen to select the boot device even if you put USB before hard drive in CMOS setup (unless your last successful boot was from that device).

---

