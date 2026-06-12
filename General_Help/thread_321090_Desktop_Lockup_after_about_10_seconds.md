---
title: "Desktop Lockup after about 10 seconds"
date: 2006-12-18
forum: General Help
---

### Post by beaker on 2006-12-18
Hi all,

I have a problem with my install of 6.06.  I posted a problem a few days ago, where by a Live CD or installation of 6.06 would cause a video problem with my nVidia GeForce FX 5200.  This was resolved with kind help from the forums, and was a configuration issue (which seems very common with nVidia kit).

Part of the original problem seemed to go away when I removed half of the RAM in my PC.  My PC is basically:

   AMD Althon 64 3400+
   WinFast KS8 755A-6LRS motherboard (3x DIMM slots)
   DLink DFE-530TX PCI NIC

Originally there was 1 x 512Mb DDR400Mhz PC3200 and 2 x 256Mb DDR400Mhz PC3200 DIMMs in there, but when I ran the Memtest application it started reporting lots of errors.  I systematically removed the memory and tried different combinations, and when I removed the two 256Mb DIMMs Ubuntu started fine and I could use it with no lockups at all.

I decided that, as I also run Windows XP in dual-boot, I needed more RAM so bought 2 x 1Gb DDR400Mhz PC3200 DIMMs (Kingston) and installed them.  Windows XP works no problems, even though the BIOS reports that the DIMMs are 333Mhz when I install more than one of them.

Ubuntu/GNOME starts up as normal, but when the logon appears I have about 10 seconds before the mouse and keyboard lockup totally and all I can do is a hardware reset.

Now, if I remove all the DIMMs and just put one of the new 1Gb DIMMs in, Ubuntu is fine.  If I put the 512Mb DIMM in it's fine.  Anything more than a gig and Ubuntu locks up in a very predictable manor.

Is there anything I can do to resolve this.  Please let me know what logs or information you need to help.

Thanks

---

