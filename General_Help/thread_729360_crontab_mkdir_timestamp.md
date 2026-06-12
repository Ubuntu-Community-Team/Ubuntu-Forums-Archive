---
title: "crontab mkdir timestamp"
date: 2008-03-19
forum: General Help
---

### Post by meg23 on 2008-03-19
I am trying to get crontab to create a directory with a timestamp everyday. This is the command I scheduled into crontab: 

[B]mkdir /home/bob/Desktop/web-station_"`date +%m-%d-%Y`"
[/B]
This command works fine in the terminal and displays:

**web-station_3-19-2008**

 However, in crontab, the command does not execute.  

When I remove the -"`date +%m-%d-%Y`" from the command, crontab creates the file properly according to the schedule without the segment. 

**web-station**

Why can't crontab execute a file that is executable in the terminal?

Is there a better way of creating a directory with a timestamp using crontab?

Could it be the segment  "`date +%m-%d-%Y`" contains special crontab characters?

Thanks in Advance, MG

---

### Post by pointone on 2008-03-19
cron jobs are run in a different environment than the default shell. You should always use full pathnames (i.e. "/usr/bin/date" instead of just "date"). Also, try running the command through env, as in "/usr/bin/env <date command>".

---

### Post by meg23 on 2008-03-19
I tried the following script to no avail. 

mkdir .......webstream_"`usr/bin/date +%m-%d-%Y`"

However, navigated to the directory and "date" is not present. 

Do I need to create an executable script for "date"? It works in the terminal.

---

### Post by meg23 on 2008-03-19
Here is a solution based on what I think pointeone was suggesting :

Create an executable file in your home folder file.sh.

Open file.sh and write script.

#!/bin/bash
mkdir /home/yourusername/webstream_"`date +%m-%d-%Y`"
exit

From crontab, enter only the command ./file.sh

This is probably a fairly simple solution, however it is very useful. For anyone using streamripper with crontab scheduling, this script with your parameters can help you organize your recordings. 

Thanks, MG

---

