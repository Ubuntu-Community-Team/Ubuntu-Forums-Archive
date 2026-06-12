---
title: "What is the command to install upgrades using terminal?"
date: 2015-02-21
forum: General Help
---

### Post by mandarpowale on 2015-02-21
I have UBUNTU 14.04 LTS freshly installed on my machine and all the updates automatically done using 'default software and updates'  tool.

Some files did not get installed properly even thouh the installation was a success.

Is there any terminal command to install all updates automatically ?

---

### Post by sudodus on 2015-02-21
Standard command lines for ***update/upgrade*** within the same version (*not* upgrade to another version, that is done with ***do-release-upgrade***)

```
sudo apt-get update
sudo apt-get dist-upgrade
```

If you have problems you can try the following list of commands originally posted by *oldfred*. All commands need ***sudo***.

```

# This will reinstall if not current. (from my chroot procedure which does not have sudo on every line,
# so use the sudo -i first).
 
#if not chroot use: sudo -i

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

# Remove lock
# If you are absolutely sure you do not have another upgrade process running.
# Locked dpkg - only if sure you are not running another update.

sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a 

```

---

