---
title: "Is this a cron script?"
date: 2024-11-28
forum: General Help
---

### Post by wyattwhiteeagle on 2024-11-28
Seen it at...
[https://www.reddit.com/r/linux4noobs/comments/ri24uj/how_do_i_delete_logs_and_also_stop_the_hard_drive/?sort=old](https://www.reddit.com/r/linux4noobs/comments/ri24uj/how_do_i_delete_logs_and_also_stop_the_hard_drive/?sort=old)

If this indeed is a cron script...isn't there some instructions missing?
Instructions such as "how to give file execute permissions", "what permissions to set for a cron or anacron file or how to set those permissions" and "what needs to be put into the fstab file or into 'autofs'?

> The script below will clean old and rotated logs from /var/log.


Save the script as: /usr/local/bin/cleanlogs.sh and give the file execute permission.


Once a week run the command: sudo /usr/local/bin/cleanlogs.sh


```
#!/usr/bin/bash
#
#Delete all .gz and rotated file
if [ $(whoami) != 'root' ]; then
echo
echo "Must be root to run $0"
echo
exit 1;
fi
#
echo "cleaning old log files"
find /var/log -type f -regex ".*\.gz$" | xargs rm -Rf
find /var/log -type f -regex ".*\.[0-9]$" | xargs rm -Rf
find /var/log -type f -regex ".*\.old" | xargs rm -Rf
echo "finished cleaning old log files"
exit
```

---

### Post by yancek on 2024-11-28
No, it is just a script to remove/rotate log files.  I don't see any reference in the thread to cron.    If you want to run it on a regular basis, you can use cron or anacron to do it.  If you are having a problem with acquiring large log files, it would be a good idea to look at the logs and find what the problem is and rectify it.The page at the link below discusses using cron in some detail.  Two things people neglect to do when using cron is to make the script they are using executable and to have a full path in the cron entry to the location of the script.  The site below shows example entries and explains them.  If this isn't satisfactory for you, it should be quite easy to find more sites explaining doing a simple online search for 
'how to use cron in linux'.

 [https://www.geeksforgeeks.org/crontab-in-linux-with-examples/](https://www.geeksforgeeks.org/crontab-in-linux-with-examples/)

A more detailed explanation at the link below.

 [https://www.ibm.com/docs/kk/aix/7.1?topic=c-crontab-command](https://www.ibm.com/docs/kk/aix/7.1?topic=c-crontab-command)

---

### Post by wyattwhiteeagle on 2024-11-28
> **yancek said:**
> No, it is just a script to remove/rotate log files.  I don't see any reference in the thread to cron.    If you want to run it on a regular basis, you can use cron or anacron to do it.  If you are having a problem with acquiring large log files, it would be a good idea to look at the logs and find what the problem is and rectify it.The page at the link below discusses using cron in some detail.  Two things people neglect to do when using cron is to make the script they are using executable and to have a full path in the cron entry to the location of the script.  The site below shows example entries and explains them.  If this isn't satisfactory for you, it should be quite easy to find more sites explaining doing a simple online search for 
'how to use cron in linux'.

 [https://www.geeksforgeeks.org/crontab-in-linux-with-examples/](https://www.geeksforgeeks.org/crontab-in-linux-with-examples/)

A more detailed explanation at the link below.

 [https://www.ibm.com/docs/kk/aix/7.1?topic=c-crontab-command](https://www.ibm.com/docs/kk/aix/7.1?topic=c-crontab-command)
Those two things are things I've neglected once before mainly because I didn't know how to set permissions or what permissions to set for a script being put in a directory that requires sudo rights and the cron directory...do I create a seperate executable file or do I add the full path into one of the files that are already there?

Rectifying issue's is before setting a script like this into cron or anacron.
At least the issue's that come after upgrading to the next release.
For that, I'm still in the learning process about filtering through the logs and applying the rectifications.

One thing I'm learning, some errors are because of some configuation I have set to minimize/rectify another more major issue.
I guess that could be said as "I hide the more major issue" which I need to get out of that bad habit.

The main issue's I'm noticing currently are slow execute times of packages, memory leaks, not having something set up to quickly identify issue's and apply the rectifications, and not having backups (not any real backups). I just save everything and spend hours upon hours of transferring files and reconfiguring to my likings.

I don't plan to set a script like this in cron or anacron before rectifying, not "hide", the warning/error message.
Some new users believe that if they dont see the error/warning then there's nothing to worry about until they find out they needed to address those before they couldn't address them and end up losing most or all of whats important and valuable to them.

---

### Post by ActionParsnip on 2024-11-28
Doesn't logrotate do this automatically??

---

### Post by wyattwhiteeagle on 2024-11-28
> **ActionParsnip said:**
> Doesn't logrotate do this automatically??
It does, however I believe the parameter in logrotate to delete old logs is set to not delete any old logs until the archived logs accumilated reach an astounding amount of disk space usage.


It can be reconfigured in logrotate.d.
I believe that's the file name where it can be reconfigured to delete old archived logs after a certain amount of time.


But I'm not too certain if logrotate deals with the 2 command lines
```
find /var/log -type f -regex ".*\.[0-9]$" | xargs rm -Rf
find /var/log -type f -regex ".*\.old" | xargs rm -Rf
```

---

### Post by ActionParsnip on 2024-11-28
> **wyattwhiteeagle said:**
> It does, however I believe the parameter in logrotate to delete old logs is set to not delete any old logs until the archived logs accumilated reach an astounding amount of disk space usage.


It can be reconfigured in logrotate.d.
I believe that's the file name where it can be reconfigured to delete old archived logs after a certain amount of time.


But I'm not too certain if logrotate deals with the 2 command lines
```
find /var/log -type f -regex ".*\.[0-9]$" | xargs rm -Rf
find /var/log -type f -regex ".*\.old" | xargs rm -Rf
```

You can check the config in /etc/logrotate.conf which will use the files in /etc/logrotate.d/
Logs are kept for a number of days typically, rather than size as far as I am aware

---

### Post by wyattwhiteeagle on 2024-11-28
> **ActionParsnip said:**
> You can check the config in /etc/logrotate.conf which will use the files in /etc/logrotate.d/
Logs are kept for a number of days typically, rather than size as far as I am aware
Thank you for the correction on the file name.
As far as the days vs size...you more than likely know better than I.
Reading a tutorial online, though I dont automatically trust them as they tend to have a specific goal to promote some form of GUI, seems like a size can be configured as well.
As I add a configuration line in each of the default files in logrotate.d...
(without changing the basic layout, of course)
```

rotate 0
daily
maxsize 10M

```

---

### Post by yancek on 2024-11-28
With regard to your questions about cron, the simplest way to create and edit an entry in cron is to use a terminal and as a user, just type:  crontab -e
Use the template/examples in the link I posted to create an entry.  The permissions to execute and the owner (root or user) will need to be on the script and not in your cron entry.

---

