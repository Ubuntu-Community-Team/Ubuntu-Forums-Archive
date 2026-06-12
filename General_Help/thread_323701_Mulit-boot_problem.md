---
title: "Mulit-boot problem"
date: 2006-12-22
forum: General Help
---

### Post by pleriche on 2006-12-22
Hi -

I have 3 hard disks containing WinXP (hda), Win98 (hdb - for the kids to play games) and Linux (hdc - for me to experiment). I've been using mrbooter successfully for a while as a boot manager, which worked in the past with an old RedHat.

I installed Ubuntu Desktop from the live CD, and was disappointed that it overwrote mrbooter (with GRUB?) without so much as a by-your-leave. This actually worked, and booted all 3 systems, but I wanted mrbooter back, as it's slicker.

I reinstalled mrbooter, but ubuntu doesn't boot. I presumably need to restore a bootloader on the MBR of hdc, tho' I do seem to have a broken LILO, judging by the "LI" which comes up on the screen.

Can someone give me a quick pointer in the right direction please?

Regards - Philip

---

### Post by dbbolton on 2006-12-22
what do you have set as the location of the kernel, init file and partition in mrbooter  ?

---

### Post by steve.horsley on 2006-12-22
The "alternate" installer CD has a rescue mode that can drop you into a root command prompt on hdc. From here issue the command 
**grub-install /dev/hdc**
which will install grub on the hdc partition. Now you can chainload this partition in the same way as you would boot a windows partition.

---

### Post by pleriche on 2006-12-23
Currently don't have the alternate install cd (and I'm waiting for 3GB of OpenSuse to come down).

So I found the Grub User Manual, and before blowing away Grub from hda I tried grub-install /dev/hdc.

That didn't work. I'm getting confusd, I think it just gave LI again.

So I read a bit more of the manual and tried
root (hd2,0)
setup (hd2)
and for good measure
setup (hd2,0)

I then booted hdc from the BIOS and got a grub menu, but booting ubuntu , it said the filesystem type was FAT, ptn type 0xC and couldn't find vmlinux, error 15.

Trying to create a grub floppy according to the grub manual, dd gave a segmentation error.

I tried to create an iso image for a grub cd (I could only find an iso9660_stage1_5, not a stage2_eltorito), I actually got a .iso file, but trying to burn it to cd, it completed too fast and apparently burnt nothing.

---

