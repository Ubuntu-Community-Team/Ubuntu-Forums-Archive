---
title: "cron job fails, but works when manually executed"
date: 2007-10-21
forum: General Help
---

### Post by txr13 on 2007-10-21
I've got a script that I want to execute at midnight on the first and fifteenth day of every month. The script itself runs perfectly when executed from the command-line. However, when executed via cron, the script doesn't return correct results.

Specifically, the manually-executed script creates a tar.gz file and transmits it to my backup server--approximately a 15MB filesize. However, when run by cron, the received file only contains a random selection of files from the source directory--approximately 300KB in size.

The script's permissions are set to 700, due to the necessity of it containing the sudo password. (The source directory and daemon are owned by root.) Does anybody have any thoughts?

crontab:
```
00 00 01,15 * * /home/<username>/backup.sh
```

script:
```
#!/bin/sh
echo "<password>" | sudo -S /etc/init.d/boinc stop
sleep 5
cd /usr/bin
sudo tar -cvzf /home/<username>/xels.tar.gz BOINC/
sudo /etc/init.d/boinc start
cd ~
if ncftpput -f /home/<username>/login.cfg -E -S .tmp /BOINCPS /home/<username>/xels.tar.gz; then
	sudo rm -f /home/<username>/xels.tar.gz
	exit 0
fi
exit 1

```

---

### Post by keithweddell on 2007-10-21
Cron doesn't like script names with dots in them.  Try calling your script "backup" without the ".sh" and it should work.

Keith

---

### Post by txr13 on 2007-10-21
I renamed the script to "backup" without the ".sh", but it still doesn't work when called by cron. Also, there's another script called by cron in the same directory with the .sh extension, and it works just fine.

---

### Post by cas65 on 2008-01-23
I had a similar problem with a cron job failing and producing no informative output, but working when manually executed.  I guessed that possibly the problem was related to the problem described in [http://lists.freebsd.org/pipermail/freebsd-bugs/2006-May/018362.html](http://lists.freebsd.org/pipermail/freebsd-bugs/2006-May/018362.html), Cron jobs may attempt to mail output to the user, and apparently can fail if there is no mail program.  I checked and discovered that the mail program was not installed with my gutsy 7.10 kubuntu setup.  Installing it, by installing the mailx package that contains it, ended my problems with the cron job.

---

