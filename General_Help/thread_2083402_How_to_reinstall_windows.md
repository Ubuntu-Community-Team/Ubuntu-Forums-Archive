---
title: "How to reinstall windows?"
date: 2012-11-12
forum: General Help
---

### Post by PPamaterasu on 2012-11-12
Last night I took Linux Mint LiveCD that has Gparted included in it. Those where my actions:

- I chose the disk where Xubuntu was installed (698 GB). I selected ''resize'' and cutted it to the half.

On the other half, a grey block (unallocated) I chose ''new'', then create a NTFS primary partition

**I am doing something wrong or this is the right way?** I had to stop the operation because it was too late and the operation was going to lastmore than 4 hours. Thus I had school today. Still, I didn't wanted to left the laptop on with a CD inside. Afortunately nothing bad happened and the partitions are safe, not corrupted. My disk was reduced from 698 to 611 GB and there is an unallocated grey block with 30GB, but that can be fized

---

### Post by chuck_theobald on 2012-11-12
Sounds good, I use gparted to slice and dice disks as well. Have not had any problems.

Next, you will boot to your xubuntu partition to be sure all is well with it. Then, boot from the Windows install disc, be sure to select the correct (blank) partition. I think Windows will occupy your MBR, so you may need to go through your rescue disc to re-enable grub. In my experience, Ubuntu will recognize Windows and try to coexist. Not so much for the other way around.

---

### Post by oldfred on 2012-11-12
You need to have available a primary partition. 

Windows only installs to primary partitions (sda1 thru sda4) formatted NTFS with the boot flag or unallocated space where it can create that partition.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
 [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by PPamaterasu on 2012-11-12
Perfect. So I did well. But I should't have stopped the process, as it could ''cause severe damage'' the partitions and files. So I would never stop the actions again.

**Now...how do I recover the Grub after windows installation?**

---

### Post by chuck_theobald on 2012-11-12
The Ubuntu installation process will detect the existence of Windows and install an appropriate selection in grub.cfg. Not sure if grub can be made to do so with a Live disc, though.

Generally, since Windows wants to own your computer, it is best to install Windows first, then install other operating systems next. The latter are likely to permit Windows to coexist, whereas Windows does not want to coexist with other operating systems.

Perhaps a better way would be to use Windows as a Virtual Machine and have no worries about dual-boot or concern for having your MBR hijacked.

---

