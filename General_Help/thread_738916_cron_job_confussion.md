---
title: "cron job confussion"
date: 2008-03-29
forum: General Help
---

### Post by pabc on 2008-03-29
I've a cron job to call my antispam program (mailfilter) every 10 minutes

crontab -e shows;

```
*/10 * * * * mailfilter
```

Running mailfilter from a termianl works fine but the cron job doesnt seem to work.

If I go into the GUI (scheduled tasks in the menu) and execute the task it works fine from there.

I got a message saying recurring tasks run from ~ so I stuck a script in ~ called .10minutely which called mailfilter which works fine if called from a terminal or executed from the cron gui but it doesnt get called every 10 minutes if I change my chromtab to 

```
*/10 * * * * ~/.10minutely
```

I'm clearly missing something obvious - any ideas please?

P

---

### Post by dcstar on 2008-03-29
> **pabc said:**
> I've a cron job to call my antispam program (mailfilter) every 10 minutes

crontab -e shows;

```
*/10 * * * * mailfilter
```

Running mailfilter from a termianl works fine but the cron job doesnt seem to work.

If I go into the GUI (scheduled tasks in the menu) and execute the task it works fine from there.
........
```
*/10 * * * * ~/.10minutely
```

I'm clearly missing something obvious - any ideas please?

P

Cron does** not** run in the same environment as a user shell.

Put in full path names unless you can guarantee that the cron environment has the right path settings.

---

### Post by pabc on 2008-03-29
OK, having checked with /usr/bin/mailfilter and just mailfilter as the cron job both are starting.

My problem appears to be that the in either case the cron initiated job bails shortly after starting

The log for the cron inititiated job shows...

```
mailfilter: 0.8.1 querying xxxxxxxxx@pop.mail.yahoo.com on Sat Mar 29 11:57:01 2008.
mailfilter: Examining 36 message(s).
mailfilter: Pass: "xxxxxxx" rxxxxx.com>: [b3ta] "We shagged Paul McCartney and all we got was this lousy newsletter", Thu, 20 Mar 2008 13:22:02 -0000 [Score: 0].
mailfilter: Pass: <xxxx@xxxxxx>: Alan xxxxxxxx, Thu, 20 Mar 2008 22:42:11 -0000 [Score: 0].
mailfilter: Allow: x@x: FW: Re: FLM, Thu, 20 Mar 2008 23:56:03 +0100 ["^From:.*xx@xxxxxxxxx\.com" matches "From: xxxxxx@x.com"].
mailfilter: Pass: <editor@runnersworld.co.uk>: RW Marathon Training Newsletter - Week 14, Fri, 21 Mar 2008 01:27:58 -0000 [Score: 0].
mailfilter: Pass: WestEnd Runners <xxxxxx@xxxxxxxx>: RE: Westend 8, Sun, 23 Mar 2008 10:55:05 +0000 [Score: 0].
```

ie, it stops at the 8th message on the first account

where as if I do it from the terminal it checks all 36 messages AND then goes on to complete a seconf pop3 account account correctly.

Any idea why the cron version doesnt complete?

---

### Post by Athelstan101 on 2008-03-29
Maybe the script needs to be run under superuser.
```
$ sudo bash
# crontab -e
```

---

### Post by justleen on 2008-03-29
bit far fetched, maar are you using any other relative paths in the mailfilter?
I've had similair issues once, cron bailing out for nothing, and when i redefined $PATH in my script, it worked fine.
you could do an ```
echo $PATH
```
paste the output into your script
PATH=<output>

do you see any other log entries ? messages log, error log, auth log, anything?
let the cron run, then do a ls -ltr on /var/log/ , it will place the last modified files at the bottom - tht way you can easily spot which logs are updated..

---

### Post by pabc on 2008-03-29
running it again from cron;

auth.log has this appended;
```
Mar 29 13:10:01 study CRON[15624]: pam_unix(cron:session): session opened for user phil by (uid=0)
```

and syslog has this appended.
```
Mar 29 13:11:01 study /USR/SBIN/CRON[15648]: (phil) CMD (mailfilter # JOB_ID_3)
```

and my $PATH is;
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

so I have a script now like
```
#!\bin\bash

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
mailfilter
```

which when run through cron does exactly the same so I dont think the PATH var is playing a part in my problem.

any other ideas.

P

---

### Post by pabc on 2008-03-29
anyone? please?

---

### Post by drs305 on 2008-03-29
As mentioned earlier, cron doesn't recognize relative paths.

Change ~/.10minutely to /home/USERNAME/.10minutely

I don't know if that's the only problem but it will help.

---

### Post by pabc on 2008-03-29
nope. in both cases the job starts but doesnt complete. very strange.

---

### Post by Feller on 2008-03-30
I've also experienced much agony getting cron to behave, and this is what worked for me.
The previous posts are correct in saying that the cron environment must be set correctly for  cron to function, but how to set them is the question.

The following link details the required actions/information to get a script to run under cron without extensive knowledge of cron or the environment itself.

[http://aplawrence.com/Unixart/cron.html]("http://aplawrence.com/Unixart/cron.html")

In a nutshell, create a temporary 'at' job to create the environment required to run the script. Then copy the environment setup created by the 'at' job to the script itself.

This appears to allow the script to generate the appropriate environment to run the required commands independent of cron.

Hope this helps!

---

### Post by pabc on 2008-03-30
albsolutly brilliant solution. Thanks.

I created an AT job for an hours time which called 'ls' then found the script at had created in var/spool/cron/atjobs then copied all of it to a script in my home dir and just replaced the final line (the 'ls' command) with mailfilter and called it from cron and it worked fine.

Thank you

---

