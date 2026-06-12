---
title: "Assistance : Partimage Batch To Cron"
date: 2007-08-06
forum: General Help
---

### Post by indytim on 2007-08-06
I have a small bash script which I put together to run a partimage archive of a partition.  The script is an executable and it is located in /usr/local/bin.  When I run the script from the terminal it runs fine.  When I submit it for a scheduled Cron event (via KCron), it appears in the crontab but does not run.  Looking for any feedback to get this puppy running in a cron job (have multiple other partitions that I want to do the same treatment with).

Here's a copy of the bash command script

[PHP]#!/bin/bash  

of=/media/LxBackup/HD-BU/sda9-$(date +%Y-%m-%d).gz
#partimage -z1 -om -d -f3 -B=image_file save /dev/sda9 $of
partimage -z1 -om -d -f3 -b -g0 save /dev/sda9 $of
[/PHP]

Many Thanks,

IndyTim

---

