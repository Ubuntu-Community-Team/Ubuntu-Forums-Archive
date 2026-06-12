---
title: "Bootable SD Card - Get back write access"
date: 2017-03-14
forum: General Help
---

### Post by schnuckenack2 on 2017-03-14
Hello

I have created a bootable sd-card from an Ubuntu image. After installation I would like to free the storage from said data and use it otherwise. There is a problem however. The "Delete" option in Nautilus is turned off. I can't delete anything that way. Neither can I delete or give write rights to the sd-card via terminal. Not even as sudo. I made sure the physical write protection pin is in write mode of course. The attempt to format the device throws an error.

The heck?!

Sincerely yours,

Schnuckenack

---

### Post by sudodus on 2017-03-14
You can install ***mkusb*** and use it to restore the SD card to a standard storage device. See the following links

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[wipe and/or restore](https://help.ubuntu.com/community/mkusb/wipe)

If mkusb cannot do it, I am afraid that the SD card is damaged internally (physically).

---

### Post by Impavidus on 2017-03-14
By turning the sd card into an ubuntu live disk, you gave it a read-only file system. You cannot delete files from those or even mount them read-write mode. You have to format the sd card before you can use it for anything else. Disk formatting tools should be able to do the job. mkusb is simple, safe and very reliable.

---

### Post by schnuckenack2 on 2017-03-25
Thank you guys!

---

