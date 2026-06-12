---
title: "Backing-up Android Device"
date: 2015-10-06
forum: General Help
---

### Post by BJones007 on 2015-10-06
I'm trying to backup my data, but each time the command line says I should unlock my device it 

1. Doesn't show anything on the device and 
2. The command line jumps to next line as if to say the command was complete. The command in question is this

```
./adb backup -apk -shared -all -f ~/Backups/N5/fullbackup-20150510.ab
```

I posted this in the Android Community section on Google Plus, but I haven't gotten any help so far. I'm using a Nexus 5 with Android 6.0 Preview 3&#65279; and I added a photo at the end of this post with all the info I think y'all might need to help.

Any and every help is appreciated. Cheers

[IMG]https://lh3.googleusercontent.com/-Sq_2qKr_TcQ/VhMx749QoPI/AAAAAAAAFZw/MBHPT832lYM/w346-h203/2015%2B-%2B1[/IMG]

---

### Post by superkid333 on 2016-05-04
I know no one has replied to this, but I am experiencing the same exact issue. 

I upgraded to Marshmallow 6.0. I want to use ADB to backup my device. It goes to the "Now unlock your device and confirm the backup operation" and then nothing happens. My device does not ask for a backup.

---

### Post by sirda on 2016-11-22
Try adding \ between arguments, like this:

adb backup -apk\ -shared\ -all\

It worked for me.

---

### Post by kingneutron on 2016-12-01
--Attached is the script that I use to backup Android, with references. **IMPORTANT**: The Android device should have USB debugging enabled and be attached as an MTP device, you may have to change this in settings.  Also you should edit the script before running to define your destination directory for the backup.

( Recommended to run this as root )
```

#!/bin/bash

# REF: http://linuxconfig.org/how-to-backup-htc-android-phone-using-linux-system-command-line-tools
# REQUIRES adb (pkg android-tools-adb

# xxx EDIT ME - destination dir
cd /zredpool2/dvcompr && mkdir -pv androidbkp
cd androidbkp || exit 99;

ls -alh

bkpdate=`date +%Y%m%d`
bkpfname="bkp-android---$bkpdate--running-ok"

[ "$1" = "nexus7" ] && bkpfname='bkp-android--nexus7-'$bkpdate'--running-ok'
[ "$1" = "n7" ] && bkpfname='bkp-android--nexus7-'$bkpdate'--running-ok'

echo "$PWD/$bkpfname"

adb start-server
adb devices

#time adb backup -f $bkpfname.adb -apk -all
# REF: http://www.techrepublic.com/article/how-to-create-a-full-backup-of-your-android-device-without-root/
if [ "$1" = "n7" ]; then
# REF: https://www.reddit.com/r/nexus6/comments/3nyg8g/adb_backup_issues/
  time adb backup -f $bkpfname.adb -all
else
  time adb backup -apk -shared -all -f $bkpfname.adb
fi

ls -alh; pwd

exit;

```

---

