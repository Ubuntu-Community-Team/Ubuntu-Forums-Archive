---
title: "[B] Partition error: cant resize / cant boot windows Ubuntu7.04 [/B]"
date: 2007-06-10
forum: General Help
---

### Post by Labrada001 on 2007-06-10
Im a new Ubuntu user. I was installing Ubuntu7.04, on my uncles laptop: P4 2.8Ghz, 1G of Ram and 100G hard drive.
In the process I made a mistake and chose to use entire disk. The hard drive was repartitioned from 90G to 100G. I cant resize hard drive to make space for Ubuntu. Also, now the computer does not reboot to windows. I would like to rescue the windows install and reinstall Ubuntu. Can I get windows to boot again? Is there a partitioning software that I can use to correct this error? 

This is the error:
[COLOR="DarkRed"][SIZE="3"]
[!!] Partition Disks
The resize operation is impossible

Because of an unknown reason it is impossible to resize this partition.

Check /var/log/syslog or see virtual console 4 the details.[/SIZE][/COLOR]

---

### Post by merlinus on 2007-06-10
If the partitioner fromatted your entire disk as ext3 (linux), then you will be hard-pressed to get anything back.

Hopefully you have back-ups of important data.

Try entering this in a terminal whilst ubuntu is running:

sudo fdisk -l

(the l is a lowercase L)

and post the results.

-merlin

---

