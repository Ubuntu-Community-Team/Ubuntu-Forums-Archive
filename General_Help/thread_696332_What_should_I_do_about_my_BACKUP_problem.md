---
title: "What should I do about my BACKUP problem?"
date: 2008-02-13
forum: General Help
---

### Post by adn258 on 2008-02-13
So I backed up my system but unfortunately the archived contents take up about 9 gigs.  I have two problems I can just leave it on my computer but then what if something happens where I can't log back in?  The other problem is if I put it on a DVD there won't be enough room and I don't know If I can put it on two dvd's and be able to correctly restore it do you?  It's all compressed so I would think it would have to go on one thing i.e. one disk or device.  WHAT SHOULD I DO?

---

### Post by marufaberlin on 2008-02-14
Do you have an external hard drive? You know, you can get one for really cheap if you're lucky :)
Otherwise, there are online storage services where you can upload your backup. There are also Double Layer DVDs onto which you could burn your backup - they have about 9 gig space if my poor brain doesn't fail me right now :-)

---

### Post by adn258 on 2008-02-14
> **marufaberlin said:**
> Do you have an external hard drive? You know, you can get one for really cheap if you're lucky :)
Otherwise, there are online storage services where you can upload your backup. There are also Double Layer DVDs onto which you could burn your backup - they have about 9 gig space if my poor brain doesn't fail me right now :-)

The online thing would kind of be best but unfortunately that costs lol.  I'll try to figure out something

---

### Post by adn258 on 2008-02-14
> **adn258 said:**
> The online thing would kind of be best but unfortunately that costs lol.  I'll try to figure out something

can anyone think of a good place online to store them?

---

### Post by dcstar on 2008-02-14
> **adn258 said:**
> can anyone think of a good place online to store them?

And just how long will it take you to upload 9G?

---

### Post by joebeasley on 2008-02-14
Buy one of the hard disk enclosures (usb or firewire) and add a drive to it.  Use it only for backups.

---

### Post by Zwack on 2008-02-14
Or choose some form of backup/recovery system that allows you to span volumes and take incremental backups...

Personally I've used mindi/mondo for bare metal restores and Amanda for a daily backup to tape.  Amanda sorts out the repetition so that it performs multiple backups to tape and eventually gets everything backed up...

Mindi/Mondo is good for restoring at least enough functionality from a single CD that you should then be able to restore using Amanda...

Bacula also looks decent, of course these might all be overkill for your particular situation.

Z.

---

### Post by farruinn on 2008-02-14
I think ultimately you want some sort of external backup system.

If you want to fit it onto DVD's, however, there is a solution: from the command line you can use 'split' to, well, split them :) Then use 'cat' to concatenate them. Something along the lines of:

split -b4700m backup.tar backup.tar.

Which will split backup.tar into 4700mb chunks called backup.tar.aa, backup.tar.ab, etc. You can then put them back together with:

cat backup.tar.a* > backup.tar

Which should put them in order for you.

---

### Post by Sokertes on 2008-02-15
That is a good idea to use split and cat. I have never heard nor used it so I don't know.

What I do is have a smaller, slower machine (700Mhz 256M ram) with 4 random size drives that I use for backups using rsync over my home network. It works great.

###

config file

```



RSYNC="/usr/bin/rsync -e ssh"
OPTS="--quiet --recursive --links --perms --times --devices --timeout=300 --backup"

SRC="/etc /var /home /scripts /usr/local/games"
DST="192.168.0.3:/Backup/disney/"

```

rsync run script

```

#!/bin/bash

source /scripts/backup.conf

echo "Started update at" `date` >> $0.log 2>&1
logger -t rsync "re-rsyncing the manatee files"
${RSYNC} ${OPTS} ${SRC} ${DST} >> $0.log 2>&1

echo "End: "`date` >> $0.log 2>&1

```

I setup ssh trust relationship between the 2 machines so that I can have it run in cron

On client:

(1) ssh-keygen -t rsa

Accept default filename and default (blank) password
(Hit enter for password)

(2) Copy ~/.ssh/id_rsa.pub to your ~/.ssh directory on the server

ssh server.name.here "mkdir .ssh; chmod 0700 .ssh"
scp .ssh/id_rsa.pub server.name.here:.ssh/authorized_keys2

(OR, depending)

scp .ssh/id_rsa.pub server.name.here:.ssh/authorized_keys

I use this for a variety of purposes, and it works well. Since you are now using key-based authentication, there is no authentication prompt, and you can use scp or t
he ssh command in crons/shell scripts to execute commands on remote servers.

###

It may not be as efficient as an external hd but it works and works well.  I have used it for over 3 years now. I only had to actually use my backup once to recover my workstation but it saved me a boat load of work in the long run

Sokertes

---

### Post by adn258 on 2008-02-17
> **Sokertes said:**
> That is a good idea to use split and cat. I have never heard nor used it so I don't know.

What I do is have a smaller, slower machine (700Mhz 256M ram) with 4 random size drives that I use for backups using rsync over my home network. It works great.

###

config file

```



RSYNC="/usr/bin/rsync -e ssh"
OPTS="--quiet --recursive --links --perms --times --devices --timeout=300 --backup"

SRC="/etc /var /home /scripts /usr/local/games"
DST="192.168.0.3:/Backup/disney/"

```

rsync run script

```

#!/bin/bash

source /scripts/backup.conf

echo "Started update at" `date` >> $0.log 2>&1
logger -t rsync "re-rsyncing the manatee files"
${RSYNC} ${OPTS} ${SRC} ${DST} >> $0.log 2>&1

echo "End: "`date` >> $0.log 2>&1

```

I setup ssh trust relationship between the 2 machines so that I can have it run in cron

On client:

(1) ssh-keygen -t rsa

Accept default filename and default (blank) password
(Hit enter for password)

(2) Copy ~/.ssh/id_rsa.pub to your ~/.ssh directory on the server

ssh server.name.here "mkdir .ssh; chmod 0700 .ssh"
scp .ssh/id_rsa.pub server.name.here:.ssh/authorized_keys2

(OR, depending)

scp .ssh/id_rsa.pub server.name.here:.ssh/authorized_keys

I use this for a variety of purposes, and it works well. Since you are now using key-based authentication, there is no authentication prompt, and you can use scp or t
he ssh command in crons/shell scripts to execute commands on remote servers.

###

It may not be as efficient as an external hd but it works and works well.  I have used it for over 3 years now. I only had to actually use my backup once to recover my workstation but it saved me a boat load of work in the long run

Sokertes


that is a good idea thanks dude

---

### Post by UK-Wobbie on 2008-02-17
> **adn258 said:**
> So I backed up my system but unfortunately the archived contents take up about 9 gigs.  I have two problems I can just leave it on my computer but then what if something happens where I can't log back in?  The other problem is if I put it on a DVD there won't be enough room and I don't know If I can put it on two dvd's and be able to correctly restore it do you?  It's all compressed so I would think it would have to go on one thing i.e. one disk or device.  WHAT SHOULD I DO?

May i ask what do you use to backup your ubuntu computer? :)
I like to backup my computer but not having any luck on getting the right tool :lolflag:
I can back it up on to a windows home server.

---

### Post by adn258 on 2008-02-17
> **UK-Wobbie said:**
> May i ask what do you use to backup your ubuntu computer? :)
I like to backup my computer but not having any luck on getting the right tool :lolflag:
I can back it up on to a windows home server.

I am actually using a program sbackup you can get it by going to the terminal and typing sudo apt-get install sbackup and then go to administration and you will see a simple restore and backup config you can use the recommended settings which don't backup everything but all the important stuff or you can add each directory individually if you want.  I'll give you a link about it below.  


[http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html]("http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html")

---

### Post by UK-Wobbie on 2008-02-17
> **adn258 said:**
> I am actually using a program sbackup you can get it by going to the terminal and typing sudo apt-get install sbackup and then go to administration and you will see a simple restore and backup config you can use the recommended settings which don't backup everything but all the important stuff or you can add each directory individually if you want.  I'll give you a link about it below.  


[http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html]("http://www.debianadmin.com/backup-and-restore-your-ubuntu-system-using-sbackup.html")

Thanks :mrgreen:

---

