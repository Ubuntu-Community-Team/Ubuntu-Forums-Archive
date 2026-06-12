---
title: "Ubuntu desktop on VBOX. [FAILED] Failed to mount /boot"
date: 2022-02-17
forum: General Help
---

### Post by aitijneg on 2022-02-17
Dear Gurus,
I have Ubuntu Desktop running on VBOX. Everything is fine and this issue might be just cosmetic but every time when machine booting up I see the "[[COLOR=#ff0000]FAILED[/COLOR]] Failed to mount /boot" message and few "[[COLOR=#ff8c00]DEPEND[/COLOR]]  Dependency failed for..." messages. Anyways the system is booting up and working after that. I did some digging into the problem and found this 

[FONT=courier new]$ systemctl list-units  boot.mount[/FONT]
[FONT=courier new]  UNIT       LOAD   ACTIVE SUB    DESCRIPTION[/FONT]
[FONT=courier new]&#9679; [COLOR=#ff0000]boot.mount[/COLOR] loaded [COLOR=#ff0000]failed failed[/COLOR] /boot      [/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]LOAD   = Reflects whether the unit definition was properly loaded.[/FONT]
[FONT=courier new]ACTIVE = The high-level unit activation state, i.e. generalization of SUB.[/FONT]
[FONT=courier new]SUB    = The low-level unit activation state, values depend on unit type.[/FONT]
[FONT=courier new]
[/FONT]
[FONT=courier new]1 loaded units listed. Pass --all to see loaded but inactive units, too.[/FONT]
[FONT=courier new]To show all installed unit files use 'systemctl list-unit-files'.[/FONT]

At this point I don't know what should be the next steps to troubleshoot. Can you please help me out? 

My system is Ubuntu 20.04.3 LTS with ZFS

Best regards,

---

### Post by MAFoElffen on 2022-02-18
Does it ever start? Has this just happened recently and now you can't get in?

I just feel like I'm missing part of the story there...

Because the instramfs, when it updates the system on ZFS, you probably have noticed that the last thing it sends a message to console at the end of that process, is that it says: "ZSys is adding automatic system snapshot to GRUB menu", or something along those lines...

This ZFS ZSys snapshot feature is turned on by default in Ubuntu. On boot, if your VM boots via BIOS/CSM mode, after the BIOS Messages, but before the System boots, hit the Spacebar a few times for the Grub Menu to show. If UEFI, then you use the ESC key. 

Select the third Menu Item, labeled as History For Ubuntu 20.04... Select an earlier ZFS Snapshot to restore and boot from...

---

### Post by aitijneg on 2022-02-19
MAFoElffen, yes. The system starts and works normally. I don't see any problem. Just 'Failed' message during the booting up annoying me. 
I missed the moment when it happened. I noticed the message some time ago but ignored it for a while.
Also I'm destroying from time to time old zfs snapshots so I don't have backup state of the system before the issue noticed first time.
I don't do anything bad or weird with the system. I use it for running a python scripts mostly. The system is being updated from time to time via native  'Software Updater' utility from GUI. That's it.

---

