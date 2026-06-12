---
title: "GRUB and dual boot."
date: 2013-04-19
forum: General Help
---

### Post by Kashic on 2013-04-19
First off, I am not too skilled with unix/linux OS, but I know some stuff. I have a laptop with W7 and Mandriva on it. It had GRUB from  the mandriva install I guess. Anyways, i deleted that partition, and made a new  one getting ready for a new ubuntu install. 

  Whenever I turn on the laptop, it gets a GRUB Loading .... Error 17. And it wont do anything.

  I read somewhere to try to use a live usb to be able to change the  HDA? When I did this with my W7 Desktop (other PC completely) the flash  drive didn't do anything, it said there was no bootable OS. I had used [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)    Pendrives usb installer. I put the USB back into my desktop, and it  won't read, I assume since the MBR changed? I tried to use another flash  drive, and it got errors during the process, 202 errors in pendrive.  Then it wouldnt recognize that now. I have no access to my laptop. How  can I fix my GRUB or get past it? Now I can't read either USB device on my desktop.

Thank you in advance for any and all help!

---

### Post by Jacob-Gates on 2013-04-19
can you go into the motherboard bios at all? if so, set it to boot with a cd/dvd first and put a live cd in. When you install ubuntu with dual boot it will create a new grub.

---

### Post by Kashic on 2013-04-19
I was able to load a dvd ubuntu, and am installing it to see if it reloads a GRUb. Thanks for the info. Will come back with updates if it doesnt work.

---

### Post by Kashic on 2013-04-19
Awesome Jacob!! I now have a new grub menu. 

One last question, how can I make the USB drives readable on Windows again? Changing the MBR?

---

### Post by oldfred on 2013-04-19
Installer flash drives are usually formatted FAT32. Windows should read that without issue. But do not use FAT32 on large drives or newer larger flash drives as NTFS is better as it has journal.

Windows only reads first partition on flash drives.

---

