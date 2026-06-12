---
title: "Cannot Log In"
date: 2007-05-07
forum: General Help
---

### Post by cd-r80 on 2007-05-07
I played with dpkg-reconfigure xserver-xorg. Now I cannot log in anymore. Recovery mode asks root password but does not accept it. Continue & normal boot goes to just blank screen. I cannot open virtual console ctrl+alt+2 etc. What can I do?

---

### Post by rai4shu2 on 2007-05-07
You do mean of course ctrl+alt+F1/F2 etc?

---

### Post by taurus on 2007-05-07
Did you make a backup copy of your /etc/X11/xorg.conf?  You can boot from the LiveCD, mount your /, then copy the backup back again.

---

### Post by cd-r80 on 2007-05-07
Yes I mean f2, f3. etc. No backup. Ok perhaps at first I try to copy from LiveCD.

---

### Post by taurus on 2007-05-07
Boot with the LiveCD and post the output of this command from a terminal.  Need to mount your root partition, /, from the harddrive.

```
sudo fdisk -l
```

---

### Post by cd-r80 on 2007-05-08
Yes I mounted & copied xorg.conf & restored X then. X ok now. XFCE not... I just would have liked to know some boot options to open console without LiveCD.

---

### Post by taurus on 2007-05-08
Boot into recovery mode from GRUB menu.

---

### Post by cd-r80 on 2007-05-09
Like I said recovery mode asks password, but does not accept it. Other option Ctrl +d goes to the same blank screen.

---

### Post by taurus on 2007-05-09
Did you create a password for root?  

How about booting with the LiveCD?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by cd-r80 on 2007-05-09
Yes, like I said before I managed to repair X with the LiveCD. Of course I had root password. I  had used the installation already for months.

---

