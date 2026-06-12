---
title: "Grub Error 18"
date: 2007-06-16
forum: General Help
---

### Post by mrbiggreg on 2007-06-16
I'm running xp pro on hd2 & Vista on hd3 both sata raid 160 gigs with vista boot loader at options prompt. I reformatted an 160 seagate and installed ubuntu on the drive which is on the IDE channel and adjusted bios to boot from HD0. In stead of scic. Grub loads then says error 18. What's up with this? I give it 160 by itself to run on. Tried it twice to no avail. Any one have a solution?:(:(

---

### Post by confused57 on 2007-06-16
Here are some possible solutions for grub error 18:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

---

### Post by Reugen on 2007-06-16
This is because the kernel isn't within the disk space recognized by the bios, therefore you need to move the kernel to a location on the disc that can be accessible by the bios. There is also a problem caused by some raid controllers and motherboards  of having part of the installation rewritten by the device. [http://www.markwilson.co.uk/blog/2006/03/grub-error-18-when-installing-suse-10.htm](http://www.markwilson.co.uk/blog/2006/03/grub-error-18-when-installing-suse-10.htm), [http://savannah.gnu.org/bugs/?2394](http://savannah.gnu.org/bugs/?2394). These aren't from the location being out of range of the motherboard, but it is feasable that it could also cause this error  asi it did in the first link (i think that would normally be error 21, not sure though).

here is a snippet from a gentoo forum about this error: 

"18 : Selected cylinder exceeds maximum supported by BIOS. This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).
http://forums.gentoo.org/viewtopic.php?t=122656"

with current motherboards its usually quite a bit bigger than 512 or 8 gb, i have a 300 gig hd i havent had problems with , but have had problems with an older computer with a 200 gig hard drive.  Seeing as how ubuntu is on the same hard drinve as the mbr and the only os on the drive i would say it is more likely that the kernel is being written over. You could always try rewriting grub with supergrub as confused57 suggests

---

