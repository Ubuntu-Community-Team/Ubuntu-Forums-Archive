---
title: "CD tray will not open on server LTS 12.04"
date: 2012-11-10
forum: General Help
---

### Post by simvin76 on 2012-11-10
Hello

When I insert a CD or DVD in the CD/DVD player, I can't eject the tray with the physical button.
The disc is not mounted and I can eject it with usr/bin/eject.

Before the upgrade LTS 10.04 -> LTS 12.04 this was not a problem.
The physical button works fine before Ubunto boots. When Ubuntu is running the button only works if the tray is open. If the tray is closed with no disc, it doesn't work.

My fstab:
```
proc            /proc           proc    defaults        0       0
UUID=e04fe8f4-0769-4fff-a685-1688e94e1339 /               ext3    relatime,errors=remount-ro 0       1
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/vgr01/pub  /pub            ext3    relatime,errors=remount-ro      0      2
/dev/vg00/backup /backup        ext3    relatime,errors=remount-ro      0      2
/dev/vg00/backup_work /backup/work ext3 relatime,errors=remount-ro      0      2
```

Best regards
Simon

---

### Post by rnerwein on 2012-11-10
> **simvin76 said:**
> Hello

When I insert a CD or DVD in the CD/DVD player, I can't eject the tray with the physical button.
The disc is not mounted and I can eject it with usr/bin/eject.

Before the upgrade LTS 10.04 -> LTS 12.04 this was not a problem.
The physical button works fine before Ubunto boots. When Ubuntu is running the button only works if the tray is open. If the tray is closed with no disc, it doesn't work.

My fstab:
```
proc            /proc           proc    defaults        0       0
UUID=e04fe8f4-0769-4fff-a685-1688e94e1339 /               ext3    relatime,errors=remount-ro 0       1
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/vgr01/pub  /pub            ext3    relatime,errors=remount-ro      0      2
/dev/vg00/backup /backup        ext3    relatime,errors=remount-ro      0      2
/dev/vg00/backup_work /backup/work ext3 relatime,errors=remount-ro      0      2
```Best regards
Simon

hi
this look like the default of your system is:
eject -i o
--> man eject 
-i on|1|off|0
            This option controls locking of the hardware  eject  button.  When
            enabled, the drive will not be ejected when the button is pressed.
            This is useful when you are carrying a laptop in a bag or case and
            don't want it to eject if the button is inadvertently pressed.

---

### Post by simvin76 on 2012-11-10
Thank you, that solved it.
Now I have to figure out why the eject button is switched off every time a disc is loaded.
Short term solution is to run a cron job every minute with "sudo eject -i 0".

---

### Post by dcstar on 2012-11-10
> **simvin76 said:**
> Thank you, that solved it.
Now I have to figure out why the eject button is switched off every time a disc is loaded.
Short term solution is to run a cron job every minute with "sudo eject -i 0".

I would guess that the system has been configured for a Graphical Desktop to control the CD/DVD and since the server version does not have one of these the default setting is incorrect.

You should lodge a Launchpad bug for this.

---

