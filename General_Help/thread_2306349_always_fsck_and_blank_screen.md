---
title: "always fsck and blank screen"
date: 2015-12-14
forum: General Help
---

### Post by bjlockie on 2015-12-14
My computer always seems to do an fsck on bootup.
The screen is blank but the disk activity light on my case is on.
I get the motherboard splash screen (and maybe grub, it goes by too fast).
I shut it down normally so it shouldn't be doing an fsck.
Is there a key to switch to a text mode so I can at least see what did it is checking?

Could it be related because I use bind in my fstab?
sda iss an SSD.
I tried to put /var on the hdd too but I couldn't make it work.

UUID=ba1b1bda-9bbb-46fe-a91b-bf5a9856caa5 /               ext4    noatime,errors=remount-ro 0       1
UUID=1a65f0aa-091b-4561-85f8-0d7b450a3ec5    /os-hdd      ext4    errors=remount-ro 0       1
UUID=b7c60eb6-5501-4f1e-9c05-a416770cc32f    /storage      ext4    errors=remount-ro 0       1
UUID=eca5ef35-1a89-43e0-ad37-1d8a93ba2a3f    /other      ext4    errors=remount-ro 0       1
/os-hdd/home              /home                none    bind    0 0

---

### Post by bjlockie on 2015-12-15
Alt-F7 got me the console, /dev/sda1 was clean but it didn't say what it was doing.

---

