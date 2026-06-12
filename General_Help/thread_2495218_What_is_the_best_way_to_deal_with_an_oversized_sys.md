---
title: "What is the best way to deal with an oversized syslog in 22.04"
date: 2024-02-11
forum: General Help
---

### Post by foxsquirrel on 2024-02-11
Logrotate is active however this file has grown to over 120Gb. 

Is it okay to delete it??

---

### Post by TheFu on 2024-02-12
```
journalctl --disk-usage   # See log file disk use
  sudo journalctl --vacuum-size=200M    # Drop log file size to 200M, if possible.
  sudo journalctl --vacuum-time=10d     # Drop logs, over 10 days old
```

Then set the maximums you want to allow in the journald.conf file. It is well commented.

For old style logs, which are gone in Debian 12, logrotate is the method.  There are plenty of examples in the config directory that can be followed. I don't think logrotate config options have changed much the last 20 yrs, so any tutorial or how-to guide you find online should be good enough.

Don't be afraid to look at text files and read them.  They are usually pretty clear for what they do and don't do.  And if you modify logrotate configs be certain to either HUP or restart the service fo rthose changes to get picked up.  Same for journald.conf.

And lastly, both of these tools and their config files are well documented in the manpages on your system.  Manpages are there to be read, not just eat storage.

---

### Post by foxsquirrel on 2024-02-12
> **TheFu said:**
> ```
journalctl --disk-usage   # See log file disk use
  sudo journalctl --vacuum-size=200M    # Drop log file size to 200M, if possible.
  sudo journalctl --vacuum-time=10d     # Drop logs, over 10 days old
```

Then set the maximums you want to allow in the journald.conf file. It is well commented.

For old style logs, which are gone in Debian 12, logrotate is the method.  There are plenty of examples in the config directory that can be followed. I don't think logrotate config options have changed much the last 20 yrs, so any tutorial or how-to guide you find online should be good enough.

Don't be afraid to look at text files and read them.  They are usually pretty clear for what they do and don't do.  And if you modify logrotate configs be certain to either HUP or restart the service fo rthose changes to get picked up.  Same for journald.conf.

And lastly, both of these tools and their config files are well documented in the manpages on your system.  Manpages are there to be read, not just eat storage.



The config shows weekly. I cannot open it due to the size, the syslog.1 file is small.

```
/var/log/syslog
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
        /usr/lib/rsyslog/rsyslog-rotate
    endscript
}
```

---

### Post by deadflowr on 2024-02-12
Run tail on the large file to see the last lines
When something is that big it's usually because lines keep endlessly repeating.
I'd run
```
tail -n 100 /var/log/syslog
```
that'll show the last 100 lines which should be enough, (well, normally it would be) to see what's causing it to be so big.

---

### Post by foxsquirrel on 2024-02-12
> **deadflowr said:**
> Run tail on the large file to see the last lines

```
tail -n 100 /var/log/syslog
```


Thank you, I should have known that....

It does look like VMware is a big contributor, nouveau has a few
```
Feb 12 00:51:37 eng-dev2 kernel: [26189.635362] nouveau 0000:01:00.0: DRM: DDC responded, but no EDID for DP-6
Feb 12 00:51:42 eng-dev2 kernel: [26194.939434] nouveau 0000:01:00.0: DRM: DDC responded, but no EDID for DP-6

```

Not sure how to read this block:
```
Feb 12 07:07:09 eng-dev2 gnome-shell[1786]: Window manager warning: Overwriting existing binding of keysym 31 with keysym 31 (keycode a).
Feb 12 07:07:09 eng-dev2 gnome-shell[1786]: Window manager warning: Overwriting existing binding of keysym 32 with keysym 32 (keycode b).
Feb 12 07:07:09 eng-dev2 gnome-shell[1786]: Window manager warning: Overwriting existing binding of keysym 33 with keysym 33 (keycode c).
Feb 12 07:07:09 eng-dev2 gnome-shell[1786]: Window manager warning: Overwriting existing binding of keysym 34 with keysym 34 (keycode d).
Feb 12 07:07:09 eng-dev2 gnome-shell[1786]: Window manager warning: Overwriting existing binding of keysym 35 with keysym 35 (keycode e).
Feb 12 07:07:09 eng-dev2 gnome-shell[1786]: Window manager warning: Overwriting existing binding of keysym 36 with keysym 36 (keycode f).
Feb 12 07:07:09 eng-dev2 gnome-shell[1786]: Window manager warning: Overwriting existing binding of keysym 37 with keysym 37 (keycode 10).
Feb 12 07:07:09 eng-dev2 gnome-shell[1786]: Window manager warning: Overwriting existing binding of keysym 38 with keysym 38 (keycode 11).
Feb 12 07:07:09 eng-dev2 gnome-shell[1786]: Window manager warning: Overwriting existing binding of keysym 39 with keysym 39 (keycode 12).

```

This is all just moments ago, screen blanking was active, no user present.

---

### Post by TheFu on 2024-02-12
Gnome issues. Can you stop using Gnome? Use a different DE?

Did you run the journalctl commands to clean up logs?
Did you set the max size in the logrotate config to force rotation?  It doesn't have to be time-based.
For example, 
```
/var/log/libvirt/libxl/*.log {
        **size 2097153**
        missingok
        rotate 4
        compress
        delaycompress
        copytruncate
}
```

---

### Post by foxsquirrel on 2024-02-12
Yes, I ran the journalctl commands you posted.

Modified the /etc/logrotate.d/rsyslog

Here is the file with mods:

```
/var/log/syslog
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
        su **** *****
        maxsize 100k
        minsize 100k
        rotate 4
        daily
        missingok
        notifempty
        compress
        delaycompress
        sharedscripts
        postrotate
                /usr/lib/rsyslog/rsyslog-rotate
        endscript
}


```

then forced an update
```
sudo logrotate -f /etc/logrotate.d/rsyslog
```

Then it would not allow me to do that, it responds read only. Not sure what direction to go now.
Since it is now set to daily, maybe tomorrow it will be updated on its own?
```
sudo logrotate -f /etc/logrotate.d/rsyslog
error: unable to open /var/log/syslog.1 (read-only) for compression: Permission denied
error: unable to open /var/log/kern.log.1 (read-only) for compression: Permission denied
error: unable to open /var/log/auth.log.1 (read-only) for compression: Permission denied

```

Update:

Just cleared it out using:

```
                 sudo truncate -s [COLOR=#2aa198]0[/COLOR] /var/log/syslog   
```

I will have to check on it and see if they log is really being throttled back to the 100k size in the updated config file.

---

