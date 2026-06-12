---
title: "Automatically copying folder from one location to another to a fixed schedule."
date: 2019-03-14
forum: General Help
---

### Post by daitheboot on 2019-03-14
I am looking for an automated method to copy a folder  from my home folder to my NAS on according to a schedule. Can anyone point me in the general direct please. I am running Ubuntu 18.04.
I am not very proficient in bash but can usually muddle through with the ais of books and forums but not sure what I need to search for. 

Any help would be very welcome.
thanks
David

---

### Post by HermanAB on 2019-03-14
$ man rsync

There are examples at the bottom of the man page.

---

### Post by aromo2 on 2019-03-14
for the scheduling part:
```

$ man crontab
$ man 5 crontab

```

---

### Post by #&amp;thj^% on 2019-03-14
In order to do what you want, you need to figure out a command that will do what you want, and then execute it with cron at a given time.

For example, to simply copy the files from one location to another, you could use
```

rsync -a /origin /destination
```

and then schedule it to run with cron by running crontab -e and specifying
```

0 0 * * * /usr/bin/rsync -a /origin /destination
```

in the file. That will cause your rsync to run at midnight each day.
by "keeping them in sync" I mean it will make the destination directory an exact copy of the source. Rsync will only copy the files that have changed, including new ones.


Doing that each day will keep the two directories in sync. If you want to only copy files that have been created in the last day, that's a bit more difficult, but can be done with find with the --newer and -exec option to run a cp to copy the files.
Also a more complex way is something like what is found here: [https://www.alibabacloud.com/blog/how-to-automate-and-schedule-tasks-with-crontab-on-ubuntu-16-04_594117](https://www.alibabacloud.com/blog/how-to-automate-and-schedule-tasks-with-crontab-on-ubuntu-16-04_594117)

---

