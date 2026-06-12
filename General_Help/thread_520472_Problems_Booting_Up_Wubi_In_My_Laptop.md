---
title: "Problems Booting Up Wubi In My Laptop"
date: 2007-08-08
forum: General Help
---

### Post by maurozea on 2007-08-08
I have an hp laptop and i installed wubi and when i rebooted i selected ubuntu, but when it appeared to be done setting up, it restarted, and now nothing will boot, itll get to the hp page where you can go to the bios and then itll go blank and go back to that page, and itll keep doing this over and over
please if you guys could help me, it would be great
thx

---

### Post by maurozea on 2007-08-08
oh and by the way i have 2 hard drives, but i did install wubi on c

---

### Post by tinybit on 2007-08-08
Try to use grub4dos instead of GNU GRUB, and it will be OK.

---

### Post by maurozea on 2007-08-08
ok but how do i do that since i cant even boot up to windows it just loops the main screen, any key combination that i can press while the screen is blank?

---

### Post by azagorath on 2007-08-08
it sounds like you replaced the NTLDR with grup . what you can do is try to boot from live CD and mount your windows drive , and then try to edit boot.ini in your C drive (where windows at ) :guitar:

---

### Post by tinybit on 2007-08-08
Try to boot a dos from floppy or cdrom, run grub.exe, and chainload ntldr or bootmgr to enter your Windows.

---

### Post by hh93 on 2007-08-29
> **maurozea said:**
> I have an hp laptop and i installed wubi and when i rebooted i selected ubuntu, but when it appeared to be done setting up, it restarted, and now nothing will boot, itll get to the hp page where you can go to the bios and then itll go blank and go back to that page, and itll keep doing this over and over
please if you guys could help me, it would be great
thx

seems like boot problem; is windows CD available?

---

