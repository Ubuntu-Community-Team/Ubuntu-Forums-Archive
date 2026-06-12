---
title: "ISO for CD to boot USB hard drive"
date: 2016-04-27
forum: General Help
---

### Post by stepheny on 2016-04-27
I have recently installed Ubuntu 15.10 on a 480GB SSD on my Packard-Bell Easynote laptop. I have re-installed my old /home via backup and all my old packages via Synaptic so I have a pretty good replication of my old system. My old HDD was 1000GB with three main partitions, a small Windows partition (because it was paid for with the laptop!), an Ubuntu 64-bit 15.04 partition (380GB)  and a Ubuntu 14.10 32-bit partition (480GB).

Now that the Ubuntu 15.10 on the SSD is stable and working well I do not want to keep removing it and plugging in the old HDD to check things on my old working systems, so I have connected my old HDD to a SATA/USB cable and can read all of the partitions by plugging it in to a USB port. I would also like to be able to boot into the old system via USB so I altered the BIOS so that USB-HDD came above the SSD in the boot sequence. However, on boot, the HDD is ignored and the system boots straight into the Ubuntu 15.10 on the SSD.

I am not sure why the HDD doesn't boot, maybe the partitions are simply too big, but I thought that maybe the solution would be to write Grub script on a bootable CD that would allow any of the partions on the USB-HDD to be booted. Is this possible and if so how?

---

### Post by oldfred on 2016-04-27
UEFI or BIOS?
Have you tried in 15.10 with external plugged in (only works if all systems boot in same boot mode):
sudo update-grub

But HDD should boot from external if system allows it. Some UEFI/BIOS require you to turn on allow boot, even if it works for data.

 But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 


When I had my 60GB SSD, I had two / (root) partitions, main working and next working as test.
I now have 120GB and do not know what to do with all the space.
But all my data is in a separate /mnt/data partition that I can mount in every install. And as part of my rsync backup I export current list of installed apps, so I can restore quickly.

---

### Post by stepheny on 2016-04-27
It is BIOS, as I stated in the OP!

I don't want to make any changes to the existing SSD OS because that is working perfectly. What I want to do is to boot an old HDD via a CD or USB-stick. I don't see how posting lots of irrevelent reports would help, either you know how to do it or you don't.

---

### Post by oldfred on 2016-04-27
Then sudo update-grub will work.
And you should be able to directly boot from sdb drive with out issue.

But if something is mis-configured then need reports to tell.

If old BIOS, then there are some issues with boot files being beyond 137GB on drive. Often suggest smaller / (root) fully inside first 100GB with rest of drive as /home or data partition(s). Or a separate /boot partition which is a bit more complex to  configure.

---

### Post by stepheny on 2016-04-27
How would sudo upgrade-grub work? I think you should read my original post again.

---

### Post by oldfred on 2016-04-27
The sudo update-grub will find all your installs and let you boot them from your install on sda.

Did you try it?

---

### Post by stepheny on 2016-04-28
Firstly my apologies, you understood the problem perfectly well. I just didn't appreciate your answer. Sorry!

Secondly, sudo update-grub did find all partitions and wrote them into the Grub menu on boot. However when I select one ot the partitions on the USB drive(sdbx) instead of the sda drive I get the following warnings:

```
Error: No such device
Error: hd1 cannot get C/H/S values
Error: first load the kernel.
```

I cannot actually boot into the pertitions on the USB drive. Any ideas about what I am doing wrong?

---

### Post by oldfred on 2016-04-28
How old is BIOS? Is it set for AHCI, not RAID nor IDE.
But that may not be the issue, as similar issue seems to apply to USB boot. And then boot files have to be in first 100GB of drive. Again with Boot-Repair's report we could tell that.

Not sure if USB driver or some USB caddies?
We have seen older or cheaper USB caddy that does not work with large drives (over 2TB) or USB3 ports.

---

### Post by stepheny on 2016-04-28
Bios is approx 6 years old and is set for AHCI.

Here is Boot-Repair's report [http://paste.ubuntu.com/16092148/]("http://paste.ubuntu.com/16092148/")

---

### Post by stepheny on 2016-04-28
OK it's working now! I moved the USB-HDD below the SSD in the BIOS and used a USB2 port instead of a USB3 port.

Thanks for your patience.

---

