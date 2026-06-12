---
title: "&quot;Boot Repair&quot; question"
date: 2020-08-21
forum: General Help
---

### Post by jamesmck on 2020-08-21
I used Boot Repair in the past (from bootable USB stick on Win 7 or 10 machines) to fix several unbootable USB drives containing Ubuntu installations, and I believe that I was given a choice of which of the attached drives to  be the target of the repair (when there are multiple drives). Now, I do  not seen seem to get that option. I have tried re-scanning after inserting the USB drive, but everything seems the same as when the USB drive was not there.  What am I missing?[COLOR=#888888]

[/COLOR]

---

### Post by CelticWarrior on 2020-08-21
Machines *aren't *"Win 7 or 10", machines may come with Windows preinstalled but machines aren't Windows. I shouldn't need to be repeating [this]("https://ubuntuforums.org/showthread.php?t=2444952&p=13963488#post13963488") and [this]("https://ubuntuforums.org/showthread.php?t=2444952&p=13963529#post13963529").

BIOS or UEFI matters but what flavour of Windows there is in dual-boot or no OS at all is seldom relevant.

> [COLOR=#000000]I believe that I was given a choice of which of the attached drives to be the target of the repair (when there are multiple drives)[/COLOR]

I think you're confused, the default "correction" Boot Repair applies is installing Grub in all drives. But it may have some other possibilities in the advanced option. Don't know, almost never use it, everything Boot Repair does can be done manually with a few commands.

---

### Post by jamesmck on 2020-08-22
> **CelticWarrior said:**
> Machines *aren't *"Win 7 or 10", machines may come with Windows preinstalled but machines aren't Windows. I shouldn't need to be repeating [this]("https://ubuntuforums.org/showthread.php?t=2444952&p=13963488#post13963488") and [this]("https://ubuntuforums.org/showthread.php?t=2444952&p=13963529#post13963529").


Thank you for the unnecessary lecture.

---

### Post by oldfred on 2020-08-22
Boot-Repair's advanced mode.

[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by jamesmck on 2020-08-28
> **oldfred said:**
> Boot-Repair's advanced mode.

Bear with me while I clarify the reason for my question.  The reason I  was using Boot Repair (BR), and probably why I might continue to use it  in future, was to deal with Ubuntu installations on USB drives that  refused to boot properly. BR was on a bootable USB stick. I must have  used BR’s “Recommended” solution, since the USB drives responded  successfully.  Perhaps needlessly, I have since wondered about how  selectively BR is in choosing which drives to repair.  To be specific,  might the Linux or Windows installations on the hard disk drive of the  computer being used when booting the BR stick be compromised in any way  when using BR to repair a USB drive?  I think not, but want to be sure.

---

### Post by oldfred on 2020-08-28
Important to know if UEFI or BIOS.

Boot-Repair typically defaults to a grub re-install. But then grub settings may determine where, and if those settings are obsolete or incorrect grub may not repair correctly.

And with UEFI, you have to have system configured for UEFI boot with an ESP - efi system partition.
Ubuntu's Ubiquity installer works fine for one drive, but if you want grub installed to a second driver or external drive it fails miserably and has for years. Old bug report with now multiple work arounds. But Boot-Repair cannot reinstall grub to an external drive in UEFI boot mode unless you have an ESP - efi system partition. Boot-Repair does not create partitions.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive. 
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall to correct drive.

---

