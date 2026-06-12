---
title: "[CLOSED] Broken UEFI boot after partition cleanup"
date: 2014-09-03
forum: General Help
---

### Post by gdupont on 2014-09-03
Hi,
I'm stuck with a broken boot since I tried to cleanup the partitions on my disk. I own a Lenovo yoga 2 laptop which is bundled with win8 and a dirty initial partition. After deciding to delete win8 and cleanup the partitions, I accidentally removed the UEFI partition that was used to boot. Tried to fix following different posts online (I'm trying to relocate them) without succes so far.

As far as I understand, I don't need UEFI anymore since I want single boot but I cannot fix that. So I tired to recreate the boot partition Boot-repair was not able to fix it and its latest report is here:
[http://paste.ubuntu.com/8222439/]("http://paste.ubuntu.com/8222439/")

Anyone see how to fix this?

gd

---

### Post by slickymaster on 2014-09-03
*Moved to the ***General Help*** sub-forum.*

---

### Post by moore.bryan on 2014-09-03
If you use [this]("https://help.ubuntu.com/community/UEFI") guide a walkthrough--although, perhaps you already have--you should be able to get it install, *then* run boot-repair from a livecd.  If you've already tried those steps, could you be a bit more specific with your partition table/other details?

---

### Post by yancek on 2014-09-03
You have Grub code in the mbr and it looks for the core.img file at a specific location and it is not there.  It is generally located in /boot/grub and in your case that would be on partition sda8.  You won't be able to boot without it.  You still have the EFI partition (sda2) but none of the necessary files are in it.  Try the suggestion at the link above and post the results

---

### Post by gdupont on 2014-09-04
Hi guys and thanks for the response.

I did follow the tutorial you linked, but I'm stuck on the creation of the EFI partition. Well, it did create with correct flag and all, then mounted to /boot/efi. But Boot-repair does not detect it and still say I have to create it... Did I miss anything?

To confirm, ubuntu is installed in EFI mode. It's really the EFI partition that I need to restore. Boot-repair is telling me that my system is in GPT mode and I starting to wonder if that is not in conflict with EFI... And of course, I did not re-install ubuntu (yet) since I'm trying to fix my current installation. Worst case, I'll do this.

BTW, any chance to get back the pictures that are in the tutorial? (broken links)

---

### Post by gdupont on 2014-09-04
Finally resolved to re-install. But as soon as I got more time, I'll definitly need to get around this UEFI/GPT/grub issue.

Thx anyway

---

### Post by moore.bryan on 2014-09-04
Hmm... never noticed the broken pics; I don't know if there floating in the webs or not.

---

