---
title: "Deleted ubuntu partition now I cant boot"
date: 2019-11-08
forum: General Help
---

### Post by zapponej on 2019-11-08
I deleted my ubuntu partition using gparted live now I cant boot windows 10. All I get to is the grub rescue. Unfortunately I didnt have ubuntu live usb made and I dont have access to a computer to make one. I have gparted live but I dont know if I can download boot repair or something while on it.
Also I havent been able to configure the wireless connection in gparted live.

Any help would be greatly appreciated.

---

### Post by oldfred on 2019-11-08
UEFI or BIOS install?
If UEFI, just reboot and use UEFI boot key to choose the Windows boot entry. The set that as default in UEFI.

If BIOS, you need to install a Windows or Windows type boot loader to MBR. Do not know if gparted ISO includes syslinux or not which is a Windows type boot loader.
It looks like my gparted ISO .32 version uses syslinux for BIOS boot.
You then may be able to install it, or copy to MBR.
You do not want a full syslinux install, just the MBR portion that will chain to the partition with boot flag which then must have your Windows boot files.

See if gparted ISO has mbr.bin.
Then something like this from where ever it has it.
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

---

### Post by zapponej on 2019-11-09
Thanks I actually just got it I just had to set a different partition as boot and it seemed to work. But thanks for your reply.

---

