---
title: "How to run ssh command every minute? writing to a log file."
date: 2016-01-15
forum: General Help
---

### Post by rob134 on 2016-01-15
I have this command/script that I would like to run every 60 seconds in order to monitor CPU/memory usage writing to a log.
```
while true; do (echo "%CPU %MEM ARGS $(date)" && ps -e -o pcpu,pmem,args --sort=pcpu | cut -d" " -f1-5 | tail) >> ps3.log; sleep 60; done
```
So sleep 60; will make it write to the log every 60 seconds but will have to stay logged in SSH until I hit CTRL-C to cancel the command so it will stop logging.
I would like to log it every 60 seconds for days/weeks since my server has stability issues and would like to monitor cpu/memory when it crashes.

I have tried ```
watch -n 60 bash ./pscript.sh
```
pscript.sh contains the code:
```
#!/bin/bash
while true; do (echo "%CPU %MEM ARGS $(date)" && ps -e -o pcpu,pmem,args --sort=pcpu | cut -d" " -f1-5 | tail) >> ps5.log; sleep 60; done

```
And same thing... it stops logging after I hit CTRL-C in the SSH.

What's the correct way of doing this?

Thanks!

---

### Post by papibe on 2016-01-15
Hi rob134.

A couple of thoughts.

The simple solution I can think of is to run it inside a GNU screen, or a tmux session. That way you could detach the session and let it run on sort of a virtual sesion.

Another alternative is to run a cron job on the server, not your machine, so that every minute you could add an entry to the log. You won't need leave anything running after your ssh session as the cron daemon would create the command every time.

Does that help? Let us know how it goes, and if you have more questions.
Regards.

---

### Post by rob134 on 2016-01-16
> **papibe said:**
> Hi rob134.

A couple of thoughts.

The simple solution I can think of is to run it inside a GNU screen, or a tmux session. That way you could detach the session and let it run on sort of a virtual sesion.

Another alternative is to run a cron job on the server, not your machine, so that every minute you could add an entry to the log. You won't need leave anything running after your ssh session as the cron daemon would create the command every time.

Does that help? Let us know how it goes, and if you have more questions.
Regards.

I have:
1. created a conjob with 
crontab -e 
in the file I added [COLOR=#111111][FONT=Consolas]* */1  * * * /var/log/pscript.sh
[/FONT][/COLOR]
2. put the pscript.sh file in /etc/cron.hourly 

Both seem to not do anything

Am I doing something wrong? I'm new to cron jobs :)

---

### Post by 1clue on 2016-01-16
Have you thought of using snmp?  It's made for exactly this purpose.

[http://www.thegeekstuff.com/2012/09/snmp-introduction/](http://www.thegeekstuff.com/2012/09/snmp-introduction/)

---

### Post by papibe on 2016-01-16
Keep the script on your directory. Don't move it to 'etc/cron.hourly'. For instance:
```
/home/user/bin/pscript.sh
```
Add execution permissions:
```
chmod a+x /home/user/bin/pscript.sh
```
Make sure it starts with a shebang:
```
#!/bin/bash
while true...
```
Don't use the 'sleep 60' part. Call it every minute instead. The syntax would be:
```
*/1 * * * *  /home/user/bin/pscript.sh
```
Here are more examples and details: [Howto crontab]("https://help.ubuntu.com/community/CronHowto").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by rob134 on 2016-01-16
> **papibe said:**
> Keep the script on your directory. 

```
#!/bin/bash
while true; do (echo "%CPU %MEM ARGS $(date)" && ps -e -o pcpu,pmem,args --sort=pcpu | cut -d" " -f1-5 | tail) >> /home/user/bin/ps6.log; done

```
This while true works when I enter it in the ssh. It writes it to the log successfully.

With grep -i cron /var/log/syslog I can see the cron is succesfully running every minute. I've both entered */1 * * * *  /home/user/bin/pscript.sh as root and as the user in crontab -e

So it's running the cronjob but not executing the pscript.sh 
I did the chmod

No big thing if I can't get it to work. But just curious why it doesn't :)

Thanks

---

### Post by papibe on 2016-01-17
Since the crontab is running the cycle now, you don't need the 'while' loop.

Try something like this, so you can debug it:
```
#!/bin/bash
LOGFILE="/home/user/bin/ps6.log"

# Log tittle
echo "%CPU %MEM ARGS $(date)" >> "$LOGFILE"

# List of top processes 
ps -e -o pcpu,pmem,args --sort=pcpu | cut -d" " -f1-5 | tail >> "$LOGFILE"

# Blank line that separates output from next run
echo "" >> "$LOGFILE"

```
Make sure to replace 'user' for your actual username, and that the ~/bin directory exists.

Stay logged in, and keep checking the content of the log file.

Hope it helps. Let us know if that makes a difference.
Regards.

---

### Post by rob134 on 2016-01-18
> **papibe said:**
> 
Hope it helps. Let us know if that makes a difference.
Regards.
Still no luck. There must still be something wrong with the script code for cron jobs specific.
Every minute the cron job attempts to do something with it. (I've changed the user to my own username in the actual file)
```
Jan 18 15:19:01 CRON[23012]: (user) CMD (/home/user/bin/pscript.sh)
```
Appreciate your help thus far.

---

### Post by btindie on 2016-01-18
Does the user the script is now running as have permission to write to the log file?
```
ls -l /home/user/bin/ps6.log
```
it should have the same user/group as the user who runs it.

That script can be improved slightly so it sorts the list the other way up
```

#!/bin/bash
LOGFILE="/home/user/bin/ps6.log"

# Log date
date >> "$LOGFILE"

# List of top processes 
ps -eo pcpu,pmem,cmd --sort=-pcpu | head >> "$LOGFILE"

# Blank line that separates output from next run
echo >> "$LOGFILE"

```

You can then run 'tailf /home/user/bin/ps6.log' from an ssh session to monitor the log. The 'tailf' command will update what appears on the screen if something is written to the file it's monitoring. Ctrl-C to exit.

---

### Post by rob134 on 2016-01-18
> **btindie said:**
> Does the user the script is now running as have permission to write to the log file?
```
ls -l /home/user/bin/ps6.log
```
it should have the same user/group as the user who runs it.


It works! Before what I did was I created the file with root in FTP and chmod a+x /home/user/bin/pscript.sh. I even set the 777 for both .sh and .log files. 
I just logged in with ssh user and created the script file in there. chmod a+x the file again and now it works. Which obviously I should have done from the start... 

This should give me more insight on dealing with these [daily crashes I'm having.]("http://ubuntuforums.org/showthread.php?t=2308415&p=13425241#post13425241")

Thank you for your patience

---

