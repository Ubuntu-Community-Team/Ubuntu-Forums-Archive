---
title: "Can't boot from USB or CD ..."
date: 2014-01-07
forum: General Help
---

### Post by Bucky Ball on 2014-01-07
Hi all,

Created Clonezilla boot USB using UNetbootin, Tuxboot and the default Startup Disk Creator app, created CD by burning an image to CD, but despite setting the BIOS to boot from optical drive or USB, which ever the case may be, neither boots.

I have booted the Clonezilla ISO as a virtual machine and it works faultlessly (I was thinking of doing the clone from there, but can't get the Guest Additions installed).

Any ideas? My machine just won't boot from the USB or CD. I have tried a different bootable CD and it won't boot from that, either. Never had any issues with booting from either before now ...

All ideas appreciated. TIA. ;)

---

### Post by Bucky Ball on 2014-01-07
Well, not a solution, but I'll mark it solved.

If I hit F12 at boot it takes me to a list of boot devices. If I choose USB from there (haven't tried CD but suspecting it will work), it works.

The original problem remains, though. No matter what boot device I set in the BIOS it is ignored and boot is from the hard drive.

---

