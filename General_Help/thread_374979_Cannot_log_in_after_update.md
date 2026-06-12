---
title: "Cannot log in after update"
date: 2007-03-03
forum: General Help
---

### Post by coconuteire on 2007-03-03
Hi all.

I just installed the 32-bit version of Ubuntu (6.06 - Dapper). Everything was working fine until I installed all of the recommended updates (which numbered in the hundreds). After rebooting and trying to log in with my account (david), I get an error message which says "Your session lasted less than 10 seconds". The error report mentions something like this after just four lines:

Line 106: /etc/profile: Permission denied

I know a lot of other people get this error and it often has something to do with the HDD being full. Here's an output of df -h:

david@david-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G  2.2G   32G   7% /
varrun               1014M   84K 1014M   1% /var/run
varlock              1014M  4.0K 1014M   1% /var/lock
udev                 1014M  108K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   19M  995M   2% /lib/modules/2.6.15-28-386/volatile

Here's the output of ls:

david@david-desktop:~$ sudo ls -la /home
Password:
total 12
drwxr-xr-x  3 david root  4096 2007-03-02 12:21 .
drwxr-xr-x 21 root  root  4096 2007-03-02 12:51 ..
drwxr-xr-x 14 david david 4096 2007-03-03 12:56 david

I can log in fine using the failsafe GNOME session with the same username.

Any idea what might be causing this?

Thanks in advance. :popcorn:

---

