---
title: "Bash Script - dynamic Filename"
date: 2016-05-24
forum: General Help
---

### Post by Harpz on 2016-05-24
I have a simple bash script that pulls the SMART data for all the drives in my server and picks out the key parts.

It stores the info in a temp file in the desired format and then uses that temp file as the emails body, which i get once a week.

I'm trying to figure out how to get the same script to instead of putting all this info together in 1 file but put it into seperate files.

IE.. smart report for /dev/sda goes into a file called 20160524_sda the report for /dev/sdb goes into a file called 20160524_sda and so on.

How do i get the filename to change its sdX part with each report?

---

### Post by TheFu on 2016-05-24
Pull the SMART data separately for each disk device.

```
DATE=`date +'%Y%m%d-%H%M%S'`
OUTPUT_SDA=/tmp/SMART-$DATE-sda
OUTPUT_SDB=/tmp/SMART-$DATE-sdb

/usr/sbin/smartctl /dev/sda  2>&1 >  $OUTPUT_SDA
/usr/sbin/smartctl /dev/sdb  2>&1 >  $OUTPUT_SDB
```

If you are really lazy, you can use arrays in bash - I'd have to look that up. The ABSG is an amazing resource.  "ABSG bash" will find it.
But it probably isn't worth overthinking.  If I had 500 servers to do this with, I'd have 1 script and 1 config file. The script would be the same, the config file would list the devices for each server and perhaps the output filenames.

BTW, I include this sort of data, along with a daily lshw, parted -l and a few other little config utils, in my backups for every system.

---

### Post by Harpz on 2016-05-25
Thanks for the reply,

My first though was to do exactly what you said about, pulling the individual reports for each drives, i just wondered if there was another way.

In the end i came up with the following, It doesn't look like the pretty code i see on here but it does the job and i must admit Im happy with it considering i know very little about bash and coding in general.

```
#! /bin/bash

# binarys
DF_BIN="/bin/df"
SMART_BIN="/usr/sbin/smartctl"
MUTT_BIN="/usr/bin/mutt"


# options
TMPLOC="/home/mike/.tmp/"
DATE=$(date +"%Y%m%d")
REPORT="SMART_Report"
EMAIL="email@gmail.com"
SMARTSUM="/home/mike/.tmp/smartsum"

# temp report locations
SDA_RPT="$TMPLOC$DATE"_"sda"_"$REPORT.log"
SDB_RPT="$TMPLOC$DATE"_"sdb"_"$REPORT.log"
SDC_RPT="$TMPLOC$DATE"_"sdc"_"$REPORT.log"
SDD_RPT="$TMPLOC$DATE"_"sdd"_"$REPORT.log"
SDE_RPT="$TMPLOC$DATE"_"sde"_"$REPORT.log"
SDF_RPT="$TMPLOC$DATE"_"sdf"_"$REPORT.log"
SDG_RPT="$TMPLOC$DATE"_"sdg"_"$REPORT.log"
SDH_RPT="$TMPLOC$DATE"_"sdh"_"$REPORT.log"
SDI_RPT="$TMPLOC$DATE"_"sdi"_"$REPORT.log"
SDJ_RPT="$TMPLOC$DATE"_"sdj"_"$REPORT.log"
SDK_RPT="$TMPLOC$DATE"_"sdk"_"$REPORT.log"
SDL_RPT="$TMPLOC$DATE"_"sdl"_"$REPORT.log"

# SMART summary report
echo "Summary SMART Report Generated on: `date`" >>$SMARTSUM
for disk in {a..l}
do
# Drive / Mount point
echo "--------------------------------------------------------------------------------------------------------" >>$SMARTSUM
$DF_BIN -h | egrep /dev/sd$disk | awk '{print $1, "- " $6}' >>$SMARTSUM
echo "--------------------------------------------------------------------------------------------------------" >>$SMARTSUM
$SMART_BIN -a /dev/sd$disk | egrep 'Model Family|Device Model|Serial Number|User Capacity' | awk '{print $3,$4,$5,$6,$7,$8,$9,$10}' >>$SMARTSUM
echo "--------------------------------------------------------------------------------------------------------" >>$SMARTSUM
# Headings
printf " %-4s %-23s %-6s %-6s %-7s %-10s \n" "ID#" "ATTRIBUTE_NAME" "VALUE" "WORST" "THRESH" "RAW_VALUE" >>$SMARTSUM
# Pull basic data from the smart report
$SMART_BIN -a /dev/sd$disk | egrep 'Current_Pending_Sector|Reallocated_Sector_Ct|Power_On_Hours|Load_Cycle_Count|Total_Pending_Sectors' | awk '{printf " %-4s %-23s %-6s %-6s %-7s %-12s \n", $1, $2, $4, $5, $6, $10 }' >>$SMARTSUM
echo " " >>$SMARTSUM
done

# Geenerate reports for individual drives
$SMART_BIN -a /dev/sda > $SDA_RPT
$SMART_BIN -a /dev/sdb > $SDB_RPT
$SMART_BIN -a /dev/sdc > $SDC_RPT
$SMART_BIN -a /dev/sdd > $SDD_RPT
$SMART_BIN -a /dev/sde > $SDE_RPT
$SMART_BIN -a /dev/sdf > $SDF_RPT
$SMART_BIN -a /dev/sdg > $SDG_RPT
$SMART_BIN -a /dev/sdh > $SDH_RPT
$SMART_BIN -a /dev/sdi > $SDI_RPT
$SMART_BIN -a /dev/sdj > $SDJ_RPT
$SMART_BIN -a /dev/sdk > $SDK_RPT
$SMART_BIN -a /dev/sdl > $SDL_RPT

# Send final reports
$MUTT_BIN -s "Altair - S.M.A.R.T Data for drives in Server." -a $SDA_RPT -a $SDB_RPT -a $SDC_RPT -a $SDD_RPT -a $SDE_RPT -a $SDF_RPT -a $SDG_RPT -a $SDH_RPT -a $SDI_RPT -a $SDJ_RPT -a $SDK_RPT -a $SDL_RPT -- $EMAIL < $SMARTSUM

rm -f $TMPLOC$DATE*
rm -f $SMARTSUM

exit
```

I will have a look at arrays and thank you for the "ABSG bash" resource, I have a pdf of it now and will start working my way thought it learning :) this little project has got me really interested in bash scripts and what i can do with them.

---

### Post by TheFu on 2016-05-25
Might want to consider other scripting languages which have more powerful and nicer syntax.  Python is popular these days. I use perl.  Basically, if a script gets over about 2 pgs long, I'll switch from bash to perl because it has better looping, arrays, hashes, regex handling, and readability.  I prefer the whitespace control in perl - much more readable, to me.

But there are always 500 ways to solve any scripting problem and whatever works is usually just fine, even if it is ugly.  I don't have any better answer than what you've done above, thought maybe a loop for the drive device names would be cleaner and maybe using a function, since each drive has the same processing? Not a big deal, either way.

---

### Post by steeldriver on 2016-05-25
I don't really understand what your hang up is here - you appear to be looping over disks using a variable already:

```

for disk in {a..l}
do ...

```

Why not simply do the same for the individual reports, appending variable $disk to the filename?

---

### Post by Harpz on 2016-05-25
> **steeldriver said:**
> I don't really understand what your hang up is here - you appear to be looping over disks using a variable already:

Why not simply do the same for the individual reports, appending variable $disk to the filename?

If I'm honest i haven't figured out what you mean by this yet still learning my way around bash but learning something new every day :)

---

### Post by Harpz on 2016-05-25
> **TheFu said:**
> Pull the SMART data separately for each disk device.

BTW, I include this sort of data, along with a daily lshw, parted -l and a few other little config utils, in my backups for every system.

You said you back up the above any chance you could explain the reason behind it please, still learning my way around this server and what i need to backup in case of a crash.

---

### Post by steeldriver on 2016-05-25
> **Harpz said:**
> If I'm honest i haven't figured out what you mean by this yet still learning my way around bash but learning something new every day :)

I meant something like

```

for disk in {a..l}
do
# Geenerate reports for individual drives
$SMART_BIN -a /dev/sd**$disk** > "${TMPLOC}${DATE}"_"sda**${disk}**"_"${REPORT}.log"
done

```

or (perhaps easier to read)

```

for disk in **sd**{a..l}
do
# Geenerate reports for individual drives
$SMART_BIN -a /dev/**$disk** > "${TMPLOC}${DATE}_**${disk}**_${REPORT}.log"
done

```

---

### Post by TheFu on 2016-05-25
> **Harpz said:**
> You said you back up the above any chance you could explain the reason behind it please, still learning my way around this server and what i need to backup in case of a crash.

There are many different ways to perform backups.
* images
* data only
* settings, data, list of installed packages, and system config

My RPO and RTO requirements are 24 hrs and 45 min, so I need to have daily backups and be able to restore those to a working system within 45 minutes.  Also have to limit downtime to a few minutes daily - of course ZERO downtime would be best. Need 60-120 days of backups, which uses a little more storage, but not as much as you'd think, provided image-based backups are avoided.

So ... with all those requirements, backing up data-only isn't sufficient.  That leaves only 1 solution - backup everything necessary to recreate the system, including data and all programs + settings + config within 45 minutes.  If the system configuration isn't saved, how can I possibly recreate it quickly?  HDDs fail.  Partitions become corrupt.   Sometimes USB disks and other failed HW disappears.  Without capturing daily config changes, I'd have no way to know when that happened if it didn't impact the primary system running.  

I've posted about backups here probably 20 times.  My signature has links to other resources that you can review.  There are lots of ways to perform backups, so you'll need to find the way that meets your RTO/RPO requirements.  I cannot imagine a method that is as efficient with time to backup and time to restore as the method I'm using while still using minimal storage.   For example, the email front-end server here is high-risk, so 120 days of backups are retained.  But since it doesn't actually have **any** data on it, it is purely settings and configuration - that means all that backup data for all those days is just 100MB.  

My primary desktop has 60 days of backups.  Let me pull the size information.
```
# rdiff-backup --list-increment-sizes /Backups/icarus
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Wed May 25 01:15:11 2016         5.37 GB           5.37 GB   (current mirror)
Tue May 24 01:15:08 2016         9.09 MB           5.38 GB
....
Mon Mar 28 01:15:06 2016         8.20 MB           6.63 GB
Sun Mar 27 01:15:07 2016         9.27 MB           6.64 GB

``` .

A summary script gets emailed every morning so it is easy to see any failures.  That happens about once a year for 1 box.

---

### Post by Harpz on 2016-05-26
Wow now i see it in front of me i cant believe i didn't think of that, I had a play with something similar but was having a mental block and over thinking it, guess that comes with experience, loads to learn.

Thank you steeldriver and thank you TheFu i look at the links in your sig.

---

