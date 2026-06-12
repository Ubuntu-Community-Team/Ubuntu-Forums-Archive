---
title: "Crontab Problem... bump"
date: 2007-09-05
forum: General Help
---

### Post by dgib on 2007-09-05
Hey guys/girls...

New to the crontab idea but totally get it!! =D

all im trying to do is run a couple of scripts which back some things up...
the scripts work perfectly on their own just running from the terminal.

but in the crontab... the first script does not work. it is set to run ever 5 minutes but does nothing. nothing wrong with the script... anyone have any ideas?

here is my crontab...

```

# m h  dom mon dow   command
0,5,10,15,20,25,30,35,40,45,50,55 * * * * /home/terry/backup.sh 
42 4 * * * /home/terry/automysqlbackup.sh
42 15 * * * /home/terry/sqlbackup.sh

```

p.s. i know people have had the same problem but never found a reply which fixed my issue... so bump bump bump =DD

---

### Post by malder on 2007-09-05
Try trapping the output to a file to record what is happening:

42 4 * * * /home/terry/automysqlbackup.sh > /home/terry/mysqloutput.txt 2>&1

That should give you a clue...

---

### Post by dgib on 2007-09-05
strange,

nothing will output. doesn't attempt to create the file or anything :/
like it skips the first line and does the others :/

---

### Post by pmg on 2007-09-05
One thing to keep in mind with cron jobs is they don't go thru the normal login process, so some things may not be set up in the environment the way you expect them.  For example the PATH environment variable may not have the same list of directories you're used to.  As a very simple test try something like:
```
42 * * * * /bin/echo testing > /tmp/outfile
```
to make sure you're getting the job set up right and crond is running.  Then, try
```
43 * * * * /usr/bin/printenv > /tmp/outfile
```
and compare that to when you run **printenv **from a login session.

You may also find it useful to **tail -f /var/log/syslog** while working on this.  That way you'll be able to see what cron writes and when it runs commands in a crontab file.

---

