---
title: "Unable to Update E: Read error - read (5: Input/output error)"
date: 2012-11-20
forum: General Help
---

### Post by funkmasterdelux on 2012-11-20
Hi Folks,

Long time reader, first time poster. I've searched and read similar posts on this topic but have not been able to find a solution.

When running sudo apt-get update I get the following error:

Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

I have tried the various instructions on some of the other forums including this, nothing has worked:

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update

The install is pretty new, about a month or so old. I've run 12.04 before without issues on the same PC. In a potentially related issue, my system hangs at times, I haven't had this issue previously.

The contents of /etc/apt/sources.list is below, i understand it is correct (?):

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

Thanks in advance!

Cheers

---

### Post by drmrgd on 2012-11-20
If purging the package lists didn't work, then I'm wondering if it's a problem with either space on the drive or a bad sector.  What's the output of :

```
df -Th
```

Also, can you run a disk check on that drive (or partition depending on what you've got) to make sure there's nothing wrong.

---

### Post by ibjsb4 on 2012-11-20
Post #5 has a possible solution.

[http://ubuntuforums.org/showthread.php?t=1642574](http://ubuntuforums.org/showthread.php?t=1642574)

---

### Post by wildmanne39 on 2012-11-20
Hi, that usually means bad sectors in the hard drive, the last person I helped with that error ended up after days of trying to fix it reformatting there drive and reinstalling.

---

### Post by funkmasterdelux on 2012-11-21
Hi all,

Thanks for the prompt replies

drmrgd, the output to df -Th is:

duncan@duncanpc:~$ df -Th
Filesystem        Type      Size  Used Avail Use% Mounted on
/dev/sda1         ext4      109G   64G   40G  62% /
udev              devtmpfs 1000M  4.0K 1000M   1% /dev
tmpfs             tmpfs     403M  876K  402M   1% /run
none              tmpfs     5.0M     0  5.0M   0% /run/lock
none              tmpfs    1007M  1.9M 1005M   1% /run/shm
//192.168.1.8/mp3 cifs      1.4T  1.2T  172G  87% /home/duncan/PetstoreMusic
//192.168.1.8/TV  cifs      1.4T  1.2T  172G  87% /home/duncan/PetstoreTV

ibjsb4 - i get a similar error when i copy status-old:

cp: reading `/var/lib/dpkg/status-old': Input/output error
cp: failed to extend `/var/lib/dpkg/status': Input/output error

Wild Man - i think you are on the money. im running a disk scan now. im hoping to avoid the reinstall if possible but ill see how i go. 

cheers

---

### Post by drmrgd on 2012-11-21
Yup!  I'd say it was a bad sector too.  Had to check for both space and that to rule it out and checking for space is a little quicker.   Hopefully it's a simple fix and you don't end up having to recover the whole drive.

---

### Post by xp15 on 2013-05-26
i used mhdd ^^

after remaping everything is fine now, and from 8 bad sectors-to only 2. and one kind of bad sectors just no more exist. the software kind of hidding the bad sectors, so the drive wont use them.
she cant fiz any bad sector.

anyway, my system is working again ^^ .

---

