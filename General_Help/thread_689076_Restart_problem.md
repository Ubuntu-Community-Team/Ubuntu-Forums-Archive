---
title: "Restart problem"
date: 2008-02-06
forum: General Help
---

### Post by Ryan Strife on 2008-02-06
I have a acer Ferrari 1000, using Ubuntu gutsy. after restarting, it hangs at the boot screen. Dual-booting windows XP. Anybody know how to fix this???

---

### Post by K.Mandla on 2008-02-06
Not specifically, but if you reboot the machine, hit Escape at the Grub menu and take "quiet" and "splash" out of the boot line, you should be able to see where, and maybe why, it's freezing.

---

### Post by kesman on 2008-02-06
You should make the change permanent by editing the grub menu file.
For that, do
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
sudo nano /boot/grub/menu.lst

```
Then browse to the part that has the linux loader in it, and remove splash and quiet from the end of the line. Then exit with ctrl+x and answer YES to save the file. Now reboot your machine and you should be able to see what's going on in the boot process.

---

### Post by Ryan Strife on 2008-02-07
thanks. the solution works.

---

