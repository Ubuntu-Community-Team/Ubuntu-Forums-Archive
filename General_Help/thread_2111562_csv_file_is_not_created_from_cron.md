---
title: "csv file is not created from cron"
date: 2013-02-02
forum: General Help
---

### Post by devendram on 2013-02-02
Hi,
     I have created a php file which generates csv file and saves file in folder csvfilefolder. Csv file is created when I run php file from browser. Csv file is also created when I run php file from command line with command /usr/bin/php generatecsv.php.

Command  /usr/bin/php generatecsv.php has been placed in crontab. Cron executes file generatecsv.php but csv file is not created. It is known that cron executes file generatecsv.php because I have used some code to update log file. The only problem is that csv file has not been created. Its so weird. Please help.

Kind Regards,
Devendra

---

### Post by prodigy_ on 2013-02-02
Cron runs in its own environment and usually this is the cause of issues. If you enable debugging in the script and redirect all output to a file it may help you understand what's actually happening.

---

