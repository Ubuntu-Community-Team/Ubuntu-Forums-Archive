---
title: "Can't Access Data Partition (Unknown in GParted)"
date: 2016-04-23
forum: General Help
---

### Post by AnggaRifandi on 2016-04-23
Hi Community,

I have several partitions on my hard disk:
[LIST]
[*]/dev/sda1 (Linux Swap) 
[*]/dev/sda2 (/) 
[*]/dev/sda3 (Extended) 
[*]/dev/sda5 (/home) 
[/LIST]

Because I have a problem during upgrading Lubuntu I have a plan to reinstall Lubuntu in  **/dev/sda2**.

Before reinstall Lubuntu in **/dev/sda2** I tried to resize the size because it's to big (from 32 GB to 25 GB) and try to move the free space (7 GB) to **/dev/sda5** using GParted.

Everything looks fine until GParted stop working during the process (move the free space to /dev/sda5). When I tried to access it again the /dev/sda5 is marked as Unknown in GParted.

All my Photos, Documents and files in /dev/sda5 :(

I have tried TestDisk but have no clue how to fix this problem.

Anyone have similar experiences or know how to fix it? :confused:

---

