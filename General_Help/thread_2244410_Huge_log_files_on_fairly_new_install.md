---
title: "Huge log files on fairly new install"
date: 2014-09-16
forum: General Help
---

### Post by newb85 on 2014-09-16
I was notified this morning that I'm running out of disk space on my 275GB Ubuntu partition.  Being a little surprised by this, I checked, and half of it is occupied by /var/log.  Specifically, syslog and kern.log are each about 65GB.  I understand that if they aren't purged, log files do build up, but I did a fresh install about 4 months ago.  Any ideas why this happened so quickly?  Should I just go ahead and delete those two files and let the system start building them up again.  (If I do, I'll watch to see if they keep growing so fast.)

---

### Post by slickymaster on 2014-09-16
The only way I see to figure out what's the problem is actually to take a look inside those log files and to see what error messages are causing the files to grow that large.

One other thing is **logrotate**, which should take care of compressing, rotating and backing up the log files.

---

### Post by newb85 on 2015-02-22
I've made changes to logrotate.conf so that logs are rotated daily instead of weekly, and compressed.  But will that affect both syslog and kern.log?

*Edit: I've reverted the changes*  Looking back at /var/log, it looks like they were already being compressed (even though the "compress" line was commented out in logrotate.conf).  kern.log had 4 backlogs, and syslog had 7 (even though logrotate.conf was set to "rotate 4").  Is it possible logrotate isn't reading the settings from logrotate.conf?

---

### Post by newb85 on 2015-02-22
> **slickymaster said:**
> The only way I see to figure out what's the problem is actually to take a look inside those log files and to see what error messages are causing the files to grow that large.

I don't remember the problem being so consistent.  I just looked at syslog, and it seems to be filled almost entirely with copies of one complaint.
```
Feb 22 01:17:32 gerber-Satellite-P755 kernel: [96435.155865] mei_me 0000:00:16.0: no destination client found 0x00000985
```

But I don't know what this means...

---

### Post by tgalati4 on 2015-02-22
A google search reveals:  [http://askubuntu.com/questions/561324/mei-me-00000016-0-no-destination-client-found-0x00002285-spamming-logfile](http://askubuntu.com/questions/561324/mei-me-00000016-0-no-destination-client-found-0x00002285-spamming-logfile)

---

### Post by newb85 on 2015-02-22
I had seen that.  Didn't seem all that helpful, though.  I'll see what I can find in the BIOS.

---

### Post by newb85 on 2015-02-23
I checked the BIOS.  Wake on LAN is already disabled.  Anyone have any better explanation/information?

---

### Post by pmi2 on 2015-02-23
There seems to be a more detailed discussion, here:

[http://forum.ubuntuusers.de/topic/kern-log-und-syslog-1-zu-gross/](http://forum.ubuntuusers.de/topic/kern-log-und-syslog-1-zu-gross/)

unfortunately it is in German (!), so I can just barely make out that it suggested a partial solution in directing the output of the offending modules to a separate log file, and then setting limits on that new logfile, leaving the other logs intact.  In other words, the OP in that thread had a solution for the disk filling up, but not for preventing the problem.

That thread is referring to some kind of wakeup function on a laptop.  There may be more info there, but not easy to make out for me b/c the language barrier.

---

### Post by newb85 on 2015-02-24
Thanks, pmi!  That was interesting.  Diverting the output of the offending module to a size-limited log file is a creative way of controlling it.  The reality, though, is that the problem seems to have stopped after a day.  (I have one syslog file that's about 51GB.  It's predecessor is .35 GB, and the one before that 5.2 KB.  The one following the peak came in at 21  MB.)  I'm content to move on without changing my system in hopes that the problem won't resurface.  I've done some cleaning, so if it does, it probably won't fill my drive anyways.

However, I'm still a little baffled by how syslog is being rotated.  If I 
```
ls -l /var/log | grep syslog
```
I see that syslog was rotated daily, and kept for seven days.  However, my /etc/logrotate.conf file has:
```
# see "man logrotate" for details# rotate log files weekly
weekly


# use the syslog group by default, since this is the owning group
# of /var/log/syslog.
su root syslog


# keep 4 weeks worth of backlogs
rotate 4


# create new (empty) log files after rotating old ones
create


# uncomment this if you want your log files compressed
#compress


# packages drop log rotation information into this directory
include /etc/logrotate.d


# no packages own wtmp, or btmp -- we'll rotate them here
/var/log/wtmp {
    missingok
    monthly
    create 0664 root utmp
    rotate 1
}


/var/log/btmp {
    missingok
    monthly
    create 0660 root utmp
    rotate 1
}


# system-specific logs may be configured here
```
and there is no file about syslog in /etc/logrotate.d.

My interpretation of the config file would be to rotate syslog weekly and keep it for four weeks.  Perhaps what it's doing is the default behavior, since there's no specific section in logrotate.conf for syslog?

Could someone clear this up for me?

---

### Post by pmi2 on 2015-02-24
Are you sure about your /etc/logrotate.d? 

Not sure about the terminology here, but basically you would go to logrotate.d to change your actual settings from daily to something else.  

My logrotate.d (as installed, and not edited by me) shows that syslog is rotated daily, and last seven copies are kept.   This section:

> 
/var/log/syslog
{
    rotate 7
    daily
    missingok
    notifempty
    delaycompress
    compress
    postrotate
        reload rsyslog >/dev/null 2>&1 || true
    endscript
}


---

### Post by newb85 on 2015-02-24
Nope. 
logrotate.d is a directory with config files for specific logs.   I don't have one for syslog.  The section you showed is absent from my logrotate.conf file, too.

---

### Post by pmi2 on 2015-02-24
> **newb85 said:**
> Nope. 
logrotate.d is a directory with config files for specific logs.   I don't have one for syslog.  The section you showed is absent from my logrotate.conf file, too.Yes, sorry.  Too much cut and paste, too little actual thinking on my part... :(

this file: /etc/logrotate.d/rsyslog

I have two sections, the first is what I posted above, the second covers other logs.

> 
/var/log/syslog
{
    rotate 7
    daily
    missingok
    notifempty
    delaycompress
    compress
    postrotate
        reload rsyslog >/dev/null 2>&1 || true
    endscript
}

/var/log/mail.info
/var/log/mail.warn
/var/log/mail.err
/var/log/mail.log
/var/log/daemon.log
/var/log/kern.log
/var/log/auth.log
/var/log/user.log
/var/log/lpr.log
/var/log/cron.log
/var/log/debug
/var/log/messages
{
    rotate 4
    weekly
    missingok
    notifempty
    compress
    delaycompress
    sharedscripts
    postrotate
        reload rsyslog >/dev/null 2>&1 || true
    endscript
}


---

### Post by newb85 on 2015-02-25
Oh, you're right, pmi2.  When I scanned the contents of logrotate.d visually, I overlooked rsyslog.  It is exactly as you say.  It makes sense, now.

---

### Post by newb85 on 2015-02-25
...but I just found something that doesn't.  The current syslog file is only 21MB, but it still contains scores of the offending entries from Feb 22.  That was 3 days ago.  It also has quite a few entries from the 23rd.  Why would those entries appear in syslog, and not one of the archived files?  Perhaps it had something to do with how large syslog was?

---

### Post by pmi2 on 2015-02-25
1) I don't know why there are multiple dates in your log files, but that may be a separate issue.

2) Your log files are still very large.  Unless you are doing something very elaborate with your system, and you know why they are filling up (besides mei-me), I would try to get this sorted.  Really.

3) There are a lot of posts regarding multiple mei-me messages, and mei-me spamming the logs, not just in Ubuntu, but other distros also.  There seem to be more on Euro web sites, and some (OK most) are over my head.  I did NOT see a perfect solution, just workarounds, and no single workaround or patch.  I think you have some options to try, but not a single solution guaranteed to work.

MEI is also called "Intel Management Engine Interface".  You can try to disable MEI in the BIOS.  There are some references on how to do that, and it seems to solve some of the issues, but not all.

It looks like mei and mei-me are kernel modules that you have (some) control over.  I can remove them from my system without breaking stuff, but there is no telling about yours.

You can try to blacklist the module, but if something else calls for it, it may load anyway, so that may be an exercise in futility.

I think you can remove this module safely using rmmod, or modprobe -r

rmmod [-w] [-v] [modulename] 

(-w for wait until module is not active, and -v for verbose so you can see what you are doing)

example:

sudo rmmod -w -v mei-me

If you go this route (removing the module), you should probably run lsmod before and after, to make sure it is really gone, and then check the log for the messages.  If they are gone, you can look into removing the module automatically immediately on boot.

If you find a solution that works, please post it for others, I bet this is causing a few more people headaches, and should probably be dealt with by someone above my paygrade... :D

---

### Post by newb85 on 2015-02-26
I don't know that I'm doing anything elaborate.  I run virtualbox on my system to do some testing.  I have a few extra packages installed.  

I can't seem to find anything in the BIOS about disabling Intel Management Engine Interface.

My current syslog (which apparently hasn't been rotated since the 23rd?) comes in at 21 MB, but if I strip it of all mei_me entries, it's a mere 729kB.  Is that alarming?

---

### Post by pmi2 on 2015-02-26
Less than 1 MB size in the current syslog is not alarming.  Mine reaches around 3~400K before is is compressed and archived, and less than 100K after (the .gz files).  I would examine what is left for other unexpected error messages.

Here is a link to a post by someone who disabled it in his BIOS, but I have seen other comments from people who tried the same fix unsuccessfully.  In any case it is not really a fix (having to disable part of your BIOS is a kludge, not a fix) there are posts elsewhere from people whose system is basically locked up by a similar error, and some may just give up.

[http://askubuntu.com/questions/561324/mei-me-00000016-0-no-destination-client-found-0x00002285-spamming-logfile](http://askubuntu.com/questions/561324/mei-me-00000016-0-no-destination-client-found-0x00002285-spamming-logfile)

The answer for why the log is not being rotated may be in the .conf file, or in /etc/logrotate.d/rsyslog.  Rotate has a lot of options, so you may have to examine those line by line.

---

### Post by pmi2 on 2015-02-27
> **newb85 said:**
> ... I can't seem to find anything in the BIOS about disabling Intel Management Engine Interface. ...Just to cover all bases, and for anyone else reading, on my older Intel mobo the ME options are not accessible from the System BIOS, so in that case,  pressing <F2> on boot would take you to the wrong place. 

I have to press <ctrl><P> to access the "Intel Management Engine BIOS Extensions" screen. I am  not sure on other motherboards/chipsets.

---

