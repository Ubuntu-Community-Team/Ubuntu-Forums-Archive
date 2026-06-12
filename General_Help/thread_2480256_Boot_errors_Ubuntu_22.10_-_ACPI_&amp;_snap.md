---
title: "Boot errors Ubuntu 22.10 - ACPI &amp; snap"
date: 2022-10-23
forum: General Help
---

### Post by zkab on 2022-10-23
When booting Ubuntu I receive following errors:
```
sudo dmesg | grep -i error

[    0.775985] RAS: Correctable Errors collector initialized.
[    0.776099] ACPI Error: No handler for Region [ECRM] (000000001f075226) [EmbeddedControl] (20220331/evregion-130)
[    0.776605] ACPI Error: Region EmbeddedControl (ID=3) has no handler (20220331/exfldio-261)
[    0.776625] ACPI Error: Aborting method \_SB.GPIO._EVT due to previous error (AE_NOT_EXIST) (20220331/psparse-529)
[   15.998889] snapd-desktop-i[2127]: segfault at 0 ip 00007f84c66b63d4 sp 00007ffd6ab96be8 error 4 in libglib-2.0.so.0.6400.6[7f84c668c000+9a000]
[   16.419804] snapd-desktop-i[2252]: segfault at 0 ip 00007f79137fc3d4 sp 00007ffc3fab4fc8 error 4 in libglib-2.0.so.0.6400.6[7f79137d2000+9a000]

```

How can they be fixed?
I have Dual Boot System (Windows11 & Ubuntu 22.10) running on Beelink GTR5 5900HX.

---

### Post by zkab on 2022-11-01
I changed to 'beta'

gnome-3-38-2004   0+git.6f39565   119    latest/beta 

and after that the 'snap-dektop' error was gone.

---

