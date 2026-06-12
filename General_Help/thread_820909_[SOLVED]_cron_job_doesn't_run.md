---
title: "[SOLVED] cron job doesn't run"
date: 2008-06-06
forum: General Help
---

### Post by HDave on 2008-06-06
I have a user specific crontab job created via "crontab -e" that doesn't run at all.  Based on reading several similar postings, I added a simple line just to see if cron was running my jobs at all...it doesn't appear to be.  That is, its not running *anything* apparently.

However, "ps" shows cron is running. I have tried restarting cron several times  with:
```
sudo /etc/inet.d/cron restart
```

Also, here is the my output of "crontab -l"
```
# m h  dom mon dow   command
* * * * * /usr/bin/touch /tmp/test.file
```

Any help is appreciated.

---

### Post by ibuclaw on 2008-06-06
May I suggest that you put it in your system crontab?
I always prefer to use mine because I know the commands will always be executed.
Plus I have a little more flexiblilty because I can execute the commands as anyone I want on my system (including root).

The way you would go about doing it is like this:
```
sudo nano /etc/crontab
```
And putting in the exact same line as you did. but include your username
> * * *   *  *   **username**   exec /usr/bin/touch /tmp/test.file
I've also put in the command "exec", because I favour the nature of the program (it executes the command passed to it).

Also, open up your syslog monitor ("**System>Administration>System Logs**") and select the "syslog" file in the left column and scroll down to the bottom of the file.
Wait a minute, and something like this should appear to show you that the command has been executed successfully:
> Jun  6 23:15:01 fredbuntu /USR/SBIN/CRON[5840]: (iain) CMD (exec /usr/bin/touch /tmp/test.file)
Then, when you peer into the /tmp folder. The dummy file will be there.

Regards
Iain

---

### Post by pancakedan on 2008-06-06
Thats how I do my cron jobs as I had the same problem that a job would not run as a user specific job

---

### Post by mike2357 on 2008-06-06
I generally prefer to use individual users' cron files, but mainly because that's how I learned.  Debugging cron commands can be difficult.  When I'm having trouble with one I send the output of the command to a file, as follows:

* * * * * /usr/bin/touch /tmp/test.file > OUT_CRON 2>&1

If cron is running, OUT_CRON will be written in the user's home directory.  The 2>&1 means to send error messages to the same output file as standard output, which in this case is OUT_CRON.

Good luck.  Incidentally, I tried your cron command and it worked fine.  If you solve the mystery, please post what happened.  I'd be curious to find out.

---

### Post by HDave on 2008-06-06
> **mike2357 said:**
> * * * * * /usr/bin/touch /tmp/test.file > OUT_CRON 2>&1

I tried your line and got same result -- nothing.  Given that my line works for you it is absolutely a problem with my system. Hmmm.... :confused:

---

### Post by unutbu on 2008-06-06
Try editing your crontab to this: (Change the PATH to your taste). If any of these environment variables will help you, it is probably SHELL.

```
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/hdave/bin
MAILTO=hdave
HOME=/home/hdave
DISPLAY=:0.0

* * * * * /usr/bin/touch /tmp/test.file

```

I tried the above crontab (changing the username to my own) and it worked for me.

---

### Post by HDave on 2008-06-06
> **pancakedan said:**
> Thats how I do my cron jobs as I had the same problem that a job would not run as a user specific job

Did you ever file a bug report in launchpad?  I searched there and found a few things:

1) My account need to be added to the crontab group
2) Crontab entries cannot have a period "." in them
3) There must be a new line after the entry

So I fixed all three of these things...no joy.  This is really starting to tick me off.  I respect the advice I have been given here to punt and use the system cron facility...but I can't let it go!  ](*,)

---

### Post by HDave on 2008-06-06
> **unutbu said:**
> Try editing your crontab to this: (Change the PATH to your taste). If any of these environment variables will help you, it is probably SHELL.

```
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/hdave/bin
MAILTO=hdave
HOME=/home/hdave
DISPLAY=:0.0

* * * * * /usr/bin/touch /tmp/test.file

```

I tried the above crontab (changing the username to my own) and it worked for me.

Tried this -- again, no joy.  

For what its worth, everytime I edit my crontab I see entries in /var/log/syslog so I know cron is getting the message.  Plus I confirm the change with crontab -l.

It doesn't look like cron has its own logging facility...that would be cool.

---

### Post by unutbu on 2008-06-06
This shows which groups I am a member of:
```
% id
uid=1000(pigeon) gid=1000(pigeon) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),1000(pigeon)

```
Your crontab entry works for me so I don't think you need to be part of the crontab group.

---

### Post by unutbu on 2008-06-06
Perhaps create a new user and see if cron works for the new user?

---

### Post by HDave on 2008-06-06
OK -- In desperation to see cron actually do ANYTHING on my machine, I went ahead and edited /etc/crontab to touch a file in the /tmp directory.  

If I use "root" as the userid it works.   If I use my own userid it does not work.  If I use one of the other userid's on the system, it also works.

Before anyone asks...I typed my userid in correctly.  Checked it 50 times.  I don't have any funky userid stuff going on...NFS, Windows Domain, etc.  Just plain old vanilla Hardy.

So the question is this:  Why does cron refuse to run a command as me?

---

### Post by HDave on 2008-06-06
> **unutbu said:**
> Perhaps create a new user and see if cron works for the new user?

I did this and it works for the other users on this machine.

I can't imagine this makes a difference, but my home directory is auto-mounted when I log in by Truecrypt-PAM.

My username is 12 characters...does that matter?

---

### Post by unutbu on 2008-06-07
Check for differences between your .bashrc and the new user's .bashrc.

For instance, does your .bashrc include
```

[ -z "$PS1" ] && return
```
? If not, include it.

I don't think Truecrypt, nor the length of your user name should make a difference, but that's just an opinion, not backed up by any experience.

---

### Post by mike2357 on 2008-06-07
From "man crontab":

"If  the /etc/cron.allow file exists, then you must be listed therein in order to be allowed to use this command.  If the  /etc/cron.allow  file does  not  exist  but the /etc/cron.deny file does exist, then you must not be listed in the /etc/cron.deny file in order to use this  command."

My system has neither /etc/cron.allow nor /etc/cron.deny.  Also, I'm in the same UNIX groups as you're in.

The issue with an encrypted home directory could be the problem, if the "root" account doesn't also have access to your home directory.  I'm making this guess because cron is run by root.

---

### Post by HDave on 2008-06-07
> **unutbu said:**
> Check for differences between your .bashrc and the new user's .bashrc.

For instance, does your .bashrc include
```

[ -z "$PS1" ] && return
```
? If not, include it.

I don't think Truecrypt, nor the length of your user name should make a difference, but that's just an opinion, not backed up by any experience.

I did have this in my .bashrc at the top.  Also I noticed that the shell being run from the system cron is "sh".

---

### Post by HDave on 2008-06-07
> **mike2357 said:**
> From "man crontab":

"If  the /etc/cron.allow file exists, then you must be listed therein in order to be allowed to use this command.  If the  /etc/cron.allow  file does  not  exist  but the /etc/cron.deny file does exist, then you must not be listed in the /etc/cron.deny file in order to use this  command."

My system has neither /etc/cron.allow nor /etc/cron.deny.  Also, I'm in the same UNIX groups as you're in.

The issue with an encrypted home directory could be the problem, if the "root" account doesn't also have access to your home directory.  I'm making this guess because cron is run by root.

I don't have the cron.allow and cron.deny files in my etc directory, so I am good there.  Also I checked and root can read/write to my home directory no problem.

Just wanted to say I *really* appreciate everyone's help here.  I am just hoping that *when* we get to the bottom of this, we all learn something useful.

EDIT:  I reverted my .profile back to a pristine original state...no change.

EDIT:  I enabled logging for cron only to find out that cron.log contains EXACTLY the same content as syslog :-(

EDIT:  Just for fun, I stuck a bogus username into /etc/crontab...a minute later got a nice error message in syslog...so it knows I am a valid user

---

### Post by HDave on 2008-06-08
OK -- I think I found the problem, though I don't know how to fix it easily.

Knowing that cron runs as root, I did an "sudo -i" to get a root terminal prompt.  I then did a "su myaccountname" and immediately got an authentication error:

```
su: Authentication failure
```

I can su from root to any account on the machine but mine.  As mine is the only one that has touched PAM to auto-mount my truecrypt partition, I must have goofed something up, or need to refine my settings.

Once I saw this I checked in auth.log and lo and behold there is my authentication failure error message coming from CRON.  Why cron doesn't stick this critical piece of information in its own log God only knows. 

In any event, I'll go chase that down and report back.  Still want to close the loop here on all of the above suggestions.

---

### Post by HDave on 2008-06-09
OK -- As it turns out, pam_truecrypt.so, was correctly preventing root from su'ing to my account.  It does this because encrypting the home partition on a laptop doesn't do you much good if someone can boot in recovery mode and "su" to your account name and have the encrypted partition automatically mounted!!  However, I edited the source to allow the "su" to succeed, if the partition is already mounted...i.e. I have logged in via gdm.

As a summary wrap-up here's what else we've learned:

1) user specific crontabs are stored in /var/spool/cron/crontabs, but you should never go in there directly...just use the crontab -e command.

2) user specific crontab files are named after the username, not userid.  If you change your username, your crontab will break.  This is a already a bug in launchpad.

3) The rumour about not being able to use a period "." in a crontab is false...at least on Ubuntu Hardy.  I am successfully running "myscript.sh" with no problems now.

4) The rumour about you being a member of the crontab group is also false.  Thanks to unutbu for this one.

5) Cron's log can be enabled by editing /etc/syslog.conf, but it won't give you any information you aren't already getting in syslog.

6) Authentication errors during a cron job are not put in syslog or the cron.log, only in auth.log. Check there if your job isn't running.  (this one kills me...)

7) The rumour about needing to have a newline or comments before or after your entry in crontab is false.

8) The rumour that you need to restart the cron service to have it re-read any of the crontabs is also false.

9) The rumour that using a minute indicator of "*/5" doesn't work also is false...works great on Hardy.

10) If you don't set the environment variables correctly in your crontab, then your script needs to use absolute paths for everthing and your script will not be able to run anything that requires X or graphical input.  See unutbu's post for these.

Thanks to all who helped.

---

### Post by unutbu on 2008-06-09
Congratulations on your excellent detective work (editing pam_truecrypt source? -- wow!) and thank you for the summary!

---

### Post by amaasbier on 2009-04-01
I know that this thread old already but I think that I can still add some useful information.

Since I am unable to edit source code to my needs I had to look for another solution. I had similar log messages like [this guy]("https://www.linuxquestions.org/questions/debian-26/pammount-prevents-cron-from-working-debian-sarge-360100/") so I tried the tips from the thread over there and it worked.
This error only appears to happen if you use cron and pam-mount together and edited a common configuration file instead of a specific one (i.e. GDM).
For me these files were '/etc/common-session' and '/etc/pam.d'. So I had to move the following line from one file to another:
@include common-pammount

And thanks for your investigation HDave.

---

### Post by mitchhb on 2009-04-06
Thank you for the helpful discussion.

I am using Hardy and find that a crontab entry without a newline doesn't run. This is confirmed by the crontab man page (below). So I think that the rumor about needing a newline is true.

[FONT="Courier New"]BUGS
Although cron requires that each entry in a crontab end in a newline character, neither the crontab command nor the cron daemon will detect this error. Instead, the crontab will appear to load normally. However, the command will  never  run. The best choice is to ensure that your crontab has a blank line at the end.[/FONT]

---

### Post by measekite on 2009-04-08
> **mike2357 said:**
> I generally prefer to use individual users' cron files, but mainly because that's how I learned.  Debugging cron commands can be difficult.  When I'm having trouble with one I send the output of the command to a file, as follows:

* * * * * /usr/bin/touch /tmp/test.file > OUT_CRON 2>&1

If cron is running, OUT_CRON will be written in the user's home directory.  The 2>&1 means to send error messages to the same output file as standard output, which in this case is OUT_CRON.

Good luck.  Incidentally, I tried your cron command and it worked fine.  If you solve the mystery, please post what happened.  I'd be curious to find out.

If you have 5 separate cron jobs for the same user do you have to use 5 different output names to avoid overwriting?

---

