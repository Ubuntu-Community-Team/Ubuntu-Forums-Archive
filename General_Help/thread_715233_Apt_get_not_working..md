---
title: "Apt get not working."
date: 2008-03-04
forum: General Help
---

### Post by Tyrfing on 2008-03-04
Hello, I cannot download and install any Ubuntu packages

This happens no matter what application I try to install.

tim@jemaine:~$ sudo apt-get install libdvdread3
Password:
Reading package lists... Done
Building dependency tree... Done
Package libdvdread3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdread3 has no installation candidate


Any ideas? My Ubuntu version is 6.06 LTS


Thanks

---

### Post by bapoumba on 2008-03-04
Please post your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by justinmiller87 on 2008-03-04
You probably need to enable the Medibuntu repositories.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) has the instructions.

---

### Post by Tyrfing on 2008-03-04
This is what happened:


# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by justinmiller87 on 2008-03-04
That is bizarre, no repositories are enabled. I'm not sure why, but to enable them type: gksudo gedit /etc/apt/sources.list

And copy/paste the following:

```


# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
 deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu dapper-security main
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu dapper-security main
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

Once that is finished, run the following:
sudo wget [http://www.medibuntu.org/sources.list.d/dapper.list](http://www.medibuntu.org/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update


You should be able to get the files you need after that.

---

### Post by bapoumba on 2008-03-04
Looks like [libdvdread3]("http://packages.ubuntu.com/dapper/libdvdread3") is in dapper main to me..

---

### Post by erginemr on 2008-03-04
This happens when there is no active internet connection during the install...

---

### Post by justinmiller87 on 2008-03-04
> **erginemr said:**
> This happens when there is no active internet connection during the install...
Ok, I was proven wrong, Bapoumba. It happens.

I've never had the repositories disabled when I installed Internet connection free. Then again, I've never installed 6.06. It's not done it when I used 7.04 or 7.10 anyway.

---

### Post by bapoumba on 2008-03-04
> **justinmiller87 said:**
> Ok, I was proven wrong, Bapoumba. It happens.
No problem :)
i had to check, I was not sure anymore.
> **justinmiller87 said:**
> 
I've never had the repositories disabled when I installed Internet connection free. Then again, I've never installed 6.06. It's not done it when I used 7.04 or 7.10 anyway.
I've helped people with recent gutsy install who had the same problem. When the package manager cannot connect to the repos, usually only the cdrom is left in the sources.list. Everything else is commented out.

---

