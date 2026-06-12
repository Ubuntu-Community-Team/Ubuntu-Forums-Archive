---
title: "Can't do Update"
date: 2008-05-31
forum: General Help
---

### Post by abbasali31 on 2008-05-31
I am running ubuntu V8.04 and in an update tray there are some updates available, but it wouldn't do it.  I got the error message below.

Note:  I don't have a network problem, and can browse the Internet fine.




Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.




Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Pumalite on 2008-05-31
Try changing Servers

---

### Post by abbasali31 on 2008-05-31
I tried some other sources, but didn't work either.  Can't figure it out.

Thanks,

---

### Post by unutbu on 2008-05-31
Post your /etc/apt/sources.list.

---

### Post by abbasali31 on 2008-05-31
I apologize, but what do you mean.  Do you want me post the source where updates get downloaded.  If it is then see below


[http://ftp.utexas.edu/ubuntu](http://ftp.utexas.edu/ubuntu)

---

### Post by unutbu on 2008-05-31
Click on Applications>Accessories>Terminal to open a terminal, then type

```
cat /etc/apt/sources.list
```

Please post the output here.

---

### Post by jw5801 on 2008-05-31
> **azhar-teza said:**
> I apologize, but what do you mean.  Do you want me post the source where updates get downloaded.  If it is then see below


[http://ftp.utexas.edu/ubuntu](http://ftp.utexas.edu/ubuntu)

Post the file /etc/apt/sources.list. In other words, the output from
```
cat /etc/apt/sources.list
```

---

### Post by drs305 on 2008-05-31
It looks like you didn't have the installation CD inserted when you tried to do the update. Either insert the CD from the _original_ installation or open synaptic > Settings > Repositories, Ubuntu software and uncheck the Cdrom in the window at the bottom.

---

### Post by abbasali31 on 2008-06-01
Below is the requested information.


cat /etc/apt/sources.list
# 
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) hardy main restricted
deb-src [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) hardy-updates main restricted
deb-src [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) hardy universe
deb-src [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) hardy universe
deb [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) hardy-updates universe
deb-src [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) hardy multiverse
deb-src [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) hardy multiverse
deb [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) hardy-updates multiverse
deb-src [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) hardy-security main restricted
deb-src [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) hardy-security main restricted
deb [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) hardy-security universe
deb-src [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) hardy-security universe
deb [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) hardy-security multiverse
deb-src [http://ftp.utexas.edu/ubuntu/](http://ftp.utexas.edu/ubuntu/) hardy-security multiverse
aali@HOMEPCUBU:~$

---

### Post by unutbu on 2008-06-01
I agree with drs305. Since you have a working internet connection, you probably don't need to be looking for packages off a cdrom. Therefore, 
```

gksu gedit /etc/apt/sources.list
```

Put a pound sign (#) in front of the two lines containing the word 'cdrom', so they look like this:

```
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted

#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080422.2)]/ hardy main restricted
```

Save and exit. Then, to make apt aware of the change,

```
sudo apt-get update
```

Then see if updating packages works.

---

### Post by abbasali31 on 2008-06-02
Thanks everyone who responded

---

