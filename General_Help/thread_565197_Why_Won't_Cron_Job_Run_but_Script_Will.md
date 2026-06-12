---
title: "Why Won't Cron Job Run but Script Will?"
date: 2007-10-02
forum: General Help
---

### Post by linuxfool on 2007-10-02
I am trying to use backup a couple of directories to my tape drive every night.  

None of my cron jobs do anything.  

crontab -l produces.....

30 3 * * * /home/user/BackupScripts/nightlyBackup
1 * * * * echo "hello world"  >> /home/user/BackupScripts/helloworldreport

If I open a terminal and just type "/home/user...." it backs up correctly (i.e script runs).
Likewise if i open a terminal and type the second line (without the preceding numbers and stars), the hello world runs correctly.

But cron never does anything.   

I'm at a complete loss.  I got this to work under centos linux, but i have never gotten cron to run (as a user or root, although Ihave not tried root).

Where should I start?

---

### Post by yabbadabbadont on 2007-10-02
Try setting both the HOME and PATH environment variables at the top of the cronjob.  Those are the two things that usually cause trouble for people.

---

### Post by dcstar on 2007-10-02
> **linuxfool said:**
> I am trying to use backup a couple of directories to my tape drive every night.  

None of my cron jobs do anything.  

crontab -l produces.....

30 3 * * * /home/user/BackupScripts/nightlyBackup
1 * * * * echo "hello world"  >> /home/user/BackupScripts/helloworldreport

If I open a terminal and just type "/home/user...." it backs up correctly (i.e script runs).
Likewise if i open a terminal and type the second line (without the preceding numbers and stars), the hello world runs correctly.

But cron never does anything.   

I'm at a complete loss.  I got this to work under centos linux, but i have never gotten cron to run (as a user or root, although Ihave not tried root).

Where should I start?

I don't know about the first line, but "echo" is a Shell command and **cron** is not a shell.

Make an Executable script with:

```

#!/bin/sh
echo "hello world"  >> /home/user/BackupScripts/helloworldreport
```

in it, and it should work as a **cron** job.

The difference in you doing things in a terminal versus running them via cron is like giving someone else a recipe you have just perfected and then sending them off to a dark kitchen at night to cook - without instructions to turn the light on in the kitchen!

---

### Post by scruff on 2007-10-02
If you check your mail (type 'mail' at a prompt) you should see whats going on.

---

### Post by linuxfool on 2007-10-02
> **yabbadabbadont said:**
> Try setting both the HOME and PATH environment variables at the top of the cronjob.  Those are the two things that usually cause trouble for people.

showing my lack of knowledge here. ... do you have a recommended howto or tutorial on doing this correctly?

---

### Post by linuxfool on 2007-10-02
> **linuxfool said:**
> showing my lack of knowledge here. ... do you have a recommended howto or tutorial on doing this correctly?


bash: mail: command not found

does this indicate that something is messed up?

---

### Post by yabbadabbadont on 2007-10-02
```
/home/daffy $ echo $HOME
/home/daffy
/home/daffy $ echo $PATH
/home/daffy/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```
So, in my case, I would add
```
HOME=/home/daffy
PATH=/home/daffy/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```
to the top of the cronjob.

---

### Post by linuxfool on 2007-10-02
> **dcstar said:**
> I don't know about the first line, but "echo" is a Shell command and **cron** is not a shell.

Make an Executable script with:

```

#!/bin/sh
echo "hello world"  >> /home/user/BackupScripts/helloworldreport
```

in it, and it should work as a **cron** job.

The difference in you doing things in a terminal versus running them via cron is like giving someone else a recipe you have just perfected and then sending them off to a dark kitchen at night to cook - without instructions to turn the light on in the kitchen!

Thanks.  I just put that direclty in the cron job to test it.  I did what you said and it should be running every minute.  Nothing is ever piped to helloworldreport.  However if i click on the file in the GUI, it works fine.

---

### Post by scruff on 2007-10-02
It's even easier to add things to your PATH using the original PATH variable contents. 

```

PATH=$PATH:/new/stuff:/more/new/stuff/

```

You can also put this stuff in say, your ~/.bashrc file so that it is always this way (rather than just during the cron job) if you prefer.

Not sure about your mail issue. I run a lot of server stuff and it may have came with postfix or something. I'm rather new to Ubuntu, but Slackware and Gentoo have this installed by default IIRC. The 'mail' command is just the onboard system mail, so I am surprised you don't have it...

```

sean@sullyhome:~$ which mail
/usr/bin/mail

```

---

### Post by linuxfool on 2007-10-02
> **scruff said:**
> It's even easier to add things to your PATH using the original PATH variable contents. 

```

PATH=$PATH:/new/stuff:/more/new/stuff/

```

You can also put this stuff in say, your ~/.bashrc file so that it is always this way (rather than just during the cron job) if you prefer.



Although this is slightly off track, do i figure out what the path is by the way described above, echo $PATH command. or some other way.  Where do I find the "original PATH variable contents.

Meanwhile it still won't run.  I really don't know why it runs fine when I click on the file but not as a cron job.  here is my updated cron -l output.

HOME=/home/me
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
30 3 * * * /home/me/BackupScripts/nightlyBackup
1 * * * *  /home/me/BackupScripts/helloworld

---

### Post by dcstar on 2007-10-03
> **linuxfool said:**
> bash: mail: command not found

does this indicate that something is messed up?

Install the **mailx** package.

---

### Post by scruff on 2007-10-03
> **linuxfool said:**
> Although this is slightly off track, do i figure out what the path is by the way described above, echo $PATH command. or some other way.  Where do I find the "original PATH variable contents.

Meanwhile it still won't run.  I really don't know why it runs fine when I click on the file but not as a cron job.  here is my updated cron -l output.

HOME=/home/me
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
30 3 * * * /home/me/BackupScripts/nightlyBackup
1 * * * *  /home/me/BackupScripts/helloworld

With regards to your first queston, you don't need to figure out $PATH's contents. That variable will be expanded by the shell. All you need to provide is the variable. 

Check out the cron manpage. You can increase the log level to try and determine what the problem is. 

>  
NAME
       cron - daemon to execute scheduled commands (Vixie Cron)

SYNOPSIS
       cron [-f] [-l] [-L loglevel]

-L loglevel
               Sets  the loglevel for cron. The standard logging level (1) will log the start of
               all the cron jobs. A higher loglevel (2) will cause cron to log also the  end  of
               all  cronjobs,  which  can be useful to audit the behaviour of tasks run by cron.
               Logging will be disabled if the loglevel is set to zero (0).


---

### Post by linuxfool on 2007-10-04
I put mailx on and checked the mail. I am getting this as output from the tapebackup cron job (nightlyBackup).  Again, I can click on the gui script and type the script in a terminal window and it runs fine (meaning the tar starts and the tape drive is working properly and has the correct permissions).  But the cron balks.  I have read the cron man page and for whatever reason the solution is not coming to me.  Here is the output.  


Subject: Cron <me@blackbox> /home/me/BackupScripts/nightlyBackup
X-Cron-Env: <HOME=/home/me>
X-Cron-Env: <PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games>
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <LOGNAME=me>
Date: Thu,  4 Oct 2007 03:30:01 -0400 (EDT)

star: No such device or address. Cannot open '/dev/tty'.

---

### Post by yabbadabbadont on 2007-10-04
OK, the problem becomes clearer.  Cron has a hard time whenever a running program tries to write large amounts of ouput to the screen while running.  You need to redirect the output to either a file or /dev/null.  So try something like this:
```
HOME=/home/me
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/ bin:/sbin:/bin:/usr/bin/X11:/usr/games
30 3 * * * /home/me/BackupScripts/nightlyBackup > /home/me/BackupScripts/nightlyBackup.log 2>&1
```

---

### Post by linuxfool on 2007-10-05
Yabbadabbadont,


I did what you suggested above,

The cron job ran last night, meaning the cron daemon started it up, it made the .log file, but this is all that is in the log file......  (same as what I was getting mailed to me before I changed the cron job)

star: No such device or address. Cannot open '/dev/tty'.  

I did not output it to /dev/null though to see what would happen.  I guess I can try that, but I don't think it's going to resolve the problem?????

Thanks for the help,

---

### Post by linuxfool on 2007-10-10
With the help of you guys, i think i figured it out.   Part of the star backup script (which was not published here) had a -multivol flag.  I think this was forcing a terminal launch somehow, and as several members pointed out, cron didn't like this.  When I removed the -multivol flag, all went well.

Thanks for the help.

---

### Post by outsider2222 on 2007-11-25
> **linuxfool said:**
> Thanks.  I just put that direclty in the cron job to test it.  I did what you said and it should be running every minute.  Nothing is ever piped to helloworldreport.  However if i click on the file in the GUI, it works fine.


did U ever get it to work, I seem to be having the same problem (about to give up on Ubuntu ...) reply to xxsomervi8xxatxxtelusxxdotxxnet please

---

### Post by gcediel on 2007-12-05
> **outsider2222 said:**
> did U ever get it to work, I seem to be having the same problem (about to give up on Ubuntu ...) reply to xxsomervi8xxatxxtelusxxdotxxnet please

Hi:

I don't know if you have already solved the problem. I did it by adding '> /dev/null' at the end of the script being executed by crontab.

Best regards.

Guillermo.

---

### Post by newOldUser on 2007-12-13
Just adding my two cents to help someone who may be searching the forums.

I had a similar problem running scripts that used a lot of MENCODER commands.  The scripts would run fine from a terminal but not when started up by cron.

The cron commnd was something like this:
30 1 * * * /home/user/scripts/buildVideo.sh > /home/user/log/buildVideo.log

basically it would run the script buildVideo.sh and dump script output to buildVideo.log

It wasn't till I added the 2>&1 at the end (as Yabbadabbadont suggested) that I got it work under cron.  The mencoder command was generating a lot of output to stderr, the 2>&1 redirected it to the buildVideo.log.  So the working crontab entry looks like this:
30 1 * * * /home/user/scripts/buildVideo.sh > /home/user/log/buildVideo.log  2>&1

There's a good example of Linux I/O redirection at: [http://www.cpqlinux.com/redirect.html](http://www.cpqlinux.com/redirect.html)

Hope this helps someone.

---

