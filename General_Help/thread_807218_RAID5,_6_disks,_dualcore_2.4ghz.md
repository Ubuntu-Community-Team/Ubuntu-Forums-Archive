---
title: "RAID5, 6 disks, dualcore 2.4ghz"
date: 2008-05-25
forum: General Help
---

### Post by Der_Idiot on 2008-05-25
I'm looking to software raid5 using the following:

ubuntu server 8.04
athlon 64 3800+x2
DFI SLI-DR motherboard
1x 250gb for /
6x 250gb for /media/data  (IDE for the moment, will swap these for 1tb sataii drives eventually)

What kind of write speeds can I expect using this setup (system will be almost completely dormant for cpu/ram use). Really, I just want it to be over the standard 100mbit throughput for write, read of course will be massive. This is for home experimentation, as well as real-world use for my home network.

I will be using [this page]("http://bfish.xaedalus.net/?p=188") as a guide to getting it setup, but the part with gparted is a problem -- this box is headless and has no gui installed. Is there a method to flag a partition as a raid-partition? Also, how does mdadm tell me I have a failed drive? :confused:

Edit- Do I  need to enable CONFIG_MD_RAID5_RESHAPE=y in the kernel before I can grow the raid? Or is that enabled in the latest kernel builds? :o

---

### Post by Der_Idiot on 2008-05-25
Looks like after looking at my kernel configuration, the raid5 growth command is already set to yes. :D

---

### Post by Der_Idiot on 2008-05-28
... no response? Come on guys! :(

---

### Post by fjgaude on 2008-05-28
I think your DFI motherboard uses PCI-E to drive the SATA controller for your drives. The sequential read speed of a 6-drive raid5 array will be about five times what one drive would be. If your drives are late model ones with a thourhgput of about 50MB/sec then you will see 250MB/sec, that's bytes/second. If first generation perpendicular ones then it'll be 350MB/sec. The write speed will be just a little less.

The motherboard PCI-E is likely X1 and that taps out at 500MB/sec. If you are using 2nd generation perpandicular drives then you will over run the bus, as each of these drives is good for 100MB/sec throughput.

Uses parted to create your partitions in your server, headless. If you use mdadm you might not even need to have the drives set for "raid". I didn't once or twice and all worked out just fine.

Good luck!

---

