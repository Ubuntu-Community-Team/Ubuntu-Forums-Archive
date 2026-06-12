---
title: "Xorg"
date: 2007-10-15
forum: General Help
---

### Post by trackrat on 2007-10-15
I have just had a load of updates and among them was a kernel update.
I dual boot with XP and get the option to boot to generic 16 or 17 plus XP.
I know that I have to reinstall the Nvidia drivers but without the GUI, I am up the creek without a paddle.
Could someone please post the commands to install the Nvidia drivers from the command line.

Thanks for your time.

I can still boot into Linux using the origonal kernal.

---

### Post by Pumalite on 2007-10-15
sudo /etc/init.d/gdm stop
sudo sh /path/to/driver/NVIDIAxxxxx.run
sudo /etc/init.d/gdm start
If need be: startx

---

### Post by trackrat on 2007-10-15
Thanks for that reply, but it did not work, so i booted into the previous kernel and used Synaptic to remove the new one and everything is now back to normal.

Thank you for taking the time to reply.

---

