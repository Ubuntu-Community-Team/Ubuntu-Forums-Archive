---
title: "Display problem AGAIN!"
date: 2007-11-21
forum: General Help
---

### Post by Hizzoner on 2007-11-21
I have re-installed U 7.10. Once again the display will not center on the LCD monitor.
I have in th epast re-installed U 7.10 to over come this prob. [NVIDIA card].
There must be an easier method to fix this prob. Any ideas, folks?

---

### Post by ubuntokun on 2007-11-21
You can edit your /etc/X11/xorg.conf by hand, removing the high resolution that doesn't work.

Code:

sudo nano -Bw /etc/X11/xorg.conf

Save it with <Ctrl>o and exit with <Ctrl>x. Then, reboot and see if it works again.

Code:

sudo shutdown -r now

---

### Post by Hizzoner on 2007-11-21
I rtied the fix. It did not work.
My other fix tgough did work perfectly.
I uninstalled Ubuntu 7.10, and have gone back to Windows XP Pro as my only O/S.
Ubuntu is still a work-in-progress, IMHO.
Perhaps Ubuntu 99.999 will be O.K.

---

