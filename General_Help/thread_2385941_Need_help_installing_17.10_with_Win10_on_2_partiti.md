---
title: "Need help installing 17.10 with Win10 on 2 partitions on NVMe"
date: 2018-02-27
forum: General Help
---

### Post by David4321 on 2018-02-27
System is ASUS ROG GL703VD, Intel Core i7 (7th Gen) 7700HQ, NVIDIA GeForce GTX 1050

I created an NTFS partition on half the NVMe (Samsung 960 EVO), and got Win 10 installed. The remaining space is still unallocated.

I can get 17.10 installer to run using 'nomodeset' option.

On 'Installation Type' screen, I had to select 'Erase disk' to check 'Use LVM', but the check persists with all options after that, but greyed out.

Here's where I'm stuck:

[ATTACH=CONFIG]278680[/ATTACH]

If I select 'Install alongside Windows 10' I get this:

[ATTACH=CONFIG]278681[/ATTACH]

Wrong option, I don't want it carving out a new partition inside the Windows partition, I want it to install to the unallocated space in the other half of the drive.

If I choose 'Erase disk', I'll lose Windows altogether.

When I choose 'something else', it looks like what I want.

I can choose 'free space' and add a partition.

This is how I set it. (Do I have to define a mount point? What to use?)

[ATTACH=CONFIG]278683[/ATTACH]

If I do that the ext4 partition is scheduled for formatting, and it appears to allow me to select that one for boot loader:

[ATTACH=CONFIG]278684[/ATTACH]

But 'Install Now' gets me this error. What's the problem?

[ATTACH=CONFIG]278685[/ATTACH]

What I want is Ubuntu installed on the back half of the NVMe drive using LVM, leaving Windows partition untouched.

Thanks for any help!

---

### Post by monkeybrain20122 on 2018-02-27
You have to choose a mount point for the root system (it is called "/" in the dropdown) But just be warned that dualbooting with Win10 is tricky to set up and maintained afterwards, there are a few threads where people cannot access Ubuntu anymore after some Windows update.

---

### Post by David4321 on 2018-02-27
Thanks, I'll try that. And I've heard there are issues with Win10. But it seemed a non-starter to go Win7 with a 7th generation chip & NVMe, which I would've preferred. Would you agree? Some seem to have done it, is it possible? And if not dual boot, would virtualizing be better in this case? Or what if the Ubuntu partition were on the data drive, and I just forced escape to startup menu, would that make any difference?

---

### Post by monkeybrain20122 on 2018-02-27
> **David4321 said:**
> Thanks, I'll try that. And I've heard there are issues with Win10. But it seemed a non-starter to go Win7 with a 7th generation chip & NVMe, which I would've preferred. Would you agree? Some seem to have done it, is it possible? And if not dual boot, would virtualizing be better in this case? Or what if the Ubuntu partition were on the data drive, and I just forced escape to startup menu, would that make any difference?

I would just wipe Windows and put it in VM. :)

---

### Post by David4321 on 2018-02-27
Update: when I got there it's telling me my partition tables will be changed on the whole NVMe drive, will that kill my Win10 installation?

[ATTACH=CONFIG]278689[/ATTACH]

---

### Post by monkeybrain20122 on 2018-02-27
Didn't you crave out the new ext4 partition from the nvme drive (you have only one drive)? so yes it will change The device (hard drive/ssd) is /dev/nvme0n1, the partitions are /dev/nvmeOn1p1 (ntfs) and /dev/nvmeOn1p2 (new ext4 partition) Sounds right to me.

---

### Post by David4321 on 2018-02-27
I'm used to gparted, but doing this on the new laptop, no Ubuntu there yet. I tried a few Windows tools, none of them could write an ext4 partition, so I figured the installer could do it. But I wasn't thinking about the tables. It says it's going to change the tables on the whole NVMe drive while writing partition to ext4, I guess from msdos/mbr to gpt. I was just asking if that will negatively affect my Win10 install or data on the other partition on that same drive when the table changes under it?

---

### Post by oldfred on 2018-02-27
Do you really want BIOS/MBR which is now a 35 year old configuration? UEFI/gpt is newer as Windows made it standard with release of Windows 8.
And best not to create Windows partition in advance as it wants multiple partitions.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

Also Windows 10 uses fast startup which is just hibernation. And on updates it will turn it back on. Grub only boots working Windows or Windows that is not hibernated nor needs chkdsk. So when fast start up is turned on, with UEFI you can still directly boot Windows from UEFI.
With BIOS you have to use your Windows repair flash drive or if installer has repair console to temporarily install a Windows boot loader to directly boot Windows. And then reinstall grub. Bit of a hassle.

All the LVM or LVM with encryption auto installs erase entire drive. LVM is intended to manage the entire hard drive as it is an alternative to the older MBR configuration and its 4 primary partition limit. Often used by those with servers, but if you want full drive encryption you need LVM. But running Windows on same drive as LVM means system still is at risk. Windows will not see LVM, but could erase entire drive.
 
I do not use nor know about LVM, but have some links.

 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[URL="https://wiki.archlinux.org/index.php/LVM"]https://wiki.archlinux.org/index.php/LVM
[/URL]
 Manually create
[http://community.linuxmint.com/tutorial/view/2061](http://community.linuxmint.com/tutorial/view/2061) 
        Full-system encryption with manual control and dual-booting Paddy Landau
[https://ubuntuforums.org/showthread.php?t=2357627](https://ubuntuforums.org/showthread.php?t=2357627) 
    
Update:
Just saw this thread where user is having issues with newer kernels, not yet resolved.
[https://ubuntuforums.org/showthread.php?t=2385932](https://ubuntuforums.org/showthread.php?t=2385932)

---

### Post by David4321 on 2018-02-27
Thanks very much for all that. I decided to go ahead with the install without LVM into the unallocated space alongside the Windows partition on the NVMe. Install appeared to complete, formatted to ext4, presumably updating table to GPT.

The good news: Windows still boots fine, no problems there. 

However: I can't see any way to boot into Ubuntu, so can't confirm the installation, or use it yet.
On ESC only 2 startup options, EVO drive, and 'enter setup' (bios).
EVO just boots to Windows. Inside bios, there are only 2 boot options, EVO and Windows Boot Loader. I have EVO set as first.

I don't want to reinstall Windows if that can be avoided. Everything I've read online recommends installing Ubuntu first for dualboot, because Windows destroys Grub on install, and Ubuntu leaves Windows boot loader alone. But you're not the second geek who's said install Ubuntu first, but the other friend said that was to get encryption with LVM. I don't use encryption, but I've always installed using LVM, because I like the idea I can do snapshots, and I thought it might be more complicated without, and I'd have to manually create partitions for swap etc. Apparently not (is that true?), as install appeared to complete fine. I avoided LVM as you suggested, this seemed safest, though I'm not sure it would have deleted Windows installing to a large unallocated area as I did, and not trying to put it in a pre-formatted partition. Fyi, after install I noticed that installer said it had succeeded and was complete, but clicking reboot did not succeed, it remained on the title screen after the dialogue went away, and I had to force quit. I think this may be because I was operating under nomodeset, that has happened before, but no problems with reboot after.

What next?

---

### Post by oldfred on 2018-02-27
Because you are using BIOS/MBR, you only have one MBR to control boot. Therefore last installed system is in MBR as is boot.
With UEFI, all installs share the ESP - efi system partition. But last install sets itself as first in boot order.
UEFI in effect is like having multiple MBRs to boot from.

Almost always better to install Windows first. But how you boot install media UEFI or BIOS is then how it installs for both Windows & Ubuntu.

If you installed Ubuntu in UEFI mode and converted to gpt, then Windows will not work.
Windows only boots in BIOS mode from MBR and only in UEFI mode from gpt.
You may be able to install Ubuntu in UEFI mode to a MBR drive, but not recommended.

With Ubuntu I do not use image backups, but use rsync to copy /home as backup. I also include in backup script list of installed apps and some system configuration info (more for info purposes). Then I can reinstall  and restore my data. But to each their own as there are many ways to backup.

With BIOS major Windows updates (all versions) totally erase Ubuntu if in logical partition. But it is just the partition table entry, so can be restored. But many posts on the issue back to Windows 7. And all the users dual booting and do upgrade have issue.

I really recommend UEFI install of both Windows & Ubuntu.

---

### Post by yancek on 2018-02-27
[QUOTEIf I do that the ext4 partition is scheduled for formatting, and it appears to allow me to select that one for boot loader:
][/QUOTE]

The above, from your initial post would explain why you can't boot Ubuntu.  If you're using MBR, you need to install Grub there or go through the convoluted process of creating an entry for Ubuntu with the windows BCD bootloader.

---

