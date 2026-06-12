---
title: "cron job not working"
date: 2008-03-09
forum: General Help
---

### Post by mailbox on 2008-03-09
Heya,

I've entered **0,20,40 * * * * xfdesktop -reload  >/dev/null 2>&1** with *crontab -e*, so that I can get a new, random background every 20 minutes. I know that *xfdesktop -reload* works; I have it as a rightclick-on-desktop option.
Thing is, :20 has passed, :40 just now passed, and nothing is happening. I've restarted cron, rebooted my machine, check that it's coming up by running *crontab -l* (and sure enough, it's in there). Hell, I even changed it to *** * * * * xfdesktop -reload  >/dev/null 2>&1**, but still with no luck. I have no idea what I'm doing wrong here, and as usual, #ubuntu is no help whatsoever.
Educate me, please? Thanks in advance.

---

### Post by Oldsoldier2003 on 2008-03-09
> **mailbox said:**
> Heya,

I've entered **0,20,40 * * * * xfdesktop -reload  >/dev/null 2>&1** with *crontab -e*, so that I can get a new, random background every 20 minutes. I know that *xfdesktop -reload* works; I have it as a rightclick-on-desktop option.
Thing is, :20 has passed, :40 just now passed, and nothing is happening. I've restarted cron, rebooted my machine, check that it's coming up by running *crontab -l* (and sure enough, it's in there). Hell, I even changed it to *** * * * * xfdesktop -reload  >/dev/null 2>&1**, but still with no luck. I have no idea what I'm doing wrong here, and as usual, #ubuntu is no help whatsoever.
Educate me, please? Thanks in advance.
please post the output of
```
 crontab -l 
```
so we can see that the command is properly entered in your crontab.

also for troubleshooting purposes enter this in a terminal:
```
xfdesktop -reload  >/dev/null 2>&1
``` because if it doesn't work then your cronjob wont work. I'm not real familiar with XFCE anymore but these are the obvious starting points to work out your issue.

---

### Post by mailbox on 2008-03-09
*crontab -l* returns: ```
dissonance@iridium:~$ crontab -l
* * * * * xfdesktop -reload  >/dev/null 2>&1 # new bg, 
# This file was written by KCron. Copyright (c) 1999, Gary Meyer
# Although KCron supports most crontab formats, use care when editing.
# Note: Lines beginning with "#\" indicates a disabled task.
```
and yes, *xfdesktop -reload  >/dev/null 2>&1* does indeed have the desired effect.

---

### Post by scottro on 2008-03-10
Sometimes, crontab has a shorter $PATH than other things.  You might try it with the whole path to xfcedesktop.  (I would guess /usr/bin, which crontab should see, but it doesn't hurt anything.)

If the xfcedesktop is a shell script, it could also be one of the paths in the script itself. 

For example, in FreeBSD, cron doesn't see /usr/local.  So I might have a /home/scottro/rsync.sh script. 
In cron I would have to put the whole path to the script /usr/home/scottro/rsync.sh.

In the rsync.sh script, I would have to put the whole path to rsync, that is, I'd have to do /usr/local/rsync whatever.  

Although that's a FreeBSD example, it happens in Linux as well from time to time.

---

### Post by Oldsoldier2003 on 2008-03-10
> **mailbox said:**
> *crontab -l* returns: ```
dissonance@iridium:~$ crontab -l
* * * * * xfdesktop -reload  >/dev/null 2>&1 # new bg, 
# This file was written by KCron. Copyright (c) 1999, Gary Meyer
# Although KCron supports most crontab formats, use care when editing.
# Note: Lines beginning with "#\" indicates a disabled task.
```
and yes, *xfdesktop -reload  >/dev/null 2>&1* does indeed have the desired effect.

make and save file named my.cron in your home dir with:

```
0,20,40 * * * *    xfdesktop -reload  >/dev/null 2>&1
```

then:
```
crontab -u dissonance my.cron
```

a crontab -l will verify your crontab is loaded.

edit: and as stated above you may need to give a an absolute path

---

### Post by mailbox on 2008-03-10
Hmmph.
I have **0,20,26,40 * * * *    /usr/bin/xfdesktop -reload  >/dev/null 2>&1** (/usr/bin is the correct path, I checked it.) as the contents of ~/.my.cron, and I ran *crontab -u dissonance .my.cron* as per your instructions, and made sure it was in there with *crontab -l* (it was), but still no luck. 21:26 passed and I still had the same background.

---

### Post by mailbox on 2008-03-10
I even changed it to *** * * * * /usr/bin/xfdesktop -reload >/dev/null 2>&1**, restarted cron afterwards, and still no luck.

---

### Post by Oldsoldier2003 on 2008-03-10
> **mailbox said:**
> Hmmph.
I have **0,20,26,40 * * * *    /usr/bin/xfdesktop -reload  >/dev/null 2>&1** (/usr/bin is the correct path, I checked it.) as the contents of ~/.my.cron, and I ran *crontab -u dissonance .my.cron* as per your instructions, and made sure it was in there with *crontab -l* (it was), but still no luck. 21:26 passed and I still had the same background.

hmm you might want to look in your logs then, because this should have worked... the crontab is loaded and the command works, so there might be a permissions issue somewhere. try looking in /var/log/auth.log for starters.

---

### Post by mailbox on 2008-03-10
Ahh, so that's where the log is.

Aww, crap.```
dissonance@iridium:~$ cat /var/log/auth.log | tail
Feb 19 18:09:01 iridium CRON[4499]: (pam_unix) session opened for user root by (uid=0)
Feb 19 18:09:01 iridium CRON[4499]: (pam_unix) session closed for user root
Feb 19 18:10:01 iridium CRON[4501]: (pam_unix) session opened for user dissonance by (uid=0)
Feb 19 18:17:01 iridium CRON[4572]: (pam_unix) session opened for user root by (uid=0)
Feb 19 18:17:01 iridium CRON[4572]: (pam_unix) session closed for user root
Feb 19 18:20:01 iridium CRON[4614]: (pam_unix) session opened for user dissonance by (uid=0)
Feb 19 18:29:55 iridium gdm[5148]: (pam_unix) session closed for user dissonance
Feb 19 18:30:01 iridium CRON[4671]: (pam_unix) session opened for user dissonance by (uid=0)
Feb 19 18:30:05 iridium gdm[4651]: (pam_unix) session opened for user dissonance by (uid=0)
Feb 19 18:30:19 iridium gdm[4651]: (pam_unix) session closed for user dissonance
```
I don't see anything unnatural in there.

---

### Post by Oldsoldier2003 on 2008-03-10
> **mailbox said:**
> Ahh, so that's where the log is.

Aww, crap.```
dissonance@iridium:~$ cat /var/log/auth.log | tail
Feb 19 18:09:01 iridium CRON[4499]: (pam_unix) session opened for user root by (uid=0)
Feb 19 18:09:01 iridium CRON[4499]: (pam_unix) session closed for user root
Feb 19 18:10:01 iridium CRON[4501]: (pam_unix) session opened for user dissonance by (uid=0)
Feb 19 18:17:01 iridium CRON[4572]: (pam_unix) session opened for user root by (uid=0)
Feb 19 18:17:01 iridium CRON[4572]: (pam_unix) session closed for user root
Feb 19 18:20:01 iridium CRON[4614]: (pam_unix) session opened for user dissonance by (uid=0)
Feb 19 18:29:55 iridium gdm[5148]: (pam_unix) session closed for user dissonance
Feb 19 18:30:01 iridium CRON[4671]: (pam_unix) session opened for user dissonance by (uid=0)
Feb 19 18:30:05 iridium gdm[4651]: (pam_unix) session opened for user dissonance by (uid=0)
Feb 19 18:30:19 iridium gdm[4651]: (pam_unix) session closed for user dissonance
```
I don't see anything unnatural in there.

the log should have showed the commands being executed as well. I'm at a loss right now, need to sit back and rethink what else might be wrong...

---

### Post by mailbox on 2008-03-10
Me too.
Hey, thanks for helping me so far though, sir. I truly appreciate it.

---

### Post by erginemr on 2008-03-10
I remember I needed to add the line "DISPLAY=:0." to instruct cron to use the current X screen for graphical programs. So, following this example:

```
# m h  dom mon dow   command
# 50 22 * * * DISPLAY=:0. gvim
```

you can try adding "DISPLAY=:0." without the quotes before the command.

---

### Post by Oldsoldier2003 on 2008-03-10
> **erginemr said:**
> I remember I needed to add the line "DISPLAY=:0." to instruct cron to use the current X screen for graphical programs. So, following this example:

```
# m h  dom mon dow   command
# 50 22 * * * DISPLAY=:0. gvim
```

you can try adding "DISPLAY=:0." without the quotes before the command.
argh! lol didn't think to ask him if it was a graphical program... good catch

---

### Post by dcstar on 2008-03-10
> **erginemr said:**
> I remember I needed to add the line "DISPLAY=:0." to instruct cron to use the current X screen for graphical programs.......


Correct, **cron **knows nothing about the graphical environment it runs in, people continually make the mistaken assumption that because something works in a user shell in their logged-in environment that it will work in a cron job - and as they find out, a lot of the time it doesn't.

BTW, any command starting with an "x" is usually a good indication that it is an X windows app.

---

### Post by Oldsoldier2003 on 2008-03-10
> **dcstar said:**
> Correct, **cron **knows nothing about the graphical environment it runs in, people continually make the mistaken assumption that because something works in a user shell in their logged-in environment that it will work in a cron job - and as they find out, a lot of the time it doesn't.

BTW, any command starting with an "x" is usually a good indication that it is an X windows app.

Grins, ture about the x starting the name, was just hung up over the fact it was a xubuntu program so the red flag never went up. guess its time to get either coffee or sleep!

---

### Post by mailbox on 2008-03-10
Alright, added. Let's see if this works.

---

### Post by mailbox on 2008-03-10
YES! It works! Thanks to all of you so much!

I never knew why 'x' was in app names. The more you know!
Excellent, I'm off to enjoy this now. Thanks again!

---

