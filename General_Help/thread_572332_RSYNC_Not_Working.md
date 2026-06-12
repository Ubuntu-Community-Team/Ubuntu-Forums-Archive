---
title: "RSYNC Not Working"
date: 2007-10-10
forum: General Help
---

### Post by CarlosinFL on 2007-10-10
Guys - I set up 7.04 to sync my home directory with an external usb drive every 5 minutes. I have added a new file to my home directory and it has yet to show up on /media/disk for the past hour and I don't understand why. The RSYNC is setup via CRON to run every 5 minutes so this makes no sense to me...

Can anyone please tell me what is wrong?

Here is my RSYNC command in crontab.

```
cwilliams@cwilliams:~$ crontab -l
# m h  dom mon dow   command
5 * * * * rsync --delete -rdtvu /home/cwilliams/ /media/disk
cwilliams@cwilliams:~$ ls
BEWS_11D.7170_LINUX-UNIX-MAC-NT4_AGENTS.2.tar.gz  idelab revised 8-8-06.vsd  permission.txt   wallpaper
contact.txt                                       linux_commands.txt         phonelist.txt    whitelist.txt
contact.txt~                                      mailman.txt                spam_lookup.txt  whitelist.txt~
create_calendar.txt                               mysql.txt                  stricom_vlk.txt
Desktop                                           old_users                  symantec
cwilliams@cwilliams:~$ ls /media/disk/
contact.txt          Desktop                    mailman.txt  permission.txt   stricom_vlk.txt  whitelist.txt
contact.txt~         idelab revised 8-8-06.vsd  mysql.txt    phonelist.txt    symantec         whitelist.txt~
create_calendar.txt  linux_commands.txt         old_users    spam_lookup.txt  wallpaper

```

As you can see /media/disk is missing the BEWS* tarball that is present in /home/cwilliams. That file has been there for two hours. :confused:

---

