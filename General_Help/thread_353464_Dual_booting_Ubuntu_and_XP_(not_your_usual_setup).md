---
title: "Dual booting Ubuntu and XP (not your usual setup)"
date: 2007-02-04
forum: General Help
---

### Post by vixenk on 2007-02-04
If possible, could someone tell me how to do a dual boot of Ubuntu and XP under these conditions?

master hdd (HDA1) - I want to install XP and Grub to this hdd.
slave hdd (SDA 1, 2, & 3)- This is the hdd I have Ubuntu installed to.... split up into your usual root, home, and swap partitions. Making this hdd the master hdd is *not* an option as it is a sata and my motherboard is incapable of booting from sata.

I'm pretty sure that I'm not going to be able to pull this off with the Ubuntu live CD... so, can it be done with a different cd (like the Grub live cd)? And if so, how?

---

### Post by anaconda on 2007-02-04
It should work finely.
If you first install your windows where you want  it and then install ubuntu with a liveCD (or alternate if you prefer) ubuntu installer should automatically overwrite windows bootloader (on the first disk) and install grub in its place.

then the machine will boot to grub and there you can select where you want to boot.

The only possible problem you might have is that ubuntu installer wrongly assumes that SATA would be the hd that boots first. then ubuntu installer would install grub to your SATA disk, and you would be unable to boot ubuntu.. (windows would still boot normally.)

If this happens come back and ask how can you install grub to your IDE hd.. it is easy. just typing "grub install /dev/hda" or similar... on the command line...

---

### Post by vixenk on 2007-02-04
Well, there's an issue there...

To my understanding, this will only happen when Ubuntu is allowed to auto install to the remaining space. I'm worried about choosing this option though as I'm unsure as to how it will actually work with the remaining space. I don't want any Linux oriented partitions or files on hda, and I want my partitions on sda to stay intact and one of them in particular (my home partition) to *really* stay intact.

---

### Post by anaconda on 2007-02-05
Dont worry.. I have newer let ubuntu autoinstall.. I always do the manual partitioning etc.. and ubuntu installs grub automatically to the booting hd:s mbr.

With alternate install Cd it is also possible to specify where you want to install grub.if you want it to somewhere else than the booting hd:s mbr, but then ubuntu wont boot unless you add it to some other bootloader.. But in your case you DO want grub to your master hd:s mbr, so it will be installed there..

One point worth thinking is that if you haven't installed windows yet, then you might want to make a separate 200MB /boot partition to your windows disk. Then the 2.nd part of grub, which doesn't fit to mbr will be copied to that /boot partition.. It is better in that if you hose your ubuntu installation your windows would still boot normally using grub.. even if yur SATA hd isn't connected...

---

### Post by vixenk on 2007-02-05
> Dont worry.. I have newer let ubuntu autoinstall.. I always do the manual partitioning etc.. and ubuntu installs grub automatically to the booting hd:s mbr.
I tried that when I initially installed Ubuntu and it said it couldn't install Grub to an NTFS partition (which is the partition I had XP installed on). That's why I'm looking for a method besides the Ubuntu CD.

---

### Post by rsambuca on 2007-02-05
> **vixenk said:**
> I tried that when I initially installed Ubuntu and it said it couldn't install Grub to an NTFS partition (which is the partition I had XP installed on). That's why I'm looking for a method besides the Ubuntu CD.
Both the liveCD and the alternate CD will work perfectly for your needs.  I have used both and have XP on my IDE drive and ubuntu on a SATA drive.  I have re-installed both many times  as I change my mind on how I want to set things up, but currently have XP and Vista on the IDE drive, and ubuntu 32bit, ubuntu 64 bit, Sabayon and a separate kubuntu on the SATA drive.  The ubuntu CD's will happily install onto your SATA drive but put the Grub onto hd0, giving you a choice of which OS you want to boot.

---

