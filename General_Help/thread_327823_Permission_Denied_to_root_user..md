---
title: "Permission Denied to root user."
date: 2006-12-29
forum: General Help
---

### Post by mrgorm on 2006-12-29
Currently, I cannot install or upgrade any applications via apt-get or dpkg. For example:

```
$ sudo apt-get install beagle
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  gnumeric beagle-backend-evolution
The following NEW packages will be installed:
  beagle
0 upgraded, 1 newly installed, 0 to remove and 34 not upgraded.
Need to get 0B/1238kB of archives.
After unpacking 4088kB of additional disk space will be used.
(Reading database ... 122275 files and directories currently installed.)
Unpacking beagle (from .../beagle_0.2.6-1ubuntu5_i386.deb) ...
[B]dpkg: error processing /var/cache/apt/archives/beagle_0.2.6-1ubuntu5_i386.deb (--unpack):
 unable to create `./usr/sbin/beagle-build-index': Permission denied[/B]
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/beagle_0.2.6-1ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Not being able to install seems like more of a symptom than the root of the problem. The bolded error above replicates for any install or upgrade that wants to change /usr/sbin/.

As it turns out, when functioning as root (via sudo), I no longer have write access to /usr/sbin/. Shouldn't this be impossible? I thought root could do anything?

The permissions appear to be fine. 
```
drwxr-xr-x   2 root     root         8192 Oct  3 19:51 sbin
```

However, I cannot write to the sbin directory or *any* of its contents. Some examples lie below:
```
$ sudo mv /usr/sbin /usr/sbin.moved
mv: cannot move `sbin' to `sbin.moved': Operation not permitted
$ sudo chmod 777 /usr/sbin
chmod: changing permissions of `sbin': Operation not permitted
$ sudo touch /usr/sbin/install-info
touch: cannot touch `/usr/sbin/install-info': Permission denied
$ sudo touch /usr/sbin/brand-new-file-for-ubuntu-forums
touch: cannot touch `/usr/sbin/brand-new-file-for-ubuntu-forums': Permission denied
```


Please Help!! I cannot change the state of my machine b/c of this problem and would really prefer not to reinstall Ubuntu.

Thanks in advance.

---

### Post by ~LoKe on 2006-12-29
Boot into the recovery console and try the chmod/chown.  If that doesn't work, boot up a LiveCD and mount the partition and do the same.

---

### Post by taurus on 2006-12-29
What's the output of this command?

```
groups
```

---

### Post by mrgorm on 2006-12-29
> **taurus said:**
> What's the output of this command?

```
$ groups mgormley
mgormley : mgormley adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
$ groups root
root : root
```

"mgormley" is my normal username.

---

### Post by taurus on 2006-12-29
What happens when you run these two commands?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by mrgorm on 2006-12-29
> **taurus said:**
> What happens when you run these two commands?

update runs fine. 
upgrade presents the same sort of problem I run into when trying to install: "Permission Denied" and "unable to create" a file in /usr/sbin/.

```
$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Get:1 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Get:2 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:3 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:4 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://archive.canonical.com dapper-commercial Release
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Get:5 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:6 http://us.archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://us.archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-updates/universe Sources
Hit http://archive.ubuntu.com dapper-updates/multiverse Sources
Hit http://us.archive.ubuntu.com dapper-updates Release
Hit http://us.archive.ubuntu.com dapper/multiverse Packages
Hit http://us.archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://us.archive.ubuntu.com dapper-updates/universe Packages
Fetched 6B in 2s (3B/s)
Reading package lists... Done
```

```
$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
The following packages will be upgraded:
  dpkg dpkg-dev dselect evince firefox firefox-gnome-support gdm gnupg hal
  hal-device-manager imagemagick libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-glib1 libavahi-qt3-1 libgsf-1-113
  libgsf-1-common libhal-storage1 libhal1 libmagick9 libmono0 libnspr4
  libnss3 libpng12-0 libxine-main1 linux-image-2.6.15-27-386
  linux-restricted-modules-2.6.15-27-386 linux-restricted-modules-common
  lvm2 mono-classlib-1.0 mono-common mono-jit tar
34 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/57.6MB of archives. After unpacking 49.2kB will be used.
Do you want to continue? [Y/n/?] Y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 122275 files and directories currently installed.)
Preparing to replace dpkg 1.13.11ubuntu6 (using .../dpkg_1.13.11ubuntu7_i386.deb) ...
Unpacking replacement dpkg ...
dpkg: error processing /var/cache/apt/archives/dpkg_1.13.11ubuntu7_i386.deb (--unpack):
 unable to create `./usr/sbin/install-info': Permission denied
Errors were encountered while processing:
 /var/cache/apt/archives/dpkg_1.13.11ubuntu7_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

---

### Post by mrgorm on 2006-12-29
> **~LoKe said:**
> Boot into the recovery console and try the chmod/chown.  If that doesn't work, boot up a LiveCD and mount the partition and do the same.

I couldn't actually boot into the recovery console (I pressed escape in the boot sequence, chose the recover kernel, but then got stuck when it said "enter root password". I don't actually have a root passwd set up and my normal admin password didn't work).

I tried the LiveCD idea and successfully mounted the partition. But it behaved exactly the same. I still couldn't change anything about the directory or its contents. I tried chmod and chown as you suggested as well.

```
$ sudo chmod -v 755 sbin
chmod: changing permissions of `sbin': Operation not permitted
failed to change mode of `sbin' to 0755 (rwxr-xr-x)
```

```
$ sudo chown root:root sbin
chown: changing ownership of `sbin': Operation not permitted
```

---

### Post by ~LoKe on 2006-12-29
You tried enabling the root account, didn't you. ;)

I don't even have a root line in groups.
> loke@x04d:~$ groups
loke adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

---

### Post by mrgorm on 2006-12-29
Whoops! Okay, so I enabled the root password and was able to log in to the recovery console. 

*However*, I still was unable to change sbin's permissions or owners. I used both chmod and chown again and both resulted in "Operation not permitted" errors.

Just to clarify, I re-ran groups without supplying a username and this was the output.
```
$ groups
mgormley adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
```

Should these problems even be possible? I always thought that doing things as root or with sudo never receive such "Permission Denied" errors. Isn't it sort of the highest level of admin rights?

---

### Post by dcstar on 2006-12-30
> **mrgorm said:**
> 
.........
Should these problems even be possible? I always thought that doing things as root or with sudo never receive such "Permission Denied" errors. Isn't it sort of the highest level of admin rights?

Exactly!, just out of interest, what is your disk space situation?

---

### Post by mrgorm on 2006-12-30
I am using about 20% of a my sda1 Ubuntu partition which sits on a 160gb hard drive, and have a second 200gb hard drive used for backups.
So there's plenty of disk space to go around.

---

