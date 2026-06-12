---
title: "[SOLVED] glipper"
date: 2008-03-05
forum: General Help
---

### Post by Rytron on 2008-03-05
Hi,
I recently installed Glipper.
The problem is that it once worked - now I cannot start it.
I click on the icon and nothing happens.

Please help.

Thank you.

---

### Post by kesman on 2008-03-05
have you tried to run it from terminal? That way you'd be able to see all the error messages it may generate.

---

### Post by Rytron on 2008-03-05
:~$ glipper

(process:7985): Gnome-CRITICAL **: gnome_program_module_register: assertion `module_info' failed

---

### Post by Oldsoldier2003 on 2008-03-05
> **Rytron said:**
> :~$ glipper

(process:7985): Gnome-CRITICAL **: gnome_program_module_register: assertion `module_info' failed

from the terminal:

```
sudo apt-get purge glipper
sudo apt get install glipper
```

if that doesn't solve the issue you can continue troubleshooting.

---

### Post by Rytron on 2008-03-05
Hi Oldsoldier2003,
I got it working - I must have accidentally removed notification area from my panel.
I added this again and glipper is back.
It is great solving problems in Ubuntu.
Cheers.

---

### Post by Rytron on 2008-07-20
> **Oldsoldier2003 said:**
> from the terminal:

```
sudo apt-get purge glipper
sudo apt get install glipper
```

if that doesn't solve the issue you can continue troubleshooting.

Just a quick correction:
sudo apt-get purge glipper
sudo apt**-**get install glipper

---

