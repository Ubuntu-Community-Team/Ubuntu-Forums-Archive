---
title: "ubuntu upgrade destroyed cryptsetup drive?"
date: 2015-05-07
forum: General Help
---

### Post by MarisO on 2015-05-07
hi

I have an external disk encrypted with cryptsetup / luks.

I used this command to open encrypted drive:
**[FONT=courier new]cryptsetup luksOpen /dev/disk/by-uuid/a4e7f267-c667-4912-b12e-e66c74b5120d c1[/FONT]**

Today I noticed that the disk is gone   and it seems to be changed into this:
[B][FONT=courier new]/dev/sda5: UUID="OKPUd8-Bz0v-SCui-SAt7-feoH-uGz3-JGOCQ8" TYPE="LVM2_member"
[/FONT][/B]
I did apt-get upgrade recently.    Did upgrade destroy encrypted disk?   Why did it change UUID ?

Ubuntu 14.04.2 LTS,  kernel 3.13.0-32-generic


last update:

Start-Date: 2015-04-28  04:25:04
Commandline: apt-get upgrade
Upgrade: initscripts:amd64 (2.88dsf-41ubuntu6, 2.88dsf-41ubuntu6.1)


Looks like device header got deleted:

**[FONT=courier new]sudo cryptsetup -v luksDump /dev/sda5                                                                            [/FONT]**
**[FONT=courier new]Device /dev/sda5 is not a valid LUKS device.[/FONT]**
**[FONT=courier new]Command failed with code 22: Device /dev/sda5 is not a valid LUKS device.[/FONT]**

---

### Post by MarisO on 2015-05-07
problem solved,  after reboot disk is back :popcorn:

---

