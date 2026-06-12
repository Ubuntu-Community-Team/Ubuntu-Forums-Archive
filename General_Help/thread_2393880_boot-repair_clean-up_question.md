---
title: "boot-repair clean-up question"
date: 2018-06-09
forum: General Help
---

### Post by aeronutt on 2018-06-09
I installed a second linux OS (fedora) for "testing" on a clean partition, all went ok. 
When I do this, I run boot-repair in my 'main' OS (Ubuntu 18.04) to get grub back to a boot that I know I won't screw up.

After running boot-repair, there seems to be a lot of fluff. See picture below.
- How do I get rid of this fluff?
- How do I prevent boot-repair from creating it?

FYI, it was odd that boot-repair thought I had an encrypted home directory somewhere, and asked if I wanted to continue or not. I continued, and everything boots ok.

[img]https://i.imgur.com/CKubims.jpg[/img]

---

### Post by Dennis N on 2018-06-09
If boot repair resulted in the extra EFI things in there, I would try booting to Ubuntu (which you apparently have as default) and just run **sudo update-grub**. See if they get left out of your menu this time.

---

### Post by oldfred on 2018-06-09
I know Boot-Repair adds a lot of .efi boot files as entries into 25_custom. But grub2's os-prober adds entries that it finds from other installs.
I typically turn off os-prober and add my own entries into 40_custom. When first learning I just backed up grub.cfg and copied the entries I wanted into 40_custom.

       Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries you want:
sudo -H gedit /etc/grub.d/40_custom
or
sudo nano -B /etc/grub.d/40_custom
Then do:
sudo update-grub 
    
Once you know your entries work, turn off all the os-prober entries by adding this line:
       sudo nano /etc/default/grub
GRUB_DISABLE_OS_PROBER=true 

More info:
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

---

### Post by Dennis N on 2018-06-09
I have Fedora 28, but it's own grub menu doesn't show any of those unwanted menu entry files. Neither are they in it's grub.cfg file (in the EFI system partition). So, seems like boot repair must be reading those .efi files directly from the EFI system partitions in order to creating those menu entries. If these all go into the 25_custom file in Ubuntu, why not just delete the 25_custom (or at least make it non-executable) and then run sudo update-grub? That should wipe the entries from the grub menu.

---

### Post by aeronutt on 2018-06-09
Good stuff folks, I'll play around with the ideas here and report back.
Thanks!!!!

---

### Post by aeronutt on 2018-06-10
> **Dennis N said:**
> I have Fedora 28, but it's own grub menu doesn't show any of those unwanted menu entry files. Neither are they in it's grub.cfg file (in the EFI system partition). So, seems like boot repair must be reading those .efi files directly from the EFI system partitions in order to creating those menu entries. If these all go into the 25_custom file in Ubuntu, why not just delete the 25_custom (or at least make it non-executable) and then run sudo update-grub? That should wipe the entries from the grub menu.

This worked, thanks. I'll play around with the other ideas too to see which fix I like better. 

Thanks again!!
 
Marked as solved.

---

