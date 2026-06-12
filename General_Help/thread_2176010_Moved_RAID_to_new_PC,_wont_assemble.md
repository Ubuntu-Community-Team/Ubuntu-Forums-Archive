---
title: "Moved RAID to new PC, wont assemble"
date: 2013-09-22
forum: General Help
---

### Post by ThePhantom0114 on 2013-09-22
[COLOR=#333333][FONT=UbuntuRegular]Alright, so I swapped the system board out on my server running Ubuntu 12.04. The OS is on its own drive, and then I have 1 storage drive, and 3 drives in a Raid 5. Well, when booting up with the new board, I get a raid failed error and it drops me to a busybox shell, no matter if I choose yes or no at the boot degraded raid screen, it drops me to shell. I can then exit and get to ubuntu.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Running:[/FONT][/COLOR]
```
fdisk -l 

```[COLOR=#333333][FONT=UbuntuRegular]shows me that all drives are seen fine, but if I try to run[/FONT][/COLOR]
```
mdadm --assemble --scan

```[COLOR=#333333][FONT=UbuntuRegular]nothing happens, if I manually specify the drives with[/FONT][/COLOR]
```
mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sde1 

```[COLOR=#333333][FONT=UbuntuRegular]then I get several errors, first sda1 is busy, then no superblock found on sdb1, then it aborts.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Running[/FONT][/COLOR]
```
mdadm --examine /dev/sd*

```[COLOR=#333333][FONT=UbuntuRegular]shows that sda looks good, shows the raid details, knows its a 3 device raid 5, looks great...sdb and sde however show no md superblock detected...[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Can anyone help me out here? I have a LOT of data on these drives that I REALLY don't want to lose...I tried to research this before hand and all forums said it was really easy, just run mdadm --assemble --scan and you are done...yeah that didnt work, so please, any help would be appreciated. Thanks.[/FONT][/COLOR]

---

### Post by SaturnusDJ on 2013-09-23
Post the output of the examine's.

Most likely you already tried, but sometimes reboots/poweroffs 'bring back' superblocks.

---

