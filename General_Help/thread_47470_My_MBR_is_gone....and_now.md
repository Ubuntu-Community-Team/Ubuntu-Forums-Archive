---
title: "My MBR is gone....and now?"
date: 2005-07-08
forum: General Help
---

### Post by Skaman on 2005-07-08
I have a pc with 2 h-disks
a s/ata hd  /dev/sda
a ata hd    /dev/hdb 

i had to reinstall windows (crappy thing) in sda but windows (intellligent OS...)f***d up the hdb MBR,so I cant boot my linux hd

what shall I do now?

I've tried to boot from a knoppix cd and after mounting /dev/hdb2 i can see all my files..
i opened a shell & typed:"grub-install" /dev/hdb2 but" i got an error....
what should I do to reinstall GRUB and be able to boot??


thnx all

---

### Post by angkor on 2005-07-08
To reinstall grub:

1. boot from your Ubuntu InstallationCD
2. type rescue at the boot prompt.
3. select your root partition
(4. mount /usr if it's on a different partition, like it is in my case)
5. type grub-install

And reboot.

Hope it works...

---

### Post by Skaman on 2005-07-08
[QUOTE=angkor]To reinstall grub:

1. boot from your Ubuntu InstallationCD
2. type rescue at the boot prompt.
3. select your root partition
(4. mount /usr if it's on a different partition, like it is in my case)
5. type grub-install

And reboot.

Hope it works...[/QUOTE]
 Worked great!
Thnx never be4 have done this on ubunto and i was a little disappointed!

---

### Post by angkor on 2005-07-08
Welcome,  :) 

Worked for me too when I hosed grub one day, just replaced the 'grub-install' part with 'update-grub' and I had a clean grub to work with.

---

