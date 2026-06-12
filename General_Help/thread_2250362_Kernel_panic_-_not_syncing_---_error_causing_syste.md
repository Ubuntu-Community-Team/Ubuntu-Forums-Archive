---
title: "Kernel panic - not syncing --- error causing system to hang"
date: 2014-10-28
forum: General Help
---

### Post by MorneDJ on 2014-10-28
I just installed Ubuntu Server 14.04.1. New HP Microserver. I selected the it to install a Samba server as I will be using this as a file server. This is the process I followed (I boot from a Flash drive):

After installation I installed Webmin
CTRL+ALT+DELETE to restart.

Installed RAID capability (sudo apt-get update, sudo apt-get install openssh-server mdadm perl openssl samba)
Selected "No configuration" when prompted under Postfix Configuration
CTRL+ALT+DELETE to restart.

Move temp & log folders to RAM and configure for less IO to flash
In “sudo nano /etc/sysctl.conf” added “vm.swappiness=10” at the end of the file and saved.
Open the /fstab file and change UUID=559c5376-7cc2-441d-bd31-27b901fb6928  /boot ext2  noatime,defaults 0     2
Added this to end of file. This will force the system to keep temp and log files in memory, thus limiting writes to flash disk.
tmpfs      /var/log    tmpfs        defaults           0    0                 
tmpfs      /tmp          tmpfs        defaults           0    0
tmpfs      /var/tmp  tmpfs        defaults           0    0
 
Opened the grub configuration file and change the line below:
GRUB_CMDLINE_LINUX="elevator=noop quiet"    

Restart
 
Edited /etc/network/interfaces to manually Set IP address

All to this point works 100%

Entered Webmin
Added Disks -> RAID
"Hardware" -> "Linux RAID"
Select RAID 10 - "Create RAID device"
"Force init of RAID" and then "Create".

That was yesterday. 

It hung somewhere during the rebuild.
Hard restart this morning. 
The rebuild (using 4x 3TB HDDs) was at 6%.
Retried.
While rebuilding I clicked on Create filesystem of type: (impatient, why must it rebuild the drives, it is empty ?).
Crash. See screenshot. 
[IMG]http://www.menco.co.za/images/KernelIssue.jpg[/IMG]

Hard restart. Realized not to do that again. 
Leave to rebuild. Get back. Dead again. Swore very loudly.
Nothing in /var/logs that can help.
Search net. Got a few reports in this matter, cannot see to find a fix. 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/794117](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/794117)
Installed apport and linux-crashdump to try and capture the issue when it happens again.

Would it help to reformat and reinstall ?

I do not know alot about Linux, what I have done is based on a few battles, various posts and lots of time on the net. I will slowly learning.

---

### Post by MorneDJ on 2014-10-29
OK, I patiently waited for the rebuilding of the RAID 10 system, and it was finished when I got to work this morning. PC still standing. Raid Status [COLOR=#00ff00]clean [/COLOR](in green writing). Tried to create the file system, gave error and PC hung like a paint on a wall. Dead.

Photo showing image/writing on screen.

[IMG]http://www.menco.co.za/images/KernelIssue2.jpg[/IMG]

Naturally there is nothing under the logs that I can use, or post. Could it be one of the hard drives ?

Trying to recreate the file system (now the Status is : [COLOR=#ff0000]clean, resyncing (1%, 478 min)[/COLOR])

[TABLE="class: ui_table, width: 333"]
[TR]
[TD]**RAID device options**[/TD]
[/TR]
[TR="class: ui_table_body"]
[TD="colspan: 1"][TABLE="width: 100%"]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, align: right"]**Device file**[/TD]
[TD="class: ui_form_value, colspan: 1"]/dev/md0[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, align: right"]**RAID level**[/TD]
[TD="class: ui_form_value, colspan: 1"]RAID10 (Striped and Mirrored)[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, align: right"]**Filesystem status**[/TD]
[TD="class: ui_form_value, colspan: 1"]Active but not mounted[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, align: right"]**Usable size**[/TD]
[TD="class: ui_form_value, colspan: 1"]5860004864 blocks (5.46 TB)[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, align: right"]**Persistent superblock?**[/TD]
[TD="class: ui_form_value, colspan: 1"]Yes[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, align: right"]**Layout**[/TD]
[TD="class: ui_form_value, colspan: 1"]near=2[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, align: right"]**Chunk size**[/TD]
[TD="class: ui_form_value, colspan: 1"]512 kB[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, align: right"]**RAID status**[/TD]
[TD="class: ui_form_value, colspan: 1"]clean, resyncing[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, align: right"]**Rebuilding progress**[/TD]
[TD="class: ui_form_value, colspan: 1"]2 % (469.5 min, 198 MB/s)[/TD]
[/TR]
[TR="class: ui_form_pair"]
[TD="class: ui_form_label, align: right"]**Partitions in RAID**[/TD]
[TD="class: ui_form_value, colspan: 1"]SATA device A partition 1 
SATA device B partition 1 
SATA device C partition 2 
SATA device D partition 2 [/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

[COLOR=#393939][FONT=arial]Executing command partprobe ; mkfs -t ext3 -q /dev/md0 ..[/FONT][/COLOR]
Error: /dev/md0: unrecognised disk label

Get that error.

PC hangs ....

Same error as first image. First line reads:
> [    748.031670]  general protection fault: 0000  [#1]  SMP


Going to reformat and reinstall to see. Please, any ideas ?

---

### Post by tgalati4 on 2014-10-29
Check your log files in /var/log.

Boot from a LiveUSB stick, not your custom flash stick.  Run memtest for several cycles--make sure your RAM works.  Then install *cpuburn* and run several instances to load up the cpu for several hours.  Make sure the processors are OK.  

Then get a small SSD and perform a normal server installation to it.  Don't use a flash stick.  Run that for several weeks.

If your system is stable and works, then you can ask yourself, is it worth trashing a working system to run off of a flash drive?

---

### Post by MorneDJ on 2014-10-30
Cool. I am managing to run mke2fs -cc /dev/md0 withing it crashing. I previously run in via webmin. When this is finished I will do a memtest and cpuburn. I am also starting to think that the mememry may not be perfect ...

---

