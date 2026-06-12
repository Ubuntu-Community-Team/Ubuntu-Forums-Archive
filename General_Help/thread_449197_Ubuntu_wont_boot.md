---
title: "Ubuntu wont boot"
date: 2007-05-20
forum: General Help
---

### Post by himynameis on 2007-05-20
I turned on my new PC, booted up from a mail ordered-CD and installed Dapper Drake 6.06 onto my hard drive. My PC then turns on and this appears on the screen:

verifying DMI pool data.......
Boot from CD:
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

my BIOS is set to boot my hard drive first, then my floppy drive, then my cd drive. It will not boot from my hard drive. I'm stumped, I checked to see if the hard drive was correctly connected to the motherboard and I checked the BIOS to make sure it boots from my hard drive. Any help would be much appreciated.

---

### Post by vtel57 on 2007-05-20
Your installation did not install properly. Looks like no boot loader was written onto the hard disk master boot record. Your BIOS doesn't see anything there to boot to.

---

