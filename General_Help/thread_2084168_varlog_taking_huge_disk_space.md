---
title: "/var/log taking huge disk space"
date: 2012-11-14
forum: General Help
---

### Post by Rocket J Squirrel on 2012-11-14
Or huge on this machine anyway. /var/log has about 64GB of stuff in it. kern.log and syslog.1 are both massive. syslog is big.

What's not safe to delete in this directory?

---

### Post by dannyboy79 on 2012-11-14
anything with a number after it is safe to delete. they are just older log files. for example: syslog.1, syslog.2, kern.log.1, kern.log.2

look into /etc/logrotate.conf to set the size in which log files can be before they are backed up and then use the rotate count (3 is what I use) to only keep around 3 copies of old logs.

You may have some error you need to address though. Don't delete syslog or kern.log BUT you should open them and see what the repeating errors are.

---

### Post by Rocket J Squirrel on 2012-11-14
Thank you Dannyboy79,

kern.log is 38GB, syslog is 29GB. No one lives long enough to read the entirety of either, a quick glance shows not a whole lot interesting. I reckon they will be rotated out in a few weeks, if I understand logrotate.conf

---

### Post by steeldriver on 2012-11-14
Here's a one-liner that I cobbled together awhile back to look for recurring messages in big logfiles [NB it is a hack - particularly the way it attempts to remove the timestamps - it may help but don't rely on it]

```
$ for log in /var/log/{dmesg,syslog,kern.log}; do 
> echo "${log} :" 
> sed -e 's/\[[^]]\+\]//' -e 's/.*[0-9]\{2\}:[0-9]\{2\}:[0-9]\{2\}//' ${log} \
> | sort | uniq -c | sort -hr | head -10
> done

```

---

### Post by dannyboy79 on 2012-11-15
> **Rocket J Squirrel said:**
> Thank you Dannyboy79,

kern.log is 38GB, syslog is 29GB. No one lives long enough to read the entirety of either, a quick glance shows not a whole lot interesting. I reckon they will be rotated out in a few weeks, if I understand logrotate.conf
there is absolutely NO reason a log file should ever be more then say 1GB in size IMO and I am perplexed why Ubuntu default logrotate.conf doesn't specifiy a size. Your logs have to have some repeating message for the log file to get that large. 
do this from a terminal
```
tail /var/log/syslog
```
or
```
tail /var/log/syslog.1
```

Try to fix the offending repeating error FIRST AND FOREMOST but also set a default size for a log files within /etc/logrotate.conf
you can read about examples here (the online man page)
[http://linux.die.net/man/8/logrotate](http://linux.die.net/man/8/logrotate)

---

### Post by Rocket J Squirrel on 2012-11-15
Thanks, Dannyboy.

syslog is now empty, having been rotated out. syslog.1 has this tail:
> admin@sales-desktop:/var/log$ tail syslog.1
Nov 15 07:40:24 sales-desktop kernel: [68138.185696] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 15 07:40:24 sales-desktop kernel: [68138.185700] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 15 07:40:24 sales-desktop kernel: [68138.185704] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 15 07:40:24 sales-desktop kernel: [68138.185708] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 15 07:40:24 sales-desktop kernel: [68138.185712] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 15 07:40:24 sales-desktop kernel: [68138.185716] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 15 07:40:24 sales-desktop kernel: [68138.185720] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 15 07:40:24 sales-desktop kernel: [68138.185724] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
Nov 15 07:40:24 sales-desktop kernel: [68138.185728] [drm:intel_prepare_page_flip] *ERROR* Prepared flip multiple times
admin@sales-desktop:

I have no idea what that's about.

logrotate.conf is presently:
> # see "man logrotate" for details
# rotate log files weekly
weekly

# keep 3 weeks worth of backlogs
rotate 3

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

No "size" statements. I'll add a global size default of 1M, see how that works out. 

_steeldriver_, thanks for the script but it's not giving me any output that I can see. Maybe I'm looking in the wrong place.

---

### Post by dannyboy79 on 2012-11-15
1M would be 1 megabyte which is way to small IMO but you can make it whatever you want. 

Also, that error can be solved (it's really a bandade until the kernel is updated) by doing this.
create a file in /etc/ using root privaleges and paste the following within the file
```
gksudo gedit /etc/drirc
```
once gedit opens, paste the following within the file, save and close
```
<!--  2012-05-23 : added /etc/drirc file to prevent kern.log filling with -->
<!-- [drm:intel_prepare_page_flip] messages - see ubuntu Bug #765813 -->

<driconf>
    <device screen="0" driver="dri2">
        <application name="Default">
            <option name="vblank_mode" value="0" />
        </application>
    </device>
</driconf>
```

reboot for it to take affect and your syslog, kern.log, and dmesg should not be filled with that error anymore

---

### Post by Rocket J Squirrel on 2012-11-15
Again, thank you dannyboy79. Right now the filesystem has only 4GB of space available out of 77GB. The majority of the used space is in /var/log in the logs. syslog is now 0 (must have gotten rotated, syslog.1 is now 17GB, and kern.log is 47GB.

/etc/logrotate.conf has them set to rotation weekly. Is there a way to force a rotation, or two, to make the really big logs go away?

---

### Post by dannyboy79 on 2012-11-15
just delete kern.log and syslog.1, you don't need them for anything. If they are that big filled with that same error they aren't serving any purpose.

DId you incorporate the thing about driconf like I mentioned? otherwise your kern.log and syslog will just keep filling with that error. Also, did you add size 1000M to your logrotate.conf file? That would be 1gb log files.

---

### Post by Rocket J Squirrel on 2012-11-15
"Did you incorporate the thing about driconf like I mentioned? otherwise your kern.log and syslog will just keep filling with that error. Also, did you add size 1000M to your logrotate.conf file? That would be 1gb log files."

Aye, I did all that. Many thanks for your help.

---

### Post by kjohri on 2012-11-15
For more information about logrotate, refer to the link, 

[http://www.softprayog.in/tutorials/logrotate]("http://www.softprayog.in/tutorials/logrotate")

---

### Post by dannyboy79 on 2012-11-16
> **Rocket J Squirrel said:**
> "Did you incorporate the thing about driconf like I mentioned? otherwise your kern.log and syslog will just keep filling with that error. Also, did you add size 1000M to your logrotate.conf file? That would be 1gb log files."

Aye, I did all that. Many thanks for your help.Awesome, just mark the thread solved.

---

