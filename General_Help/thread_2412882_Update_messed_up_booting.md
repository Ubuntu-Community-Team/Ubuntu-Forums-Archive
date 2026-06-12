---
title: "Update messed up booting"
date: 2019-02-18
forum: General Help
---

### Post by linuxhippy on 2019-02-18
I am running XUbuntu 18.10 64 bit on an Intel Cherry Trail Z83-F Fanless Mini PC pictured here:

[https://www.amazon.com/gp/product/B07L8FPSPH/ref=oh_aui_search_asin_title?ie=UTF8&psc=1]("https://www.amazon.com/gp/product/B07L8FPSPH/ref=oh_aui_search_asin_title?ie=UTF8&psc=1")

It came with Win 10 but for months now I've only had XUbuntu 18.10 on this and after my last upgrade it no longer automatically boots anything but gets caught in a boot loop where it keeps shutting down after the BIOS screen.  I found that if I press F7 that I can get a list of boot devices and it seems to be looking for something that doesn't exist (Android-IA) because when I select the second option of Ubuntu then it boots.  XUbuntu split up my eMMC storage into 2 partitions and one is a FAT32 boot partition which is probably called Ubuntu to the BIOS but blkid lists this:

/dev/mmcblk0p1: UUID="E0E7-8A64" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="1cb14996-9590-4bdf-8788-7324568b3d8c"
/dev/mmcblk0p2: UUID="a3390c97-2d39-4fc7-920d-f8ffc4aef310" TYPE="ext4" PARTUUID="ea6def21-04fb-48f8-9e8d-bbaece7ea1f8"
/dev/mmcblk0: PTUUID="ecaa2f68-dfc0-4d0b-88ad-18a8a9f21708" PTTYPE="gpt"

I've tried sudo grub-install /dev/mmcblk0 and /dev/mmcblk0p1 with no errors but it still doesn't boot.

How can I restore it to automatically boot again without my intervention?

Marty

---

### Post by oldfred on 2019-02-18
That is UEFI boot menu.
Usually you can change boot order in UEFI under the boot tab for all the UEFI settings.
Or you can use efibootmgr which works for most systems.

To see entries:
sudo efibootmgr -v
see also:
man efibootmgr
To change order:
       Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
example, must use your order:
sudo efibootmgr -o 2,1 

If you have old entries you may want to delete them.
      
 Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B

---

### Post by linuxhippy on 2019-03-02
I didn't know about that but those commands worked-thanks!!

Marty

---

### Post by oldfred on 2019-03-02
Glad that worked.
You can change to [Solved].

---

### Post by linuxhippy on 2019-03-02
I marked it solved.

I should mention should anybody else come across this post that my computer gave me a bit of trouble just using the command:

```
sudo efibootmgr -o XXXX,XXXX
```

Before reboot I verified the boot order with:

```
sudo efibootmgr -v
```

But when I booted it got changed back to the way it was with Android booting first.  That Android entry on my computer is empty and I'm not sure why it's there.  I used that -b command to delete all the other entries besides Ubuntu and then it was good:

> Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.

```
sudo efibootmgr -b XXXX -B 
```

---

