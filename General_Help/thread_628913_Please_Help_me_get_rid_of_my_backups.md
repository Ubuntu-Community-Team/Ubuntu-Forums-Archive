---
title: "Please Help me get rid of my backups"
date: 2007-12-01
forum: General Help
---

### Post by cptnff on 2007-12-01
Ok here's  my problem I've been running out of hd space and I figured out it was because I set my computer for daily backups with the simple backup config. I found the folder my backups are located in, but I cant delete them. thanks in advanced for any help.

---

### Post by skymera on 2007-12-01
cd /location/to backups
sudo rm <filename>

---

### Post by cptnff on 2007-12-01
thanks for your quick response skymera, but now I have a whole new problem. I cant do what you told me to do because I don't know the file names, and now when I try to enter my backup folder  it tells me "You do not have the permissions necessary to view the contents of "backup". Also the folder says there's zero items in it but I know thats not true.:confused:

---

### Post by PeterJS on 2007-12-01
You can run nautilus as root with:
```

gksu nuatilus

```and then delete the files from there.

---

### Post by skymera on 2007-12-02
a nice way to see what files and directories lie ahead.

```
cd /to/whatever
ls 
```

ls lists all files and dirs, or just files.

also press the TAB button to finish part of the command

example

```
 cd /etc/a<TAB>
will make it:
cd /etc/apt
or lists other dirs that begin with 'a' 
```

---

### Post by cptnff on 2007-12-04
So when I tried what you said this time skymera I was told permission denied. I'm starting to think I have a bigger problem than I originally thought. could this be a bug or something?

---

### Post by kikdadog on 2008-01-03
I have the same problem, hope somebody can help out here. Heres what happened to me,  few weeks ago turned on the simple backup, didnt think twice about it till this morn when I started to get low disk space warnings. Knew what the problem was right away, so I go to the var/backup folder sure enough 6 gigs worth of backups. So I root nautilus into the folder and delete the offending files, heres the problem, never got the hard drive space back. :confused:
What did I do wrong??? I tried to purge the files(left one backup in there), but no luck, seems not to work.


Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             11014416  10200848    254056  98% /
proc                         0         0         0   -  /proc
/sys                         0         0         0   -  /sys
varrun                  257916        92    257824   1% /var/run
varlock                 257916         0    257916   0% /var/lock
udev                    257916        92    257824   1% /dev
devshm                  257916         0    257916   0% /dev/shm
devpts                       0         0         0   -  /dev/pts
lrm                     257916     34696    223220  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sda5             15835172   2824148  12206644  19% /home
securityfs                   0         0         0   -  /sys/kernel/security
binfmt_misc                  0         0         0   -  /proc/sys/fs/binfmt_mis


any help would be appreciated.

---

### Post by kpkeerthi on 2008-01-03
> 
So I root nautilus into the folder and delete the offending files, heres the problem, never got the hard drive space back.

Did you do SHIFT+DELETE ? If not, the files should be in root's Trash. **gksudo nautilus** and navigate to /root, Press Ctrl + H to view hidden files and look for **.Trash-xyz** folder. The files could probably be there.

---

### Post by kikdadog on 2008-01-03
Fantastic, Thank you very very much. You :guitar: ! Really this is one reason Im an Ubuntu addict. Whackin myself in the forehead for not thinking of root. I seen a couple other posts with this type of problem I hope they catch this answer.

---

### Post by ~LoKe on 2008-01-03
> **skymera said:**
> cd /location/to backups
sudo rm <filename>

If they're backups, they probably contain directories.  You'd need to do...
```
sudo rm -r directory
```

---

### Post by kpkeerthi on 2008-01-03
As a side note, its usually a good idea to cleanup backup archives using a cron job. 

In my case, my files are backed up (as tar) with a cron once in 15 days. I have setup another cron to clean up backup archives that are 30 days or older.
```

find /var/backup -mtime +30 -exec rm '{}' ';'

```

---

### Post by cptnff on 2008-01-21
thanks to everybody who helped me out. I fixed the problem a while ago, but I forget to post that my problem was solved. well anyway, problem solved:)

---

