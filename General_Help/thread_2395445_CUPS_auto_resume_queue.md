---
title: "CUPS auto resume queue"
date: 2018-07-02
forum: General Help
---

### Post by john.lockwood on 2018-07-02
I am having problems with one print queue on our CUPS server in particular regularly pausing itself with the message 'Unable to add document to print job'. The printer in question is a Konica Minolta C284e, I added it as as an IPP queue as a PostSCript printer. We have a second literally identical printer configured identically, only one seems to have this problem.

So the fact it keeps pausing itself is one issue but not specifically what this post is about. Having this problem I looked for a way to automate resuming the print queue, I then found this page - [https://linuxgazette.net/147/misc/lg/2_cent_tip__automatically_reenabling_cups_printer_queues.html](https://linuxgazette.net/147/misc/lg/2_cent_tip__automatically_reenabling_cups_printer_queues.html)

This script when run *manually* works, that is it finds which queue is paused and *successfully* resumes it.

Note: Yes this means that any jobs stuck in the queue do then get printed.

Unfortunately even though I have added this script as a crontab job for the root account and I can see from the /var/log/syslog that the script is indeed being run, when run automatically this way it fails to resume the queue. Here are some entries from the log

[COLOR=#000000][FONT=Menlo]Jul  2 09:50:01 papercut-lon root: Executing [COLOR=#c33720]**Printer**[/COLOR] Resume script[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul  2 10:00:01 papercut-lon root: Executing [COLOR=#c33720]**Printer**[/COLOR] Resume script[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul  2 10:10:01 papercut-lon root: Executing [COLOR=#c33720]**Printer**[/COLOR] Resume script[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul  2 10:20:01 papercut-lon root: Executing [COLOR=#c33720]**Printer**[/COLOR] Resume script[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul  2 10:20:02 papercut-lon root: [COLOR=#c33720]**Printer**[/COLOR] Konica_Minolta_C284e_2 is stopped[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul  2 10:20:02 papercut-lon root: [COLOR=#c33720]**Printer**[/COLOR] Konica_Minolta_C284e_2 has been enabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul  2 10:30:01 papercut-lon root: Executing [COLOR=#c33720]**Printer**[/COLOR] Resume script[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul  2 10:30:02 papercut-lon root: [COLOR=#c33720]**Printer**[/COLOR] Konica_Minolta_C284e_2 is stopped[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul  2 10:30:02 papercut-lon root: [COLOR=#c33720]**Printer**[/COLOR] Konica_Minolta_C284e_2 has been enabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul  2 10:40:01 papercut-lon root: Executing [COLOR=#c33720]**Printer**[/COLOR] Resume script[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul  2 10:40:03 papercut-lon root: [COLOR=#c33720]**Printer**[/COLOR] Konica_Minolta_C284e_2 is stopped[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Jul  2 10:40:03 papercut-lon root: [COLOR=#c33720]**Printer**[/COLOR] Konica_Minolta_C284e_2 has been enabled.[/FONT][/COLOR]


As you can see, the queue got paused between 10:10am and 10:20am, it then tried to resume the queue at 10:20, 10:30 and 10:40 and failed each time. I then manually ran the script after 10:40am and that worked because I could see in the CUPS web interface this worked and the two stuck jobs started printing.

Based on a suggestion I found I tried modifying the script to have full file paths for using each executable just in case via cron they were not found in the environment file paths, this made no difference.

So, anyone know why this script in cron will not work properly? Anyone a solution?

As a bonus anyone and suggestions why the queue keeps getting paused this way?

---

### Post by rob-on-earth on 2018-11-08
I have a similar issue with a Toshiba e-STUDIO287CS multi functional printer but the pausing happens quite infrequently (once a week-ish) with no obvious cause.

I edited the script you linked to and this works for me.

```
#!/bin/sh#
# Check if a printer queue is disabled and reenable it.


DISABLED=$(/usr/bin/lpstat -t | grep disabled | awk '{ print $2; }')


for PRINTER in $DISABLED
do
        /usr/bin/logger "Printer $PRINTER is stopped"
        /usr/sbin/cupsenable $PRINTER && /usr/bin/logger "Printer $PRINTER has been enabled."
done
```

I deliberately paused the printer in the web interface and as soon as CRON ran the script it resumed.

FYI I removed the cupsenable -h parameter as this machine is the print server and spool.

Note: the paths are correct for my Raspberry Pi running Raspbian, YMMV

---

### Post by john.lockwood on 2018-11-09
Thanks for the reply @rob-on-earth

I solved the real problem - the cause of it repeatedly pausing queues. My original setup had the clients printing via IPP to the CUPS server and the CUPS server then printing to the actual printers via IPP as well. When I changed it so the clients still printed to the CUPS server via IPP but the CUPS server used RAW aka Socket to print to the actual printers the problems stopped, it also became a lot faster.

---

