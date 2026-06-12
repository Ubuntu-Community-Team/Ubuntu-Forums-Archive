---
title: "Unable to boot in Safe Mode"
date: 2024-08-30
forum: General Help
---

### Post by skippylou on 2024-08-30
I want to fix LibreOffice which has been corrupted.  I am using 20.04.6 on a Lenovo P620 threadripper pro.  Linux only, not a dual boot system.

Boot holding down CTRL gives normal boot.

Boot holding down ESC gives:

***********************************

GNU GRUB version 2.06

Minimal Bash-like line editing is supported.  For the first word, TAB lists the possible command completions,

***********************************

There are dozens of possibilities when I hit TAB.  None seems appropriate.  Tried BOOT and it replies "you need to load the kernel first".  But How?

Is it possible to reboot in safe mode with a terminal command?

---

### Post by skippylou on 2024-08-30
Here is the info I got from Boot Repair:

[https://paste.ubuntu.com/p/Y9WhW3dNbc/](https://paste.ubuntu.com/p/Y9WhW3dNbc/)

---

### Post by tea for one on 2024-08-31
> **skippylou said:**
> I want to fix LibreOffice which has been corrupted.  I am using 20.04.6 on a Lenovo P620 threadripper pro.  Linux only, not a dual boot system.
> Safe mode is a mode where LibreOffice temporarily starts with a fresh user profile and disables hardware acceleration. It helps to restore a non-working LibreOffice instance. 
You can open LibreOffice in safe mode via the terminal:-
```
libreoffice --safe-mode
```
> **skippylou said:**
> Is it possible to reboot in safe mode with a terminal command?
As you can still boot into Ubuntu, it may be useful if you altered Grub to always appear when you start the PC.
This will allow you to select Advanced Options > Recovery (if needed) or previous kernel
```
sudo nano /etc/default/grub
```
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=[COLOR="#0000FF"]menu[/COLOR] #replace hidden with menu
GRUB_TIMEOUT=[COLOR="#0000FF"]10[/COLOR] #replace 0 with 10 i.e. 10 second delay to allow choice
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=true
```
```
sudo update-grub
```

---

### Post by Rubi1200 on 2024-08-31
What exactly is corrupted about LibreOffice?

Try deleting the profile, when you restart LibreOffice a new and clean profile will be created.

---

### Post by skippylou on 2024-09-04
> **tea for one said:**
> You can open LibreOffice in safe mode via the terminal:-
```
libreoffice --safe-mode
```

As you can still boot into Ubuntu, it may be useful if you altered Grub to always appear when you start the PC.
This will allow you to select Advanced Options > Recovery (if needed) or previous kernel
```
sudo nano /etc/default/grub
```
```

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=[COLOR="#0000FF"]menu[/COLOR] #replace hidden with menu
GRUB_TIMEOUT=[COLOR="#0000FF"]10[/COLOR] #replace 0 with 10 i.e. 10 second delay to allow choice
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=true
```
```
sudo update-grub
```

Thanks.

---

