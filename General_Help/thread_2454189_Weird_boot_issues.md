---
title: "Weird boot issues"
date: 2020-11-24
forum: General Help
---

### Post by bytebro on 2020-11-24
Hi all,

I have a Dell laptop on which I have been running Ubuntu since 12.04 with no problems at all.  Currently it is on 20.04.  Everything has been fine until very recently (early November) I started to get weird boot problems, and I was wondering if this sounds like something which is 'known' or whether I might have a hardware problem!

Basically, I can 'suspend' and 'resume' and that works fine, and a 'restart' also works OK.  The problem is when doing a 'cold start' from a power-off condition I intermittently get a failed boot which leaves me with a non-functioning grub menu.  I have managed to find a work-around which may point toward whatever the problem might be: If I type 'c' to get a command line, I get the grub> prompt, and if I then type 'exit' it boots to some kind of hidden Microsoft thing that asks for a 'Live PIN'.  If I hit 'Restart' from *this* screen then everything boots properly and I'm back in Ubuntu!

If anyone wants me to provide more details I'd be happy to do so - just let me know what I should run to diagnose the problem.  Kind of as an aside, is there some relatively easy way to 're-write' all the boot info, in case this has somehow gotten corrupted?  I have tried 'sudo update-grub' which runs fine but makes no difference.

Thanks for any assistance!
Keith

---

### Post by oldfred on 2020-11-24
Since from older installs, is this a BIOS install, not UEFI?

The sudo update-grub just updates menu by scanning system for other installs. 
You have to do a full reinstall of grub to update grub in MBR (or ESP for UEFI).

Did you update BIOS/UEFI? If an update is still available you should update it.
It may be a setting in BIOS. Either an update or clicking on use defaults changes settings which you often then need to reset to run Linux correctly.
I have 7 or 8 settings on one system that I have to redo after every UEFI update. Some required &  some optional. With BIOS all settings were reset, but UEFI remembers some settings.

---

### Post by bytebro on 2020-11-25
Thanks for that, particularly the link to the "UEFI installing tips" post - very interesting.

I mis-spoke in my original message though.  I have been using Ubuntu since 12.04, but this is a relatively new laptop which was on a UEFI boot of 18.04 then got upgraded to 20.04.

I'm going to sit down one evening with that link you sent me and try and puzzle this out.  I think the first thing I need to be able to do is to 'refresh' the EFI boot info somehow.  If that make the problem go away then we're done!

Thanks again for the feedback.
Keith

---

### Post by oldfred on 2020-11-25
Vendor has a support site with UEFI updates.
If you have Windows that will often run updates also.
Note that UEFI updates reset some settings, I keep a list, one system needs a lot, the other just a few changes.

With old BIOS all settings were changed to default, but UEFI remembers boot & depending on system some settings.

[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist) & 
[https://fwupd.org/lvfs/devicelistSome](https://fwupd.org/lvfs/devicelistSome) new systems now will update from Linux.

---

