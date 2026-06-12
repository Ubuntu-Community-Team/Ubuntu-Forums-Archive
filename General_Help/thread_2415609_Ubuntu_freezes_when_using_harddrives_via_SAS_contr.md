---
title: "Ubuntu freezes when using harddrives via SAS controller card"
date: 2019-03-28
forum: General Help
---

### Post by matin80 on 2019-03-28
Dear Ubuntu community.
I have set up a workstation to process large amounts of satellite data, the files are between 5 and 10 gb each, and it is thousands of files. To manage this amount of data, I bought a controller card and use two 14 gb and two 12 gb drives which are put in the slots provided by the workstation. The drives show nicely up when I start my system and I can mount them without problem. I have set up a software RAID in Ubuntu (using mdadm) to have a raid0 with 52 tb. Everything works fine until I start copying files (5-10 gb each) to the raid0 drive, or also within the drive. It works for a while (very fast, up to 1 gb/s!). but then the system freezes and I have to hold the power button to restart the computer. I have tried many things:

- use different PCIe slots for the controller card,
- use different hard drives, also tried with a 6 tb drive only, without the above mentioned ones,
- flashed the controller to the newest firmware and to IT mode,
- don't use raid but the drive directly, 
- checked the drives for bad sectors, they are totally fine,
- checked the RAM, it is fine,
- monitored the drive temperature, there is no problem,
- remove the controller card.

Only the last option worked, but that's not what I want. When I start copying data via the controller, it is a matter of time until the system freezes. It may be related to the large size of the files, but it is all no problem if I use the internal SATA connections and not the controller card.

- The controller is a LSI 9211 8i, newest firmware, IT mode (newly bought),
- The mainboard a Supermicro X9SRA,
- I have 128 GB of DDR3 RAM ECC,
- The CPU is a Xeon E5 2667 V2,
- I also have a RTX 2080 ti,
- Ubuntu is 18.04 with all updates,
- as said, it happens with all drives of all size, so the harddrives do not matter.

It would be fantastic if someone has an idea what is going on, or had similar experiences to share with me..

many thanks!
Martin

---

### Post by matin80 on 2019-03-28
a short update: the system just froze without copying any data....I'm now confused on the reason for the system freeze. It may help to add that when I had removed the SAS controller it worked for 2 days, then I continued experimenting. On the other hand, yesterday it also worked for almost 20 hours with the card (but not using it). As just said, now it crashed without using the card (but it was connected).
I'm running out of ideas...

best wishes,
Martin

---

### Post by mörgæs on 2019-03-30
I don't know your particular SAS controller but the main rule is that the latest of hardware runs best with the latest of software. Have you tried 19.04 (beta)?

---

### Post by webaake on 2019-03-30
Also a newer kernel (it has newer drivers, generally) might be worth trying. Take a look at this Utility for installing kernels: [https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu](https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu)

I just installed kernel 5.0.5 on my 18.04.x system with Ukuu. The new kernel seems to work 100% on 18.04! This also has the benefit of not having to completely install/upgrade the hole system, just the kernel.

---

### Post by shag00 on 2019-03-30
You should check your kernel version, if it 4.15 then there is a known problem and you will need to install a newer version.

---

### Post by matin80 on 2019-03-30
it is indeed 4.15, I will update the Kernel and hope it helps, thanks!
Martin

---

