---
title: "I used to like ubuntu..."
date: 2006-11-19
forum: General Help
---

### Post by shame on 2006-11-19
I started using ubuntu with warty and went on to use hoary and then dapper when it was still in development.  About halfway through dapper dev things started to go wrong.  It was suddenly having trouble with my hardware that it had been fine with before and this continued through the rest of the dev period.
I tried installing dapper again from scratch when it went final but things were still the same.
Since then I've tried ubuntu a few times with similar results.
Well, having got a shiny new computer I thought I'd give it another go when edgy went final.
I tried the 64-bit version first and the only way I could get it to boot at all was to add acpi=off to the boot line and even then it still wouldn't boot if I left the splash line there so I had to do without a boot splash.  It did then install ok but I was still having tons of errors on boot so gave up.
I've now had another try, this time with the 32-bit version.
Again it refused to boot and acpi=off didn't do it.
Eventually I got it to boot after adding noapic.
It then went all the way to desktop and things seemed to be working ok so I went ahead and tried installing.
I got to the partitioning part and chose custom partitioning, it showed all my partitions correctly and I set up all my mount points and clicked next.  I then got an error saying there was no root filesystem.
There certainly was a root filesystem specified but it refused to accept there was.
I've rebooted and retried again 3 times with the same result, I've tried setting no mountpoints except root and swap but it then complains there is no mountpoint for such and such and still says no root filesystem.
The only way it will go past this stage is if I leave the root partition set as the one automatically chosen.  This isn't good enough as although the partition it chooses is empty, it is much smaller than I want for ubuntu and I intend using it for something else.
I also remember from every other version of ubuntu I've tried it always installs grub to mbr and I want it installing to partition.  Is this still the case?

AMD Athlon 64 X2
1GB Ram
1 SATA hard drive (which I'm trying to install ubuntu on).
1  ATA hard drive

I've tried disconnecting the second hard drive in case it was causing problems but that didn't help.

---

### Post by CatKiller on 2006-11-19
> **shame said:**
> I also remember from every other version of ubuntu I've tried it always installs grub to mbr and I want it installing to partition.  Is this still the case?

The (text-based) installer on the Alternate cd lets you choose where to put GRUB. As far as I know, none of the Desktop cds give you that option.

---

### Post by shame on 2006-11-20
The edgy desktop cd gives the option I just don't know if it will actually put it on mbr regardless.  I can't remember if any other versions did or not.
Does the partitioning bit work differently on the alternate cd?  Obviously there'll be no gparted but what about the bit where you select mountpoints since this is the current stumbling block.

---

### Post by CatKiller on 2006-11-20
> **shame said:**
> The edgy desktop cd gives the option I just don't know if it will actually put it on mbr regardless.  I can't remember if any other versions did or not.
Does the partitioning bit work differently on the alternate cd?  Obviously there'll be no gparted but what about the bit where you select mountpoints since this is the current stumbling block.

I've not used the alternate cd myself, or an Edgy one for that matter - the computer with Edgy got upgraded from Dapper.

[Here]("http://users.bigpond.net.au/hermanzone/") is a guide that you might find useful though.

---

