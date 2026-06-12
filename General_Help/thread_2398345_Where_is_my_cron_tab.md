---
title: "Where is my cron tab?"
date: 2018-08-10
forum: General Help
---

### Post by ulao3 on 2018-08-10
When I use crontab -e where does it go?

I made a cron job with crontab - e

0 0 1 1,6 * root rsync -a / /home/backups

but where is it?

**ls cron*.***
[COLOR=#ff0000]cron.d:
anacron  mdadm  popularity-contest

cron.daily:
0anacron    bsdmainutils      man-db   popularity-contest
apache2     cracklib-runtime  mdadm    samba
apport      dpkg              mlocate  ubuntu-advantage-tools
apt-compat  logrotate         passwd   update-notifier-common

cron.hourly:

cron.monthly:
0anacron

cron.weekly:
0anacron  apt-xapian-index  man-db  update-notifier-common
[/COLOR]

---

### Post by #&amp;thj^% on 2018-08-10
Just a Note: it's not recommended to handle these files by hand. Per crontab man page:

    > Each user can have their own crontab, and though
    these are files in /var/spool/cron/crontabs, they are not
    intended to be edited directly.
Example:
```
cd /var/spool/cron/
bash: cd: /var/spool/cron/: Permission denied

```

Files under /var/spool are considered temporary/working, that's why they will probably get deleted during an upgrade, though a closer look at the cron package's upgrade scripts may shed some light on this.

Anyway, it's always a good practice to back up your cron entries or keep them in a file in your home directory.


I'ts stored inside /var/spool/cron/crontabs folder under username.

---

### Post by SeijiSensei on 2018-08-10
I prefer to use /etc/crontab for things that require root access. You can edit that with a normal editor and sudo.

I like having everything in one place.

---

### Post by ulao3 on 2018-08-11
I'm not getting this at all. It was pretty favored all over the net to use crontab -e This seemed like the "right" way to do it. There other way was to make a file in cron.d (that seemed less correct) now if I do the /etc/crontab I see its empty so I'm not rally following that. 

"I like having everything in one place." Ok sure but the OS or many installs, stuff cron's in the weeklydaily,monthy folders. So how is that one place? When running the list of jobs it suggests there are weekly daily and months crons. I'm trying to make a by yearly. So not even sure where that fits in.

"it's not recommended to handle these files by hand." I don't understand this? I also do not get what the man is saying. spool? - I never used a spool folder. If you can not create a cron by hand (crontab -e) how are you to make a job?

Is there maybe a gui, I have x and k(5.4) environments but seems the task management is removed in k.

---

### Post by ulao3 on 2018-08-11
I was able to install gnome-schedual but now I have another problem here?

I want to run rsyn to back up my disk to my network drive. And my user is missing permissions.  Is there a way to run rsync without a password for root (guessing not) or as a daemon . I tried to run gnome-schedual as root and it does not run because of a missing home dir or something.

---

### Post by SeijiSensei on 2018-08-13
Run it from root's crontab.  If you don't want to use /etc/crontab, then use "sudo crontab -e" which will edit the file /var/spool/cron/root.

---

