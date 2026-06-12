---
title: "SATA CD Burner doesn't appear"
date: 2007-10-22
forum: General Help
---

### Post by AEngineer on 2007-10-22
I tried to burn a CD for the first time in Ubuntu (7.10) and found that the burner doesn't appear although I can read data from CD's created independently with no difficulty.

I searched and found a recommendation to try "sudo modprobe ide_generic" - this didn't solve the problem, quite possibly because I thought I was being clever and purchased a CD burner with a SATA connection. It's:
DVD ROM LITE-ON|DH-16D2S-04 SATA %

My /etc/fstab entry reads
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

I also found a post that said they had to mount the CD manually so I tried
sudo mount /dev/scd0 
This produces a "No Medium found" message although there's a blank cD in the drive.

Any suggestions

10/29/2007 -
When I replaced the CD drive with an IDE drive all was well.  Clearly this is a linux/ubuntu problem with the hardware

---

