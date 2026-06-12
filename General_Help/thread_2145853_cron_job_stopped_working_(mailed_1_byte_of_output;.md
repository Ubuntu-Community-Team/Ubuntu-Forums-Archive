---
title: "cron job stopped working (mailed 1 byte of output; but got status 0x00ff, #012)"
date: 2013-05-16
forum: General Help
---

### Post by iowabeakster on 2013-05-16
I have a couple of simple scripts that run every night as back-up cron jobs.  They simply rsync some files from my phone and back them up to an external hard drive connected to my PC.  Those scripts had worked just fine (for a couple of months), until my router reassigned the IP address for my phone on the LAN. 

Of course they stopped working as they were trying to connect to the wrong IP address.

So, I fixed my scripts for the proper IP address.  And they work absolutely fine again... when I run them manually.  

But when the scripts are run as a cron jobs they fail as with the following entry example in syslog.

```
May 16 15:51:27 optipussy CRON[19616]: (kirk) MAIL (mailed 1 byte of output; but got status 0x00ff, #012)
```

crontab entries

```
29 02 * * * /home/kirk/nexus4backup_script/titanium_script.sh
40 02 * * * /home/kirk/nexus4backup_script/TWRP_script.sh



```

script example: (both are identical except for the the specific files they back up and where they the backup-ed to)

```
#!/bin/sh
#titanium folder backup


rsync -r -t -p -o -g -v --progress --delete -c -l -b -s -e "ssh -i /home/kirk/.ssh/id_rsa" --rsh='ssh -p33669' root@192.168.0.12:/storage/emulated/0/TitaniumBackup/ /media/freeagent/phonebackup/TitaniumBackup
```

As I said, these did work perfectly every night.  And they still work if I run them manually.  But they don't work with crontab which keeps giving this error in syslog... (kirk) MAIL (mailed 1 byte of output; but got status 0x00ff, #012)

---

### Post by linuxtechguy on 2013-05-16
1. You can combine most of those flags into one group of flags like -rtpogv
2. You might want to try adding a MAILTO and TERM

You might get alot more useful information.

Like this:

```

MAILTO="your@email.com"
TERM=xterm


29 02 * * * /home/kirk/nexus4backup_script/titanium_script.sh
40 02 * * * /home/kirk/nexus4backup_script/TWRP_script.sh

```

---

### Post by iowabeakster on 2013-05-16
I tried the MAILTO and TERM additions to crontab...

I didn't get anything emailed to me.  Same error as before.

The flags are the result of some copy/pasting from the app Grsync... much easier for me to create an outrageous command line like that using Grsync than trial-n-erroring the command line myself. (wink)

---

### Post by iowabeakster on 2013-05-16
I kept playing around with it, I think I just misinterpreted the message in the syslog.  Maybe that syslog message isn't an error at all?  Googling finds all kinds of threads with that output.

Anyway, cronjobs did not run for the last few nights (after I discovered the IP change and fixed scripts).

Anyway, more playing around and I think it is working fine again.  Scripts are running from crontab right now.  So that's progress.  I added another script to do pictures too.  We'll see in the morning.

Marking as solved.... too bad I don't know why it didn't work for the last few days... nor what I did to make it work again either (if anything).

---

