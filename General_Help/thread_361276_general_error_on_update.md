---
title: "general error on update"
date: 2007-02-14
forum: General Help
---

### Post by matthewanderson on 2007-02-14
Hi im new to Ubuntu having migrated from XP, when i try to update the system using the package manager it come up with the following error:

> E: Dynamic MMap ran out of room
E: Error occurred while processing kdegraphics (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


Also i seem unable to install the java plugin for Firefox, if you could help it would be greatly appreciated.

---

### Post by taurus on 2007-02-14
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```
And also the output of this command too.

```
df -h
```

---

### Post by matthewanderson on 2007-02-14
ok the output of the sources.list 
> # Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

## official backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# If you get errors about missing keys follow these command's :
# gpg --keyserver subkeys.pgp.net --recv 33BAC1B3
# gpg --export --armor 33BAC1B3 | sudo apt-key add -
#
# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)


## plf primary repo
## http 100mbit/s mirror provided thanks to OVH [http://ovh.com](http://ovh.com)

## plf mirror. use if primary repo is offline
## FTP mirror from [http://free.fr](http://free.fr) (french ISP)
## deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
## deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

##
## Use the following repos ONLY if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## official wine apt repository
# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) breezy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) breezy main


## opera web browser
## deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

## skype
## deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
#AUTOMATIX REPOS END
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper main
##BERYL REPOSITORIES
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
deb-src [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
##BERYL SVN REPOSITORIES
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn


and the output of the second command:
> Filesystem            Size Used Avail Use% Mounted on
/dev/sdb1             7.4G  4.1G  3.1G  58% /
varrun                506M   84K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  124K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-28-386/volatile
/dev/sda1              75G   48G   27G  65% /media/windows disk
/dev/scd0             244M  244M     0 100% /media/cdrom0
/dev/sdc1             248M  243M  4.4M  99% /media/usbdisk


Oh and im using version 6.06.1

---

### Post by taurus on 2007-02-14
This is really bad.  If you are running Dapper, how come you have repos for both Breezy and Edgy?  You cannot mix them in there or bad things can happen and usually will happen to your machine soon.  Therefore, you need to edit your /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and replace both **breezy** & **edgy** with **dapper**.  Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by matthewanderson on 2007-02-14
ok thanks, now im getting this error 
> [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

---

### Post by taurus on 2007-02-14
Try

```
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by matthewanderson on 2007-02-14
Thats great, it seems to have worked ty. Do you know how i can get java to work on Firefox? or is that something for the Firefox forum?

---

### Post by taurus on 2007-02-14
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

