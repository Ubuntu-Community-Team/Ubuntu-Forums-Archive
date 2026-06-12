---
title: "My SSD  (Samsung Evo 970 1TB) does not get recognized as a bootable device"
date: 2021-04-03
forum: General Help
---

### Post by mccoo8884 on 2021-04-03
Hello, I've made a bootable usb drive with Ubuntu and I went ahead and installed it. First I tried making my own partitions. Followed a tutorial and it went fine until after the installation. A splash screen comes up saying that I need to remove my bootable device (usb) to continue. I do that and ubuntu restarts only to tell me that I dont have any bootable devices. (Doesnt recognize Ubuntu on the ssd)

Same thing happens if I use the automatic installation (so not the something elsd option). When I plug my usb back in and press the try ubuntu button it starts up fine. And when I made my own petitions I could see them just fine.

What is going on here? Would appreciate help!

EDIT 4-4: Fixed the problem. If you happen to have a Z97x-3 Gaming motherboard, update your bios. I still had version F5. Newest is F8. Go to Gigabyte's website.

---

### Post by CelticWarrior on 2021-04-03
Welcome.

Are you sure you can "see" your 1TB SSD and that you're actually installing Ubuntu there? If so, and you have have an error message after rebooting that means your firmware, UEFI or BIOS, is misconfigured. Either it's installed in the wrong mode and/or incorrect boot order is selected.

---

### Post by mccoo8884 on 2021-04-03
I am sure. It shows 1 tb of space when I did the partitions myself and I took out my other drives. Yes that probably is the case but I have no idea what I should reconfigure it to to be honest. Any ideas? Ssd also doesnt show up in my boot devices in the bios. 

Thanks for the welcome

---

### Post by mccoo8884 on 2021-04-03
I am sure. It shows 1 tb of space when I did the partitions myself and I took out my other drives. Yes that probably is the case but I have no idea what I should reconfigure it to to be honest. Any ideas? Ssd also doesnt show up in my boot devices in the bios.

Thanks for the welcome

---

### Post by Quarkrad on 2021-04-03
If the ssd is not showing up in the bios I would sort that out before looking at ubuntu.  Irrespective of the OS you want to install, you need to make sure, at a basic level, your pc can 'see'  your HD/ssd. Perhaps do some google research on your ssd and motherboard/bios - once the motherboard/bios can see the ssd  you can then look at os (ubuntu) installation issues.

---

### Post by yancek on 2021-04-03
>  Hello, I've made a bootable usb drive with Ubuntu and I went ahead and installed it.

Did you download the Ubuntu iso file from the official Ubuntu site?
Did you then verify the download with and md5 checksum?
What software did you use to write the iso to the usb?  Did you do this on windows or on a LInux?

>   First I tried making my own partitions. Followed a tutorial 

Does that mean you tried to install using the manual method (Something Else)?  You forgot to post a link to whatever tutorial you used so there is no way for experienced users here to point out any errors/problems with it if any.

After the installation finishes and you are prompted to reboot, do you access the BIOS firmware and change the boot option to the SSD after removing the install usb?  

>  I am sure. It shows 1 tb of space when I did the partitions myself and I took out my other drives. 

Other drives?  What exactly was on these other drives?  Data only?  Some other OS?  Did you reattach them before trying to boot Ubuntu from the SSD?  If so, did you set the SSD to first boot priority?   There seems to be some confusion about your SSD in posts above, is the SSD seen in the BIOS but not seen as a bootable device?

When you installed Ubuntu to the SSD, did you boot and install UEFI or Legacy/CSM?

Might be a good idea to post the output of either/both commands below with all drives attached:

```
sudo fdisk -l
sudo parted -l
```

---

### Post by oldfred on 2021-04-03
UEFI or BIOS install?
How you boot install media, UEFI or BIOS is then how it installs.
And then default boot mode in UEFI/BIOS needs to be in that boot mode.
And some tools to create live installer, make only BIOS or only UEFI installers.

---

### Post by mccoo8884 on 2021-04-03
Yes, I used the official ISO. Didnt verify. Then I wrote it to a usb with rufus and I did that on windows 10. I used Ubuntu 20.04.2.0

Yes I used the manual mode of something else by following this: [https://youtu.be/_azMm3OLuhs](https://youtu.be/_azMm3OLuhs)

I did change the mbs value of the EFI to 512. Sorry I meant other partitions not drives. There is only only device in my pc after the installation completes and i restart and that is the SSD with ubuntu on it. How do I execute that command?

---

### Post by mccoo8884 on 2021-04-03
This is my bios: [https://youtu.be/nOu7k9wDwoo](https://youtu.be/nOu7k9wDwoo) in the panel bios features my boot option 1 is: UEFI: Kingston usb

And boot mode is put to UEFI only. It does not see my ssd. I am going to see if it sees it on windows.

---

### Post by oldfred on 2021-04-03
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mccoo8884 on 2021-04-03
> **oldfred said:**
> Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Ok, I've done that and here is the pastebin: [https://paste.ubuntu.com/p/mJDxNgXHFp/](https://paste.ubuntu.com/p/mJDxNgXHFp/)

I deleted my own partitions and just did the "Erase disk and install ubuntu" option before this so I knew I could not mess up the partitions or something.

---

### Post by oldfred on 2021-04-03
You show full install, but it is missing the entry in UEFI.
See line 55, you show only entries for flash drive.

Typically you have at least two entries, one for Ubuntu (or two) and one for drive which uses /EFI/Boot/bootx64.efi (which is not shown in your ESP, but may still be there?).

Do you have an UEFI setting security type setting that "locks" or prevents updates to UEFI entries. Some systems have some setting like that. If so change that first.

You can try this:
sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1

or run Boot-Repair's fix and the reinstall of grub should run command similar to above.

---

### Post by mccoo8884 on 2021-04-03
> **oldfred said:**
> You show full install, but it is missing the entry in UEFI.
See line 55, you show only entries for flash drive.

Typically you have at least two entries, one for Ubuntu (or two) and one for drive which uses /EFI/Boot/bootx64.efi (which is not shown in your ESP, but may still be there?).

Do you have an UEFI setting security type setting that "locks" or prevents updates to UEFI entries. Some systems have some setting like that. If so change that first.

You can try this:
sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1

or run Boot-Repair's fix and the reinstall of grub should run command similar to above.

I've run the auto-repair and restarted. It still did not boot. This is the new pastebin after the repair: [https://paste.ubuntu.com/p/J8bHNhBfhY/](https://paste.ubuntu.com/p/J8bHNhBfhY/)

It does show a new entry now. I am not sure about that whole UEFI setting stuff, I've never had to do something with that.

[https://www.youtube.com/watch?v=nOu7k9wDwoo](https://www.youtube.com/watch?v=nOu7k9wDwoo)

This video shows the bios that I use. I appreciate all your help thus far.

---

### Post by oldfred on 2021-04-03
It says no errors on install.
And update showed an Ubuntu entry.

You can also see it with:
sudo efibootmgr -v

Your video shows a lot about of overclocking, not recommended.
But if you have not updated UEFI to latest available, you should, but there probably are not any real recent updates, if old motherboard. But since you have NVMe drive, I think motherboard is newer than that mentioned in video (z77).
If you do not have manual, download it from Gigabyte, so you can see about details.

Have you updated SSD firmware? 
For my Samsung, I had to download a bootable ISO. It looked like an old BIOS boot with one option to update just my model SSD.

How to update Samsung:
[https://wiki.archlinux.org/index.php/Solid_state_drive](https://wiki.archlinux.org/index.php/Solid_state_drive)
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)

---

### Post by mccoo8884 on 2021-04-03
> **oldfred said:**
> It says no errors on install.
And update showed an Ubuntu entry.

You can also see it with:
sudo efibootmgr -v

Your video shows a lot about of overclocking, not recommended.
But if you have not updated UEFI to latest available, you should, but there probably are not any real recent updates, if old motherboard. But since you have NVMe drive, I think motherboard is newer than that mentioned in video (z77).
If you do not have manual, download it from Gigabyte, so you can see about details.

Have you updated SSD firmware? 
For my Samsung, I had to download a bootable ISO. It looked like an old BIOS boot with one option to update just my model SSD.

How to update Samsung:
[https://wiki.archlinux.org/index.php/Solid_state_drive](https://wiki.archlinux.org/index.php/Solid_state_drive)
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)

I have a z97 gaming 3 motherboard. I'll try and see if there are updates available for both motherboard and SSD. Could it be that currently my motherboard physically supports the M.2. ssd but it does not recognize the software?

---

### Post by oldfred on 2021-04-03
That may be an UEFI update.
Back with z97, M.2 was pretty new. I do not remember if my z97 system supported NVMe or not.
But system shows your NVMe drive, so should be ok. There may be a setting in UEFI required on the drive settings page?

---

### Post by mccoo8884 on 2021-04-03
> **oldfred said:**
> That may be an UEFI update.
Back with z97, M.2 was pretty new. I do not remember if my z97 system supported NVMe or not.
But system shows your NVMe drive, so should be ok. There may be a setting in UEFI required on the drive settings page?

"There may be a setting in UEFI required on the drive settings page?"

I'm sorry, what drive settings page exactly? I have the feeling that the M97 does support M.2 but that it is very iffy to get working correctly. I am going to use the Samsung Magician tool to mess around with the firmware.

I've also found this post:

**On a Z97 board you must install a BIOS update to boot from a naked M.2  NVMe drive (one without a boot ROM). Your system must also be configured  for pure UEFI booting, CSM must be disabled and consequently your drive  must be partitioned with a GPT type partition table (not MBR) and have a  UEFI Windows installation.**

Well, I'm already sure that it's MBR. This is for windows but it might be what's causing my issues with Ubuntu? I also know that my bios is currently set on both legacy and UEFI so I will limit it to UEFI only. I kind of just want to buy a new motherboard that's a weak mentality.

---

### Post by mccoo8884 on 2021-04-04
> **oldfred said:**
> That may be an UEFI update.
Back with z97, M.2 was pretty new. I do not remember if my z97 system supported NVMe or not.
But system shows your NVMe drive, so should be ok. There may be a setting in UEFI required on the drive settings page?

Fixed it, finally! Downloaded the F8 Bios update for my z97 and it booted. Now time to set up my partitions properly.

Thanks for the help everyone.

---

### Post by oldfred on 2021-04-04
Please change to solved.
Also would not hurt to change title to include Z97 & NVMe at start of Title. (by edit of first post).

---

