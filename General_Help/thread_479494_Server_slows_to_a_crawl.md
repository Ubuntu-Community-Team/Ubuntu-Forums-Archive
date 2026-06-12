---
title: "Server slows to a crawl"
date: 2007-06-20
forum: General Help
---

### Post by dir7bag on 2007-06-20
I have been running Ubuntu Feisty as a multi-purpose server for over a month now.  Just the other day, my web site became unaccessible both internally and externally.  Restarting the server allowed connections for a few minutes, but then nothing.  So I ran 'top' for a while and noticed that there are multiple bash processes running, each taking 7-9% cpu, essentially maxing the system out.  I also ran 'vmstat -10' for a little while and noticed that my memory is being eaten slowly.  I have checked some logs, but I am not sure what to look for.  Also noteworthy, when the cpu is maxed out and I attempt to do anything like open a terminal or view log files, a message tells me there are too many open files (something like that) and most of the characters become boxes.

I am new to Linux and Ubuntu is my first distro.  I have Ubuntu Feisty LAMP with the desktop (I am new to this and sometimes a GUI is nice).  I have installed the following: WebMin, punBB, MediaWiki, gallery2, phpMyAdmin, openSSH, VNC, and gcStar.  I have also enabled SSI in Apache, which is the most recent change for the system.  I had ports 80 and 22 open on my Linksys WRT54G, forwarding to my server.  I have disabled port 22 for now, thinking maybe I opened a security hole somewhere.

Any help is appreciated.

---

### Post by phantomdata on 2007-06-20
My first suggestion would be to see what those BASH processes are doing.  You can get a visual layout of what processes are children of what by running "ps -auxf" - and then looking for those random BASH processes.  The USER column (far left) may also be of interest to you.

My second suggestion would be to kill off the Apache service ("sudo /etc/init.d/apache stop" should work in Ubuntu - otherwise "sudo apachectl shutdown" is standard).  With that shutdown, you should see if the processes die away.  Maybe WebMin was doing something crazy and spawning excess processes.  See where that gets you.

You might also check out what files those extra BASH processes are operating on.  "sudo lsof | grep bash" will give you the listing of open files.  Does anything look familiar to you?  You can also use "sudo lsof | grep bash | wc -l" to get the number of files opened by those bash processes.  If it's not extraordinarily high, then there's probably another culprit.

Anyway, closing down SSH was a good idea.  If it were me, I would remove all external access to the machine until you've figured out what's causing this.  It is probably just a bad process (ps -auxf should help you figure out what those BASH processes are doing!) - but it's always best to be safe than sorry.  The command "last" will show the last user logins.  Maybe you will see a login when there shouldn't be one.

As a last resort, if the system gets too bogged down - you can run "sudo killall -9 bash" to kill all bash instances (since you say that they're eating all your CPU it means that they're doing SOMETHING).  Note that it will also kill your current bash instance, so you'll have to relogin if you're at a terminal prompt.  I hope this helps.  Good luck.

---

### Post by dir7bag on 2007-06-20
Thanks.  I will try these suggestions when I get home and post the results here.

---

### Post by dir7bag on 2007-06-20
Ok, I have run these commands, but I am not too sure what I should be looking for.  I had to send the output to a file as it was too much data (it wouldn't scroll any more).  The network cable to this box is unplugged until I figure this issue out.

**First I ran "ps -auxf".**
I see a lot of this

COMMAND     PID       USER   FD      TYPE     DEVICE     SIZE       NODE NAME
rodney    6091  0.0  0.0      0     0 ?        Zs   07:43   0:00  |   \_ [sh] <defunct>
root      6094  0.0  0.1   2628   928 ?        S    07:44   0:00  \_ /USR/SBIN/CRON
rodney    6095  0.0  0.0      0     0 ?        Zs   07:44   0:00  |   \_ [sh] <defunct>
root      6098  0.0  0.1   2628   928 ?        S    07:45   0:00  \_ /USR/SBIN/CRON

and this

rodney    6916  0.0  0.1   1816   656 ?        S    10:56   0:00 -bash                
rodney    6920  0.0  0.1   1812   652 ?        S    10:57   0:00 -bash                
rodney    6924  0.0  0.1   1816   656 ?        S    10:58   0:00 -bash                
rodney    6928  0.0  0.1   1812   652 ?        S    10:59   0:00 -bash                
rodney    6932  0.0  0.1   1812   652 ?        S    11:00   0:00 -bash
[B]
Then I ran "sudo lsof | grep bash"[/B]
This is repeated over and over for 1.2 MB worth of data

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
bash       6081     rodney  cwd       DIR       33,1     4096      98114 /home/rodney
bash       6081     rodney  rtd       DIR       33,1     4096          2 /
bash       6081     rodney  txt       REG       33,1    27548     213723 /home/rodney/.../bash
bash       6081     rodney  mem       REG        0,0                   0 [heap] (stat: No such file or directory)
bash       6081     rodney  mem       REG       33,1     7552     606568 /lib/libnss_mdns4.so.2
bash       6081     rodney  mem       REG       33,1    67408     605195 /lib/tls/i686/cmov/libresolv-2.5.so
bash       6081     rodney  mem       REG       33,1    17884     605185 /lib/tls/i686/cmov/libnss_dns-2.5.so
bash       6081     rodney  mem       REG       33,1     7084     606571 /lib/libnss_mdns4_minimal.so.2
bash       6081     rodney  mem       REG       33,1    38416     605186 /lib/tls/i686/cmov/libnss_files-2.5.so
bash       6081     rodney  mem       REG       33,1  1307104     605176 /lib/tls/i686/cmov/libc-2.5.so
bash       6081     rodney  mem       REG       33,1   109268     605039 /lib/ld-2.5.so
bash       6081     rodney    0r     FIFO        0,6               18193 pipe
bash       6081     rodney    1w     FIFO        0,6               18194 pipe
bash       6081     rodney    2w     FIFO        0,6               18194 pipe
bash       6081     rodney    3u     sock        0,5             3228065 can't identify protocol
bash       6081     rodney    4u     IPv4    3228996                 UDP rlubuntu.local:41667->192.168.0.1:domain 

**"sudo lsof | grep bash | wc -l"**
results in 13869 which seems rather high.  It grows with each subsequent run.

**"last"**
doesn't show any weird or unexpected logins.

---

### Post by pmg on 2007-06-21
What cron jobs have you set up?  Looks like you have something setup to run a cron job every minute (noticed that the start times of the processes are one minute apart.)  Run **crontab -l** and/or look in the file /etc/crontab and in the directory /etc/cron.d.

---

### Post by dir7bag on 2007-06-21
I have not manually set up any cron jobs as I didn't know what it was until this exercise.

Here are the results:

rodney@rlubuntu:~$ crontab -l
* * * * * /home/rodney/.../bash

Is this a normal occurrence?

**Contents of cron.d**
anacron
php5

```
# /etc/cron.d/anacron: crontab entries for the anacron package

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

30 7    * * *   root	test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null
```

```
# /etc/cron.d/php5: crontab fragment for php5
#  This purges session files older than X, where X is defined in seconds
#  as the largest value of session.gc_maxlifetime from all your php.ini
#  files, or 24 minutes if not defined.  See /usr/lib/php5/maxlifetime

# Look for and purge old sessions every 30 minutes
09,39 *     * * *     root   [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm
```

Is anacron supposed to be in there?

---

### Post by dir7bag on 2007-06-21
I did a "crontab -e" and removed the data in the file.  This seems to have fixed the problem, but I will have to check on it when I get home.

The big question is how did that get there?  Is there some way that someone could have connected and run the command to add the cron job?

---

### Post by pmg on 2007-06-21
> **dir7bag said:**
> 
rodney@rlubuntu:~$ crontab -l
* * * * * /home/rodney/.../bash

Is this a normal occurrence?

No, that would be a problem.  That is starting a new bash shell every minute the machine is running.  Each one would use a bit of memory, but it'll add up until... well, you know the result.  :-)  
> 
Is anacron supposed to be in there?
Yes, that's fine.  It only runs once a day, at 7:30, and it'll exit when it's done and not hang around the way the bash shells were.

---

