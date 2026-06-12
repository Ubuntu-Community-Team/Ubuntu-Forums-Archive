---
title: "dual booting: clock keeps changing time"
date: 2006-12-12
forum: General Help
---

### Post by munkyeetr on 2006-12-12
I have Ubuntu running on a SATA drive, and Windows XP running on a PATA drive. Grub does not handle both OS's, just Ubuntu. I use F11 on startup and choose the drive to boot from.

The problem is each time I boot into Windows, I have to change the clock to the proper time. Then when I boot into Linux I have to change the clock there again. This just goes back and forth whenever I switch.

Is there a way to make them hold their time?

---

### Post by Ramses de Norre on 2006-12-12
```
sudo gedit /etc/default/rcS
```
And set ```
UTC=yes
```
to no.

---

### Post by munkyeetr on 2006-12-12
Thanx.

---

### Post by satya_461 on 2007-12-11
I faced the same problem. The system time keeps changing and it changes the bios time too..

Got fixed by setting UTC=no 

Thank you very much.. :)

---

### Post by metalf8801 on 2008-03-22
> **Ramses de Norre said:**
> ```
sudo gedit /etc/default/rcS
```
And set ```
UTC=yes
```
to no.
Thank you

---

