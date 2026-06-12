---
title: "Ubuntu 16.04 After update, usb, wifi, ethernet and hdmi are inoperative"
date: 2018-11-18
forum: General Help
---

### Post by Bill Roberts on 2018-11-18
Using a Lenovo Legion laptop dual booted with Windows 10.

I ran apt update, followed by apt-get autoclean.

After reboot into linux, the laptop will not connect with wired ethernet or wifi, so no internet or lan access. The usb devices do not connect, so no mouse, keyboard, or optical drive. The hdmi external monitor doesn't connect either.

Booting into Windows is normal and all the items failing in linux work correctly. No hardware issues.

My backups are on router connected external hard drives.

Providing command output files is essentially impossible, unless I copy them manually, which would be very time consuming and error prone.

Is anyone willing to advise me without having full access to command outputs. I would prefer to work on ethernet and wifi first.

---

### Post by jeremy31 on 2018-11-18
Use the grub menu/advanced options to boot into an older kernel, you might have to use the down arrow 3 times and see if everything works in an older kernel, then we can proceed with fixing it

---

### Post by Bill Roberts on 2018-11-18
The autoclean removed all but one kernel.

---

