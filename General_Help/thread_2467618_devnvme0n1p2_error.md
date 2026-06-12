---
title: "dev/nvme0n1p2 error"
date: 2021-10-02
forum: General Help
---

### Post by suezdigger on 2021-10-02
Hello,

I've been running Ubuntu 20.04 on my wife's [HP 15S-FQ2044TU]("https://www.officeworks.com.au/shop/officeworks/p/hp-laptop-15s-fq2044tu-i5-8gb-256gb-notebook-hpfq2044tu") without an issue for the last 6 months.
About two weeks ago it returns the following error code and will not boot:

dev/nvme0n1p2: clean nnn/nnn files nnn/nnn blocks

Looking at various forums the issue seems to relate to nvidia and the common fix is to enter command line "sudo apt-get purge nvidia*" via terminal or TTY.
I'm unable to get access to terminal and TTY during the boot phase.

Booting from a USB disk I'm (occasionally) able to enter the grub start-up command line.

What has caused this error code and how can it be overcome?

I'm a novice to the (wonderful) world of Linux so an answer in layman terms would be very much appreciated.

Thank you,

Tristan

---

### Post by oldfred on 2021-10-02
The comment that drive is clean is normal & good.
It used to schedule fsck every 40 to 60 reboots, but now internal checks have mostly eliminated the need for automatic fsck.

Do you have system installed without UEFI Secure Boot, but an update to UEFI either by Windows or Linux fwupd then reset UEFI to defaults?
I would first check that all the UEFI settings you change are still correct. I keep a list as when I first built system, I had regular UEFI updates, not so many now that system is older.

If you have nVidia, you typically do not uninstall the nvidia driver. And if you do, you must totally purge it, as a new driver install may give conflicts. Drivers do not auto remove older versions.

What brand/model system?
What nVidia card/chip?

#What is installed
dkms status

---

### Post by suezdigger on 2021-10-04
Thanks so much for the response.

[I]Do you have system installed without UEFI Secure Boot, but an update to  UEFI either by Windows or Linux fwupd then reset UEFI to defaults?
I would first check that all the UEFI settings you change are still  correct. I keep a list as when I first built system, I had regular UEFI  updates, not so many now that system is older.[/I]

Looking through Bios Setup Utility I can't see reference to UEFI Secure Boot.  The only reference to UEFI is "UEFI HII Configuration" which doesn't appear to have any options.
For clarity I haven't changed any UEFI settings myself.  Any changes implemented would have been done via Linux updates (I don't have Windows installed).

*What brand/model system?*
[https://support.hp.com/au-en/document/c06987739](https://support.hp.com/au-en/document/c06987739)


*What nVidia card/chip?*
I'm not sure to be honest.  The link above nominates Intel® Iris® X&#7497; Graphics as Video Graphics.  I'm not sure if this is the card/ chip.
NVMe is nominated in the Bios configuration.


I'm not sure these are the answers you're looking for (sorry, I'm a novice) but I'd be happy to take any further instruction or suggestions.  Help is really appreciated.

---

### Post by oldfred on 2021-10-04
When you say you can sometimes get to grub menu, is that from internal drive's install or USB flash drive live installer?
If NVMe drive's install, can you boot second grub menu item or recovery mode?

I am surprised you said it has worked without issue for 6 months with 20.04.
We have seen many HP and others with the newest Intel chips have to use the very latest Ubuntu or 21.04. 
Now 20.04 does have available an update to a newer kernel and I would think that would work better.
But it depends on which 20.04 you installed. If 20.04 or 20.04.1, it does not get kernel updates automatically. Those stay stable. 
But then 20.04.2 and later versions update to newest kernel for support of newer hardware, since 20.04 will be supported for 5 years.

Intel offers updates to kernels & drivers for its new chips. But getting them into a kernel and then into a distribution often takes a while. 

Many with HP have needed UEFI updates and SSD firmware updates.

Systems are similar across various models, bigger difference if AMD or Intel based.
HP 17-BY4063CL Laptop shows UEFI screens, needed 21.04 since new Intel chip
[https://ubuntuforums.org/showthread.php?t=2462045](https://ubuntuforums.org/showthread.php?t=2462045)
HP 15 disable Optane
[https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483](https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483) & 
[https://askubuntu.com/questions/1331889/grub-bootloader-issue-with-dual-boot-dual-drive-install-windows-10-ubuntu-20-10](https://askubuntu.com/questions/1331889/grub-bootloader-issue-with-dual-boot-dual-drive-install-windows-10-ubuntu-20-10)
[https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane](https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane)

Update:
Just saw this, we normally do suggest the LTS versions as they have longer support. The interim versions only have 9 months of support, so you have to regularly update. The 21.10 version will be released later this month Oct, 2021.
[https://www.phoronix.com/scan.php?page=article&item=ubuntu-2110-tiger&num=1](https://www.phoronix.com/scan.php?page=article&item=ubuntu-2110-tiger&num=1)

---

