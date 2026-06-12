---
title: "boots to a grey screen and goes no further."
date: 2015-06-19
forum: General Help
---

### Post by ulao2 on 2015-06-19
After a unintentional power off my system no longer boots. If I press esc during boot I get a grub.I have a live dvd but only a CD drive (is there a cd iso anywhere?) ? I also have a cloned disk but it too boots to a grey screen. Neither boot seems to try any hd writes/reads. So I'm guessing its not an HS issue but have no idea what to try next.

I can boot to recovery but get this. I think I have a LVM partition, maybe that is why I see that?
** WARNING: There appears to be one or more degraded RAID devices **

The system may have suffered a hardware fault, such as a disk drive failure.  The root device may depend on the RAID devices being online. One or more of the following RAID devices are degraded:


edit: I just grabbed this [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
Never mind this is useless as it requires a network to the net to install, Downloading another CD iso I found.

---

### Post by ulao2 on 2015-06-19
I was able to boot to a live CD but my drive claims its a raid device, guessing it mans the LVM partition. Really could use some help here, can't anyone lend a thought?

I have a back up drive and its also dong the same thing. The grey screen is shown and the system is running ( not locked up) but no HS access. Maybe there is a question I can not see, hitting enter does not help.

---

### Post by ulao2 on 2015-06-19
Ok, I ran recovery from grub, then passed the warning with a 'y' then existed the recover and continues to boot and that works. So how can I fix the grub to boot correctly?

I tried to do a grub-install sda and I get I/O errors? If the disk is bad how did it boot. Still not sure what is going on here.

Update: Turns out I do not have LVM and instead have some type of soft raid that was set up. It was a raid 1 as both discs seem to boot from recovery but the grub can not boot from this set up anymore. When I install the grub I get IO errors so wherever the raid was installed now has bad sectors. I'll need to remove the soft raid and rebuild the grub on the drive that is ok. Don;t really know how to do that but I guess i'll try to figure it out.

---

