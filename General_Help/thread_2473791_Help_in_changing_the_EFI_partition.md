---
title: "Help in changing the EFI partition"
date: 2022-04-14
forum: General Help
---

### Post by bclofasz on 2022-04-14
I dualboot windows and linux. Ther's one linux, Ubuntu and there are two windows on my PC.
I installed windows to my HDD so it became the EFI partition. Then I got an SSD and installed another windows there while keeping the old one(mainly because I'm in the windows insider program, and I just wanted a stable windows if the other mess up.)

If I change my EFI partition will Grub and Linux brake?
Will I have to reinstall it?

I'm new here by the way. I installed Linux to learn how it works.
Turned out Discord has way better birtate on Linux than on Windows so if I have to explain something like programing to my classmates I use Linux.

---

### Post by yancek on 2022-04-14
If you have Ubuntu already installed and windows installed on separate drives, do you have a separate EFI partition on each drive for windows?
What are you planning to change on the EFI partition?  If you already have windows and Ubuntu installed on a single drive, your EFI partition should have a Microsoft and ubuntu folder containing their respective EFI boot files.

---

### Post by dragonfly41 on 2022-04-14
I do have internal HDD with Windows and shared Ubuntu (now obsolete so I don't use it).
Separately in an external USB3 docking bay I have Ubuntu (current) on SSD.
I have configured /boot/efi/EFI folders (inside each partition) so that each partition can be booted separately.
So for example if Windows HDD is disconnected I can still boot up Ubuntu. And vice versa.
The mechanism I use is rEFInd.
My main HDD (with shared Ubuntu .. but old and not now used) shows ..
/boot/efi/EFI/Boot
/boot/efi/EFI/dell
/boot/efi/EFI/Microsoft
/boot/efi/EFI/refind
/boot/efi/EFI/ubuntu

So at grub menu I can choose to boot with either standard boot .. or refind.

---

### Post by bclofasz on 2022-04-14
Replying to [COLOR=#000000][[COLOR=#000000]yancek[/COLOR]]("https://ubuntuforums.org/member.php?u=1928724") [/COLOR]
[COLOR=#000000][/COLOR][IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG]

No, there's only one EFI partition wich is on the (Old) HDD. Iam planning to change the EFI partition to my SSD's windows partition.

---

### Post by bclofasz on 2022-04-14
Replying to [COLOR=#000000][[COLOR=#000000]dragonfly41[/COLOR]]("https://ubuntuforums.org/member.php?u=1261878")[/COLOR]
[IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]

I don't understand 100%-ly how an EFI partition works, how to edit it etc, since Iam affraid to be honest that I will  brake any of the operating systems.(So I can' test it myself)

If you sure I won't brake any of them, then Iam up to any smart changes to the EFI partition and Grub.

---

### Post by dragonfly41 on 2022-04-14
This link might explain

[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)

Perhaps one safe way of installing rEFInd through your external drive (Ubuntu)
is to first install Synaptic Package Manager.
Then launch it and you see refind in Ubuntu repo.
This will install refind subfolder into /boot/efi/EFI folder.

First check the size of your EFI folder. Should be about 500 MB.

Or you can install manually following instructions at rodsbooks.

refind does not (should not) screw up your EFI setup. It is an addition not a replacement.  Optional.

But the usual advice is to keep a recovery backup .. in case .. in case.

That is another story to keep you busy.

---

### Post by bclofasz on 2022-04-14
Alright, thanks!:D

---

### Post by oldfred on 2022-04-14
Do you have an ESP - efi system partition on both drives, or just one?
You can have an ESP on each drive.

UEFI boots from UEFI boot entries, to ESP to more boot files in a system.
UEFI uses GUID or partUUID to know which ESP to find boot files.
The ESP then has folders with boot files for installed systems.

/boot/efi/EFI/Boot  - Typically has /EFI/Boot/Bootx64.efi as fallback boot entry. Often in UEFI shown as drive name/label.
/boot/efi/EFI/dell - probably efi boot files to use recovery partition to restore to as purchased
/boot/efi/EFI/Microsoft - will have Windows boot files, If two Windows, the BCD will have entries for both.
/boot/efi/EFI/refind - Another boot manager, often useful with difficult to boot systems or those who just like another menu
/boot/efi/EFI/ubuntu - has grub boot files & grub.cfg that refers(configfile) to full grub.cfg in your install.

Boot-Repair's report shows all the links and documents partitioning.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)  

You can see both GUID/partUUID and UUIDs.
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
This will show UEFI boot entries and which partUUID where it looks for boot files
sudo efibootmgr -v
And this will show grub.cfg on where it expects to find a full grub install/Ubuntu.
[FONT=monospace][COLOR=#000000]cat /boot/efi/EFI/ubuntu/grub.cfg
And grub menu entries, summary[/COLOR]
[/FONT]cat /boot/grub/grub.cfg  | grep menuentry

To know Windows entries you will have to look into BCD. 
I do not have Windows and Linux does not easily parse BCD.

---

### Post by bclofasz on 2022-04-14
Thanks for this detailed explanation 
As I wrote earlier that I only have one EFI partition wich is on the HDD and I want to move or copy it to the SSD where the newer windows located.(Because I can't update the never windows)

I just wanted to know if I move if it messes up Grub and Linux or not.
But as I read the other and this reply I think it won't mess it up.
I will try to do the moving/copying tomorrow.

---

