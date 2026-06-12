---
title: "Dual Boot"
date: 2019-04-03
forum: General Help
---

### Post by kristofmate1 on 2019-04-03
Hi, there!

I have a Windows 10 laptop with Ubuntu installed, but Windows Update broke my Windows installation so I want now use Ubuntu as my primary OS. But it always asks me at boot if I want to start from Ubuntu or Windows Boot Manager. Is there a way to remove this prompt? 

kristofmate1

---

### Post by huff2 on 2019-04-03
If you have partitioned your hard drive to be able to run Ubuntu or Windows 10 then I imagine that you will always be prompted to run Windows or Ubuntu. I am not an expert on this but please check your boot order in bios to ensure that you are booting from the partitioned drive containing Ubuntu. Did I understand the question? Also, a screen shot of the issue would help me, maybe I can do some more research for you. Cheers!

---

### Post by deadflowr on 2019-04-03
Support thread so,
*Thread moved to **General Help***

---

### Post by oldfred on 2019-04-03
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Then we can make more specific suggestions.

Also be sure to backup Windows. We find many users who find they later have one application or game that only works in Windows & want to reinstall it. Or want to sell system and buyer only wants Windows.

---

### Post by kristofmate1 on 2019-04-04
I ran BootRepair and got a Pastebin URL. [http://paste.ubuntu.com/p/jCKWn2WmsH/](http://paste.ubuntu.com/p/jCKWn2WmsH/)
Maybe there is enough information in there.

---

### Post by oldfred on 2019-04-04
You can  delete the /EFI/Microsoft folder in sda1 which if not deleted, UEFI may add entries again. And grub uses this for its entries.

You then can delete the UEFI boot entries in EFI boot.

This shows the entries to make sure you delete the correct one. Report showed 0004 & 0007 as Windows.
       sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr 

Then rerun this to remove Windows entry in grub menu. It looks for the files in the your sda1, the ESP - efi system partition.
sudo update-grub

---

