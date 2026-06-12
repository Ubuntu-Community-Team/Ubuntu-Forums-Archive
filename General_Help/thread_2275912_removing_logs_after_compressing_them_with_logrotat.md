---
title: "removing logs after compressing them with logrotate"
date: 2015-04-29
forum: General Help
---

### Post by Raner on 2015-04-29
I am trying to remove the text file logs after compressing them with logrotate. 

I successfully have the log moved to a folder for old logs using the olddir setting, and compressed to a logname.gx file using the compress setting, but the logfile as a text file is ALSO moved, when I just want to delete that outright. logrotatedoes delete the logfile from the original directory the log was in, but along with creating a compressed .gz file for the log just rotated, it also moves the original text version of the log. I only want to keep the compressed.gz versions. Is there a setting to do this or do I just need to setup some sort of cron job to delete all non .gz files from the folder that stores old logs?

I have read the man page online here but could not find the appropriate setting: [http://linux.die.net/man/8/logrotate](http://linux.die.net/man/8/logrotate)

This is what my logrotate configuration file looks like for this log:

```
/path/to/mylog.log {
#for testing
    rotate 50000
    daily
#for testing
    size 1k
    compress
    notifempty
    sharedscripts
    missingok
    nomail
    dateext
    dateformat -%Y-%m-%d-%s
    su root root
    olddir /path/to/old-log-folder
}
```

On running the logrotate command with this configuration this happens:

/path/to/log/mylog.log - log.log is deleted

/path/to/old-log-folder/mylog-(with dateformat).log is created, and mylog-(with dateformat).gz is created.

I only want the .gz file, not the uncompressed version.

---

