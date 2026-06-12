---
title: "Ubuntu/Mate double boot UEFI problem?"
date: 2016-06-23
forum: General Help
---

### Post by giabaio2 on 2016-06-23
Hi all,
I have a weird one (well --- weird for me, at least!). So, my Dell XPS15 9550 has two hard drives. I've formatted them as follows:

```
Disk /dev/sda: 29.8 GiB, 32017047552 bytes, 62533296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 00249D0B-BE29-46EE-939C-60F6CC78063F


Device        Start      End  Sectors  Size Type
/dev/sda1      2048   976895   974848  476M EFI System
/dev/sda2    976896 59570175 58593280   28G Linux filesystem
/dev/sda3  59570176 62531583  2961408  1.4G Linux swap


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 4C97C1CF-77C8-4EAD-8249-5868B912E1A2


Device        Start        End    Sectors   Size Type
/dev/sdb2      2048   20801535   20799488   9.9G Linux filesystem
/dev/sdb3  59863040   63768575    3905536   1.9G Linux swap
/dev/sdb4  63768576 1953521663 1889753088 901.1G Linux filesystem
/dev/sdb5  20801536   59863039   39061504  18.6G Linux filesystem
```

So, sda2 is / for my main Ubuntu install and sdb2 is my /home for that. Also, I've installed Ubuntu mate on sdb2 and its /home on sdb5. I've also created an EFI partition on sda1, where I have installed the bootloader for both my OSs. OK --- I *think* I have one swap partition too many in sdb3 (is this correct?). I could remove it, but that's not the point (although any comments is more than welcome!).

At boot I get the grub screen which lets me select either of the two OSs. When I select my main Ubuntu (on sda2), everything works super OK --- no issues, boots perfectly and works well. When I try to boot Mate from sdb2, I invariably get an error message warning me that there's a "failure reading sector XXXX from hd1". This is also accompanied by a "alloc magic number is broken" message. When I go to the grub console and type ls, it appears that only hd0 (/sda) is recognised. I've read several things and tried to get my head around the EFI boot process (in case I was missing something obvious --- which I may as well!), but I couldn't come up with a decent answer to this...

The weird thing, though, is that if I try the same with a USB stick in the laptop (it doesn't have to be a USB stick with a live install. *Any* USB stick does the trick, at least in the tests I've made!), then all goes OK and I am able to boot both OSs. In fact, Mate works well, once I get past the error and manage to boot. I've checked the grub.cfg and it does match the UUIDs for the drives/partitions it's supposed to load depending on which entry is selected.

This is not a big deal for me, as I normally use my Ubuntu install for work and I only had Mate alongside it just because... (I have the space, wanted to see what it was like, was planning on having a few distros to play around, etc...). And I am able to boot Mate, if I really want to. But it's annoying --- especially as I feel that I may be missing something obvious (so when one of you guys just points it out, it'll make me feel stupid... :-) ).

Any ideas?

Thanks very much
Gianluca

---

### Post by ventrical on 2016-06-23
Hi,

```

sudo update-grub

```

?

:)

regards..

---

### Post by giabaio2 on 2016-06-23
Hi ventrical,
I've tried this a few times --- I thought this maybe the issue. But to no avail --- in fact, what's striking me is that I can't find anything wrong with the resulting grub.cfg file --- as I said, it does point to the right UUIDs!

Thanks
Gianluca

---

### Post by grahammechanical on 2016-06-23
> "failure reading sector XXXX from hd1"

My guess. That is a hardware error message. Load Disks utility from either OS and access the hard drive SMART Data.

On a separate point. It might be better to have an efi_boot partition on each hard drive and have the Ubuntu boot loader in the efi_boot partition of sda and the Ubuntu Mate boot loader in the efi_boot partition of sdb. Then if necessary you can use the UEFI setting utility to switch drives to load from. At the moment if something goes wrong with sda you may not be able to load Ubuntu Mate on sdb.

Regards.

---

### Post by giabaio2 on 2016-06-23
Thanks grahammechanical,
I will do that --- and point taken about the two separate EFI partitions. I have read a bit around, but am still a bit confused as to what is the best way of setting up the computer for dual boot with EFI... Also, may well have been my own inability, but I thought I read that Ubuntu may struggle to boot from anywhere else than sda?

In any case, could you explain in any way the fact that with a USB stick popped into the machine, then everything consistently works and I can boot the sdb OS?
Thanks
Gianluca

PS Not trying to be pedantic or annoying to people --- because this is not a big issue, as I said, I'm more genuinely interested in seeing what I may be missing here...

---

### Post by oldfred on 2016-06-23
Is sdb an external drive?
And then has it come up to full speed by the time you click on loading it?
New SSD are fast, but external drives often are slower starting, both due to lower power from USB port and being an HDD.

I often have a swap on every drive, but each new install auto adds all swaps to fstab. I just comment out extra swap. Not sure why I have extra swaps as now have enough RAM that swap is never used anyway with my normal work routine. Even when I only had 4GB I rarely used swap. But I learned not to open too much at once as old laptop with 1.5GB of RAM go real slow when using swap.

---

### Post by giabaio2 on 2016-06-23
Hi oldfred,
sdb is an internal drive (ie my laptop has two HDs).

G

---

### Post by giabaio2 on 2016-06-23
Is it possible there's a problem with my sdb? Basically, when I get the grub console with the USB stick in, the USB becomes hd0 (which it recognises with no problems), sda becomes hd1 (which again doesn't have any problem) and sdb becomes hd2 (which it complains about failing to read). But in this case, the instructions in grub.cfg tells grub to go to (hd1,gpt2). So grub goes to /sda2, complains that the UUID doesn't match (because effectively it's looking at /sda2 instead of /sdb2), but then ploughs on and boots after pressing any key...

I think that's what's going on --- but I'm not sure I can make much more sense of this...
Could this be a problem with the HD (eg not being connected properly, or something)? Strange thing is that *everything else* works fine with /sdb (eg the big /home partition for my main Ubuntu-/sda2 OS, or the /home partition for my Mate-/sdb2 OS and the /sdb2 root partition for Mate).

G

---

### Post by oldfred on 2016-06-23
I have had similar type issues with grub & loopmounting where I use device settings like hd1,3 in grub.
But grub is supposed to be using UUID and a search parameter to find UUID.

In my cases, I had skipped a SATA port on mother board on Desktop. My flash drive would be sde when plugged in but on reboot would be sdb. Second time (slower learner) I had DVD in between drives in SATA port order and similar issues. Drive was sdb, but hd2. 
Boot drive is always hd0. I always had to adjust my hdX settings to get my loopmounts to work.

---

### Post by giabaio2 on 2016-06-23
Thank you --- I'm a bit lost, though... Are you suggesting that I point to hd0 for all the OSs? (apologies if spectacularly stupid question!)...
G

---

### Post by giabaio2 on 2016-06-23
OK --- I think I maybe getting closer to solving this... If I edit the grub.cfg file and substitute hd0 for hd1 in the menuentry for Mate, then things do work, much as when the USB stick is plugged in. I do get a sort of warning about not finding the UUID for /sdb2, but then when I just press any key, things just work and I'm able to boot in Mate.

Thanks for your suggestions ---  I've also created a EFI partition on /sdb, just in case. I did notice too that a swap partition is created automatically for a new OS, but like oldfred I had commented that out in the relevant fstab.

I'm still not sure of what the rationale is (if I do sudo update-grub, then the original setting is written and Mate would search for hd1 and fail to boot...), but it'll do for today!

Any more comments, of course, more  than welcome!
Gianluca

---

### Post by oldfred on 2016-06-23
I just installed Yakkety (UEFI) to my sdb drive, specifically told it to install grub to sdb's ESP. 

And it overwrote my main working install's grub in sda's ESP. :(

I have a copy of my main working install's grub in /EFI/ubuntu and copy that back. Then update grub in main install and can boot normally or boot new install. The grub in the ESP is just a 3 line configfile for grub to find the full grub.cfg in the install.

---

