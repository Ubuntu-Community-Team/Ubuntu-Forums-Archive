---
title: "CRON Job Issues"
date: 2017-01-09
forum: General Help
---

### Post by elliotbeken on 2017-01-09
Hi All, 

I am having issues with running a CRON job that contains a few CURL commands.

The CURL commands are similar to:

curl -kG "https://10.0.9.37/esp/restapi.esp?type=config&action=show&key=LUFRPdfghdfgdgdgfgdg0MkxQWmlIT0JQeTJ$
curl -kG "https://10.0.10.37/esp/restapi.esp?type=config&action=show&key=LUFRPT1mOHU3V01NXJ0MkxQWmlIT0JQeTJ$
curl -kG "https://10.0.10.37/esp/restapi.esp?type=config&action=show&key=LUFRPT1mOHU3V0fghfhfhfhhf

This is saved in a file called: backups_script.sh (is executable)

I have edited my cron -e with the following:
(runs at 16:44 every day)

44 16 * * * root /home/mike/backups_script.sh


If i run the file via this command it all works fine and as expected: ./backups_script.sh

What am i doing wrong?

Thanks

---

### Post by dragonfly41 on 2017-01-09
There should be a closing quote " at end of each string.

---

### Post by elliotbeken on 2017-01-09
I assume to mean to the backups_scripts.sh strings? I have added " to the end like so however no luck:

[COLOR=#000000]curl -kG "https://10.0.9.37/esp/restapi.esp?type=config&action=show&key=LUFRPdfghd fgdgdgfgdg0MkxQWmlIT0JQeTJ$"[/COLOR]
[COLOR=#000000]curl -kG "https://10.0.10.37/esp/restapi.esp?type=config&action=show&key=LUFRPT1mOH U3V01NXJ0MkxQWmlIT0JQeTJ$"[/COLOR]
[COLOR=#000000]curl -kG "https://10.0.10.37/esp/restapi.esp?type=config&action=show&key=LUFRPT1mOH U3V0fghfhfhfhhf"


[/COLOR]

---

### Post by dragonfly41 on 2017-01-09
And does adding && at end of line help?
```

[COLOR=#000000][COLOR=#000000]curl -kG "https://10.0.9.37/esp/restapi.esp?type=config&action=show&key=LUFRPdfghd fgdgdgfgdg0MkxQWmlIT0JQeTJ$" &&[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]curl -kG "https://10.0.10.37/esp/restapi.esp?type=config&action=show&key=LUFRPT1mOH U3V01NXJ0MkxQWmlIT0JQeTJ$" &&[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]curl -kG "https://10.0.10.37/esp/restapi.esp?type=config&action=show&key=LUFRPT1mOH U3V0fghfhfhfhhf"

```[/COLOR][/COLOR]

---

### Post by ian-weisser on 2017-01-09
Are you copying those out of a terminal? The ending '$' often means there are more characters past the last column of the display....

How did you "edit my cron -e". Do you mean that you edited your root  crontab? Or do you mean that you edited your user crontab using the 'crontab -e' command?

If your user crontab, why does it have the word 'root' in it? You only specify a user in the root crontab.

Have you checked /var/log/syslog at the job time? Were there any messages about the job running? Or failing?

---

### Post by elliotbeken on 2017-01-09
I have moved this to crontab -e (not sudo crontab -e)

I get the following in /var/log/syslog:

Jan  9 17:56:01 Ubuntu-NTP01 CRON[30256]: (elliot) CMD (elliot /home/elliot/Palo_Script.sh)
Jan  9 17:56:02 Ubuntu-NTP01 postfix/pickup[9925]: 339D51208FB: uid=1000 from=<elliot>
Jan  9 17:56:02 Ubuntu-NTP01 postfix/cleanup[30259]: 339D51208FB: message-id=<20170109175602.339D51208FB@Ubuntu-NTP01>
Jan  9 17:56:02 Ubuntu-NTP01 postfix/qmgr[9926]: 339D51208FB: from=<elliot@Ubuntu-NTP01>, size=599, nrcpt=1 (queue active)
Jan  9 17:56:02 Ubuntu-NTP01 postfix/local[30261]: 339D51208FB: to=<elliot@Ubuntu-NTP01>, orig_to=<elliot>, relay=local, delay=0.25, delays=0.16/0.09/0/0, dsn=2.0.0, status=sent (delivered to mailbox)
Jan  9 17:56:02 Ubuntu-NTP01 postfix/qmgr[9926]: 339D51208FB: removed


I expect the script to download an name.xml file.

---

### Post by ian-weisser on 2017-01-09
Looks like the system is trying to email you something.

1) Fix your crontab to get rid of the user 'root'. You don't use that in a user crontab.
```
44 16 * * * **root** /home/mike/backups_script.sh     //OLD
44 16 * * * /home/mike/backups_script.sh          //NEW
```

Interestingly, crontab itself should have complained loudly about the error, and refused the entry. Grammar-checking is one purpose of the command.

2) Use redirection to log the error messages that the system is trying to email you.
```
44 16 * * * /home/mike/backups_script.sh **2>&1 /tmp/cron_log          // Edited to correct '&>' typo**
```

---

### Post by elliotbeken on 2017-01-09
> **ian-weisser said:**
> Looks like the system is trying to email you something.

1) Fix your crontab to get rid of the user 'root'. You don't use that in a user crontab.
```
44 16 * * * **root** /home/mike/backups_script.sh     //OLD
44 16 * * * /home/mike/backups_script.sh          //NEW
```

Interestingly, crontab itself should have complained loudly about the error, and refused the entry. Grammar-checking is one purpose of the command.

2) Use redirection to log the error messages that the system is trying to email you.
```
44 16 * * * /home/mike/backups_script.sh **2&>1 /tmp/cron_log**
```


Nope still nothing:(logs:
cat: /tmp/cron_log: No such file or directory

/tmp$ tail -f /var/log/syslog




Jan  9 20:29:01 Ubuntu-NTP01 cron[2955]: (elliot) RELOAD (crontabs/elliot)
Jan  9 20:29:01 Ubuntu-NTP01 CRON[18774]: (elliot) CMD (elliot /home/elliot/Palo_Script.sh 2&>1 /tmp/cron_log)
Jan  9 20:29:01 Ubuntu-NTP01 postfix/pickup[18600]: 91B8D12326A: uid=1000 from=<elliot>
Jan  9 20:29:01 Ubuntu-NTP01 postfix/cleanup[18779]: 91B8D12326A: message-id=<20170109202901.91B8D12326A@Ubuntu-NTP01>
Jan  9 20:29:01 Ubuntu-NTP01 postfix/qmgr[9926]: 91B8D12326A: from=<elliot@Ubuntu-NTP01>, size=625, nrcpt=1 (queue active)
Jan  9 20:29:01 Ubuntu-NTP01 postfix/local[18781]: 91B8D12326A: to=<elliot@Ubuntu-NTP01>, orig_to=<elliot>, relay=local, delay=0.09, delays=0.04/0.05/0/0, dsn=2.0.0, status=sent (delivered to mailbox)
Jan  9 20:29:01 Ubuntu-NTP01 postfix/qmgr[9926]: 91B8D12326A: removed
Jan  9 20:29:42 Ubuntu-NTP01 crontab[18816]: (elliot) BEGIN EDIT (elliot)
Jan  9 20:30:10 Ubuntu-NTP01 systemd[1]: Started Session 4760 of user elliot.
Jan  9 20:30:56 Ubuntu-NTP01 crontab[18816]: (elliot) END EDIT (elliot)




crontab -e:
29 20 * * * elliot /home/elliot/Palo_Script.sh 2&>1 /tmp/cron_log

---

### Post by chris354 on 2017-01-09
This might seem obvious, have you checked that mail box to find out what crontab is telling you? if you need to you can set up an alias for that mailbox to redirect it to a mailbox you have set up already. (see postfix documentation for that)

---

### Post by ian-weisser on 2017-01-09
> **elliotbeken said:**
> 
Jan  9 20:29:01 Ubuntu-NTP01 cron[2955]: (elliot) RELOAD (crontabs/elliot)
[...]
crontab -e:
29 20 * * * elliot /home/elliot/Palo_Script.sh 2>&1 /tmp/cron_log

You reloaded the crontab too late. 20:29:01 instead of 20:28:59 or earlier.
Cron wakes up at 0 seconds past each minute to check for crontabs to run. Then it goes back to sleep.
Like Cinderella, the stroke of the clock matters.

---

### Post by steeldriver on 2017-01-09
Shouldn't that redirect be
```

/home/elliot/Palo_Script.sh > /tmp/cron_log 2>&1

```

---

### Post by ian-weisser on 2017-01-09
Indeed. My apologies for the typo. Editing previous....

---

### Post by kevdog on 2017-01-10
Did you give your cron an environment?  Sometime cron jobs are funny.  They don't have a shell.

Here is an example of the top three lines of my frcontab file.  I think this is applicable to cron as well -- in fact I'm pretty sure it is except the 3rd line

SHELL=/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
!mail(false),bootrun(true),nice(7),serial

---

### Post by elliotbeken on 2017-01-10
still nothing:

Jan 10 12:40:01 Ubuntu-NTP01 cron[2955]: (elliot) RELOAD (crontabs/elliot)
Jan 10 12:41:01 Ubuntu-NTP01 CRON[21386]: (elliot) CMD (elliot /home/elliot/Palo_Script.sh 2&>1 /tmp/cron_log)
Jan 10 12:41:01 Ubuntu-NTP01 postfix/pickup[21352]: 823AA12326A: uid=1000 from=<elliot>
Jan 10 12:41:01 Ubuntu-NTP01 postfix/cleanup[21391]: 823AA12326A: message-id=<20170110124101.823AA12326A@Ubuntu-NTP01>
Jan 10 12:41:01 Ubuntu-NTP01 postfix/qmgr[9926]: 823AA12326A: from=<elliot@Ubuntu-NTP01>, size=656, nrcpt=1 (queue active)
Jan 10 12:41:01 Ubuntu-NTP01 postfix/local[21393]: 823AA12326A: to=<elliot@Ubuntu-NTP01>, orig_to=<elliot>, relay=local, delay=0.15, delays=0.1/0.05/0/0.01, dsn=2.0.0, status=sent (delivered to mailbox)
Jan 10 12:41:01 Ubuntu-NTP01 postfix/qmgr[9926]: 823AA12326A: removed
Jan 10 12:59:50 Ubuntu-NTP01 systemd[1]: Started Session 4781 of user elliot.

crontab -e:
41 12 * * * elliot /home/elliot/Palo_Script.sh 2&>1 /tmp/cron_log

/tmp/cron_log
Nothing!

---

### Post by steeldriver on 2017-01-10
Please change from
```

41 12 * * * elliot /home/elliot/Palo_Script.sh [COLOR=#ff0000]**2&>1 /tmp/cron_log**[/COLOR]

```
to
```

41 12 * * * elliot /home/elliot/Palo_Script.sh [COLOR=#0000ff]**> /tmp/cron_log 2>&1**[/COLOR]

```

---

### Post by elliotbeken on 2017-01-10
I have changed it to:
30 14 * * * elliot /home/elliot/Palo_Script.sh > /tmp/cron_log 2>&1


now in **/tmp/cron_log** i get the following:
/bin/sh: 1: elliot: not found


Where would the xlm files be downloaded to once successful? /home/elliot/?

---

### Post by steeldriver on 2017-01-10
Oops sorry I miseed that - in **crontabs**, the **user **field is not required - just

```

30 14 * * * /home/elliot/Palo_Script.sh > /tmp/cron_log 2>&1

```

---

### Post by elliotbeken on 2017-01-10
Thats better i am getting errors in the **/tmp/cron_log** but still not the desired output

**/home/elliot/Palo_Script.sh: 5: /home/elliot/Palo_Script.sh: cannot create device_1.xml &&**
**curl -kG [https://10.255.254.14/esp/restapi.esp?type=config:](https://10.255.254.14/esp/restapi.esp?type=config:) Directory nonexistent**
**/home/elliot/Palo_Script.sh: 7: /home/elliot/Palo_Script.sh: cannot create device_2.xml &&**
**curl -kG [https://192.168.19.46/esp/restapi.esp?type=config:](https://192.168.19.46/esp/restapi.esp?type=config:) Directory nonexistent**


device_2.xml is the file the CURL command is generating and should download.

---

### Post by ian-weisser on 2017-01-10
Egad. Sorry about making two cron mistakes in the same thread.
Now you know that it's running. Now you can see the stderr output.

You added quotes (") earlier to the curl command.
Are the quotes in the right place? Containing only the URL? 

You home directory is preserved by an environment variable. cron doe not have access to most of your login account's environment variables.
Use cURL's -o flag to specify the desired local path and filename, or specify the env vars in your script.

---

### Post by elliotbeken on 2017-01-11
This is what i have:

Palo_Backup.sh:
curl -kG "https://192.168.19.37/esp/restapi.esp?type=config&action=show&key=mdTNyTmfdgg5XSFVFZ0tFSFg4eGhVS0hlaUhzMzV0Y2Y4SlpvTT0=" > Device_1.xml" &&
curl -kG "https://192.168.19.38/esp/restapi.esp?type=config&action=show&key=3RmdTNyTmNVQdfgdfgdgd2eTFtd0srTfdgdgVS0hlaUhzMzV0Y2Y4SlpvTT0=" > Device_2.xml" &&
curl -kG "https://192.168.0.2/esp/restapi.esp?type=config&action=show&key=QXlkNVR1Qm5laEY0S0Ivd1ZWRms9bWYdfgdfgIT0JQeTJ1d3V1RkJkb3FwUT0=" > Device_3.xml"

Crontab -e:
49 14 * * * /home/elliot/Palo_Script.sh > /tmp/cron_log 2>&1

/tmp/cron_log:
/home/elliot/Palo_Script.sh: 5: /home/elliot/Palo_Script.sh: cannot create Device_1.xml &&
curl -kG [https://10.255.254.14/esp/restapi.esp?type=config:](https://10.255.254.14/esp/restapi.esp?type=config:) Directory nonexistent
/home/elliot/Palo_Script.sh: 7: /home/elliot/Palo_Script.sh: cannot create Device2.xml &&
curl -kG [https://192.168.19.46/esp/restapi.esp?type=config:](https://192.168.19.46/esp/restapi.esp?type=config:) Directory nonexistent
/home/elliot/Palo_Script.sh: 9: /home/elliot/Palo_Script.sh: cannot create Device_3.xml &&
curl -kG [https://192.168.19.25/esp/restapi.esp?type=config:](https://192.168.19.25/esp/restapi.esp?type=config:) Directory nonexistent



I have not done any of this before so sorry if i am doing something really silly.

---

### Post by steeldriver on 2017-01-11
nevermind - ian-weisser's answer below is better

---

### Post by ian-weisser on 2017-01-11
Curl seems to be asking you where to create the local files. /path/to/Device1.xml
Remember that cron does not use your logged-in environment variables. It may not know your home directory.
Best practice is to use full paths for the 'curl' command, too. Some implementations of cron may not know that it's at /usr/bin/curl, 

Remove the trailing quote (") at the end of each line.That's telling shell that the command continues on the next line (until '&', which does something you may not expect)

Consider using curl's -o flag for output instead of redirecting.

Remove the trailing '&&' on each line. && would make sense if you want some action to occur (like a log entry) based on success or failure of the curl command on that line...but there is no action after the && 

```
action1 && action2 && action3                        // Three dependent actions on one line. action3 occurs only on successful completion of action1 and action2

action1 && log_success() || log_failure()            // Usual usage for && - actions depend upon success or failure of action1

/usr/bin/curl -o /path/to/Device1.xml -kG "URL"      // Three independent actions on three separate lines 
/usr/bin/curl -o /path/to/Device2.xml -kG "URL"
/usr/bin/curl -o /path/to/Device3.xml -kG "URL"
```

---

### Post by elliotbeken on 2017-01-11
ian-weisser thanks it seems to be working now big thanks... :p

One last question i have is how would i get this to create a new file each time the CRON is run as currently it seems to be overwriting the current .xml file?

Ideally i would like the file to be renamed something like:

 Device_1_12th_Jan_1408.xml
Device_1_13th_Jan_1408.xml
Device_1_14th_Jan_1408.xml

So each file is backed up.

Thanks

---

### Post by ian-weisser on 2017-01-11
device_1_$(date +%dth_%b)_1408.xml

Try using 'echo' on it a few times to get the formatting exactly how you want it.
$(some_command) executes the command and the output replaces it.
The 'date' command can be formatted many ways. See 'man date'

---

### Post by elliotbeken on 2017-01-12
Perfect all working as expected.

I will also be looking into compressing and moving the files at the end of each day.

Thanks for all the help.

---

