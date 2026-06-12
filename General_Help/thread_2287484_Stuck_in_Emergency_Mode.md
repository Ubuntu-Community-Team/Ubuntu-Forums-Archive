---
title: "Stuck in Emergency Mode"
date: 2015-07-20
forum: General Help
---

### Post by johnbo96 on 2015-07-20
For some reason whenever I boot I get the following:
```
[0.8744291] ACPI PCC probe failed.
starting version 219
[3.539015] sd 5:0:0:0: [sdb] No Caching mode page found
[3.539065] sd 5:0:0:0: [sdb] Assuming drive cache: write through
...generic emergency mode greeting...
```
I apologize, the above is hand typed so I sorta skipped that end bit. The generic emergency mode greeting does offer me the command 'systemctl default' which gets x and some of the other [L]ubuntu goodies. But accessing/managing files is virtually impossible and the taskbar is missing.

My own diagnosis is that [http://www.ext2fsd.com/](http://www.ext2fsd.com/) somehow caused it, seeing as it only happened after accessing my ext partition from Windows.
Opening the system log via 'journalctl -xb' yields some data about write protection, but it's hard to tell what's important and what's not with 1000+ lines of log. It's quite possible that I'm just grabbing that to support my own diagnosis.

Does anyone know how I can get my system back up normally. I suppose I could copy everything over to my Windows partition and reinstall Lubuntu it's probably due for it anyway, but I'd rather not.

And apologies if this is in the wrong section, I didn't really know where to go with this.

Thanks!

---

### Post by dino99 on 2015-07-20
"ACPI PCC probe failed" is a simple info; meaning that your hardware does not have that chipset feature; so its harmless

ubuntu and the likes use ntfs-3g driver to deal with windows; so no needs for ext2fsd

---

### Post by johnbo96 on 2015-07-20
> **dino99 said:**
> "ACPI PCC probe failed" is a simple info; meaning that your hardware does not have that chipset feature; so its harmless
Okay, based off of a few other threads I didn't think it was the thing causing the issue.

> **dino99 said:**
> ubuntu and the likes use ntfs-3g driver to deal with windows; so no needs for ext2fsd
Nah there's nothing wrong with accessing the windows partition from ubuntu. ext2fsd is for accessing the ubuntu partition from windows.

---

### Post by ajgreeny on 2015-07-20
It sounds as if the ext2fsd driver in windows has done something nasty to your linux partition.  Assuming you can get to the ubuntu OS as your user you can run the command ```
sudo touch /forcefsck
``` then reboot.

That command forces a filesystem check at the next boot which may overcome any damage the windows driver has caused.

If you can not get into your ubuntu OS, boot to a live ubuntu DVD or USB and from that run command ```
sudo e2fsck /dev/sdx#
``` where sdx# is your ubuntu root partition, to see if any filesystem faults are seen.

If you really want to access files in your ubuntu partitions from windows you would be advised to use a shared NTFS partition for those files you need to access from both OSs.  I would advise that you do not access any filesystem partitions of either OS from a running OS of the other OS as file corruption from doing so is certainly not unknown.

---

### Post by johnbo96 on 2015-07-20
Before I got a chance to try either I got booted to GRUB rescue. I think I've learned my lesson...
Unless anyone has any ideas, I'll be copying everything important to a thumb drive and reinstalling Windows (via recovery partition) and Lubuntu (via CD/USB).

---

