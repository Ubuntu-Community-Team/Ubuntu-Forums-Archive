---
title: "Batch Script not working correctly via Crontab"
date: 2013-08-03
forum: General Help
---

### Post by Fascination on 2013-08-03
Hello everyone!

**EDIT: Just tried scheduling the script again just now and closed my session and it worked successfully but its not writing to the log file. This morning the files failed to upload for whatever reason but as it hadn't captured to the log I was unsure of what had happened. The problem appears more to be the &> not piping contents to the log file!**

**EDIT 2: Two steps forward, one step back. Changed the crontab to read "/home/fasc/work/stuff/st_transfer/transfer.sh >csvtransfer.txt 2>&1" which now correctly outputs what I want to a text file .... just now the FTP part isn't uploading. Pretty sure this original post is now resolved.**

I've created a batch script that wget's 4 files from a server then uploads them to an FTP server before deleting the saved files locally. If I run this script on its own (included below) it works a treat and if I schedule it via crontab it works great. However, if I then try to capture the output to a log file it works when I do it manually but when I schedule the task via Crontab it doesn't appear to run (no contents saved in the log file).

```
#!/bin/bash

vf_details="file1_"`eval date +%Y%m%d -d "yesterday"`".csv"
vf_totals="file2_"`eval date +%Y%m%d -d "yesterday"`".csv"
vf_bet="file3_"`eval date +%Y%m%d -d "yesterday"`".csv"
vf_deposit="file4_"`eval date +%Y%m%d -d "yesterday"`".csv"

echo -e "https://webaddress/$vf_details\nhttps://webaddress/$vf_totals\nhttps://webaddress/$vf_bet\nhttps://webaddress/$vf_deposit" >> toget.csv

wget --user=theusername --password='thepassword' -i toget.csv

curl -u 2ndusername:2ndpassword -T "{$vf_details,$vf_totals,$vf_bet,$vf_deposit}" ftp://888.888.888.888

rm *.csv
```

And my crontab is as follows;

```
15 07 * * * /home/fasc/work/stuff/st_transfer/transfer.sh &> /home/fasc/work/stuff/st_transfer/csv_transfer.log
30 07 * * * echo "Heres the completed log file." | mutt -a "/home/fasc/work/stuff/st_transfer/csv_transfer.log" -s "CSV Transfer" -- me@myaddress.com

```

Really scratching my head over this one, I can't understand how it works happily when I run it manually but as soon as I schedule the same command it fails to run? Any help given would be greatly appreciated, thank you!

---

### Post by JKyleOKC on 2013-08-03
Most cron jobs run as root, not as your logged-in user; if this is what is happening for you, then your four $vf* variables in the script need full pathspecs, not just the basic filenames, for it to work.

However it's possible to have cron jobs run as specific users rather than as root. We need more details about exactly how you are doing the scheduling to tell which is the case here.

---

