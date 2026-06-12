---
title: "please help cant log in"
date: 2008-05-19
forum: General Help
---

### Post by Dumazz on 2008-05-19
I attempted to change the user/ administrator info to a diff one and now when i go to log in i get (gnome-session:4485): libgnomevfs-WARNING**:unable to create _/.gnome2 directory: no such file or directory
could not create per-user gnome configuration directory '/home/t-mac/.gnome2/' no such file or directory

i tried going into a failsafe terminal and always get permission denied when i try to make it a directory and it wont allow me to log on as the original user due to the fact that i altered it

---

### Post by jpeddicord on 2008-05-19
You probably chown'd yourself out of your home folder. Try booting into recovery mode by pressing ESC at the GRUB is Loading screen when your computer first powers on. Select the option with (recovery mode) at the end, and let it boot. You will end up with a blank terminal.

Then type these commands, in order:
```
chown -R t-mac:t-mac /home/t-mac
chmod -R 755 /home/t-mac
reboot
```

Once it reboots back into normal mode, try to sign in again. You should be good from there on out. :)

---

