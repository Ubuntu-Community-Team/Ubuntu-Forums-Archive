---
title: "Failed to open \EFI\BOOT\grubx64.efi - Not Found (Dual Boot Ubuntu with Windows 11)"
date: 2022-05-01
forum: General Help
---

### Post by stfields on 2022-05-01
I have a laptop that came installed with Windows 11.  I installed Ubuntu 22.04, and it was running great for a while.  Yesterday I booted into Windows, did nothing of note, and now the Ubuntu boot loader fails.  The error message on boot is:

```

Failed to open \EFI\BOOT\grubx64.efi - Not Found
Failed to load image /EFI/ubuntu/grubx64.efi: Not Found
start_image() returned Not Found, falling back to default loader
Failed to open \EFI\BOOT\grubx64.efi - Not Found
Failed to load image /EFI/ubuntu/grubx64.efi: Not Found
start_image() returned Not Found
```

I ran boot-repair, and the report is [here]("https://paste.ubuntu.com/p/qvpxmMTWgS/").

I am hoping that someone can take a look at this and tell me whether to make the recommend repairs, or to do something different.

---

### Post by oldfred on 2022-05-01
You have an old Linpus Lite entry that refers to an ESP that does not exist.
Line 93 in report.

I might remove that.
man efibootmgr
Check that it still is 0000
sudo efibootmgr -v
sudo efibootmgr -b 0000 -B

If in UEFI boot menu, you choose the ubuntu entry does it boot?
You may want to make Ubuntu as first or default UEFI boot entry.
This works on most but not HPs. With HP, you have to go into UEFI settings to change boot order.

Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
 sudo efibootmgr -o 3,2
sudo efibootmgr -v

---

### Post by stfields on 2022-05-03
Thanks for the quick response and the suggestions.  I've got it up and running now.

---

### Post by xjhyyds on 2022-12-09
Hello, I have the same problem. I have installed windows 11 and ubuntu 20.04 dual system on a dell lucent 16plus computer, but today when I boot up the system I cannot load the Uefi option for ubuntu. The error message is the same as yours. How did you solve this problem?

---

### Post by oldfred on 2022-12-09
@xjhyyds
That system is so new it will need 22.04 at minimum.
I have a new Dell but its 11th gen with just Intel graphics. And 22.04 just worked. I did need bitlocker off in Windows.
Also if nVidia you need Safe boot & install of restricted drivers, so correct nVidia driver installed.

---

