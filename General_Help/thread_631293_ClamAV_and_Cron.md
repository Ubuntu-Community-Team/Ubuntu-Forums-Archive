---
title: "ClamAV and Cron"
date: 2007-12-04
forum: General Help
---

### Post by OMRebel on 2007-12-04
I have a quick question.  How do I setup a Cron job that will have ClamAV scan a directory (/var/www/phpbb/files) every 10 minutes?  

Or, is there a way that I can setup a scan that will run only if a new file is created in that folder?

Thanks.

---

### Post by OMRebel on 2007-12-04
bump.

---

### Post by phylae on 2007-12-15
I am NOT an expert, so use this advice only at your own risk. I don't know how to check for viruses only if things change.

Here is my setup for clamav


Install
```
sudo apt-get install clamav
```

update virus definitions
```
sudo freshclam
```

Create the file /usr/local/bin/virus_scan.sh
```

#!/bin/bash
# ----------------------------------------------------------------------
# Virus scan with ClamAV
# ----------------------------------------------------------------------

# Disabling PATH improves the security of the script
unset PATH

# Declare the variables
ECHO=/bin/echo;
DATE=/bin/date;
FRESHCLAM=/usr/bin/freshclam;
CLAMSCAN=/usr/bin/clamscan;
LOG_FILE=/home/INSERT_USER_NAME/clamscan.log;
SCAN_FOLDER=/;

# Start the log entry
$ECHO Complete system virus scan starting >> $LOG_FILE;
$DATE >> $LOG_FILE;
$ECHO \* >> $LOG_FILE;
# Update Virus definitions
$FRESHCLAM >> $LOG_FILE;

# Run the scan
$CLAMSCAN -ri $SCAN_FOLDER >> $LOG_FILE;

# Finish the log entry
$ECHO \* >> $LOG_FILE;
$ECHO Complete system virus scan finished >> $LOG_FILE;
$DATE >> $LOG_FILE;
$ECHO \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* >> $LOG_FILE;


```

Set permissions to be root accessible/executable only
```

sudo chown root /usr/local/bin/virus_scan.sh
sudo chmod u=rwx /usr/local/bin/virus_scan.sh
sudo chmod go= /usr/local/bin/virus_scan.sh

```

Add the following to /etc/crontab
```

20 3    * * *   root    /usr/local/bin/virus_scan.sh

```

I have it set up to run every day at 3:20 AM. If you want to run it every 10 minutes, you can do something like this:
```

05 *    * * *   root    /usr/local/bin/virus_scan.sh
15 *    * * *   root    /usr/local/bin/virus_scan.sh
25 *    * * *   root    /usr/local/bin/virus_scan.sh
35 *    * * *   root    /usr/local/bin/virus_scan.sh
45 *    * * *   root    /usr/local/bin/virus_scan.sh
55 *    * * *   root    /usr/local/bin/virus_scan.sh

```

Don't forget to update the values of LOG_FILE and SCAN_FOLDER!

Note: With this setup, you need to manually check the output written to the log file. I haven't figured out how to have it email/notify me when things go wrong. You might find the --beep option of clamscan useful.

I hope this helps you.

---

