---
title: "couldn't install ubuntu on main desktop"
date: 2007-03-22
forum: General Help
---

### Post by pixeldotz on 2007-03-22
i have 6.10 edgy installed on my laptop and it runs great.

now i have a really big problem. i've been trying to install ubuntu on my desktop for awhile now and here's what happens. i boot off the disk and it takes a good 15 minutes before i get the START OR INSTALL UBUNTU screen.

after this it takes another 10-20 before i see any kind of activit. once the ubuntu screen comes up with everything being loaded (desktop, cd drive sound etc..) takes another 10 minutes before i have a complete desktop loaded.

so i though, maybe something happened. after loading the installer (5 minutes) i set the partitions i the way i want. i wait about an hr for 4 operations to complete and not even one gets completed.
gparted tasks where as follow. not the exact words but you experts know what i mean :)

resize to 15Gb
create ext3
resize to 512
create linux-swap

so after an hour of nothing (the animation on the progress bar was still looping) i decided to reboot back into xp. looking at the partition table told me that nothing was ever created.

can anyone shed some light on why my desktop was taking ages to even boot the livecd and then why so long for gparted to work and nothing happened? sadly, i wasn't able to install ubuntu on my desktop :(

specs.
2.24GHZ cpu
1GB ram
40GB hdd.
everything is intel based. looking around i got the livecd booted told me that everything got picked up for my pc out-of-the-box. audio, mic, usb.  only thing was that the acomdata external hdd didn't get picked up by my usb. that's another issue that can wait though.

any help is much appreciated.

---

### Post by Kateikyoushi on 2007-03-22
Boot from the cd at the menu press F6 then press E to edit the startupline and add add these options to the end of the line to see what might have went wrong delete quiet and splash.

noapic
nolapic
pci=irqroute
pci=noacpi
acpi=off
pci=acpi
linux irqpoll

If you get an error post it, you could also try the alternate CD.

---

