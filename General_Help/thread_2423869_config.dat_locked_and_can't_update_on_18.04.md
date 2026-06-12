---
title: "config.dat locked and can't update on 18.04"
date: 2019-07-30
forum: General Help
---

### Post by buzzmandt on 2019-07-30
Searching I tried the following fixes.

```
fuser -v /cat/cache/debconf/config.dat 

```
in order to find user process to kill it but that command hangs and returns nothing. This seems to be the right fix but isn't working for me

Also found this and also didn't work

```
sudo touch /var/lib/dpkg/lock
sudo dpkg --configure -a
```

I'm at a loss for something that might work. 

Currently affected errors are

libpam-systemd
tzdata
libssl1.1
openssl
ubuntu-minimal
sane-utils
xserver-xorg-legacy
ubuntu-standard
linux-headers-4.15.0.55-generic
linux-headers-generic
linux-generic

This is my mom's computer and I only get by there once every few days so please keep the suggestions coming and I'll update once I try em.

Full error readout follows:

```
sudo dpkg --configure -a               
[sudo] password for ********:  
Setting up libpam-systemd:amd64 (237-3ubuntu10.24) ... debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

dpkg: error processing package libpam-systemd:amd64 (--configure): installed libpam-systemd:amd64 package post-installation script subprocess returned error exit status 1 Setting up tzdata (2019b-0ubuntu0.18.04) ... debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

dpkg: error processing package tzdata (--configure): installed tzdata package post-installation script subprocess returned error exit status 1 Setting up libssl1.1:amd64 (1.1.1-1ubuntu2.1~18.04.4) ... debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

dpkg: error processing package libssl1.1:amd64 (--configure): installed libssl1.1:amd64 package post-installation script subprocess returned error exit status 1 

dpkg: dependency problems prevent configuration of openssl: openssl depends on libssl1.1 (>= 1.1.1); however: Package libssl1.1:amd64 is not configured yet. 

dpkg: error processing package openssl (--configure): dependency problems - leaving unconfigured 

dpkg: dependency problems prevent configuration of ubuntu-minimal: ubuntu-minimal depends on tzdata; however:  Package tzdata is not configured yet. 

dpkg: error processing package ubuntu-minimal (--configure): dependency problems - leaving unconfigured Setting up sane-utils (1.0.27-1~experimental3ubuntu2.1) ... debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

dpkg: error processing package sane-utils (--configure): installed sane-utils package post-installation script subprocess returned error exit status 1 Setting up xserver-xorg-legacy (2:1.19.6-1ubuntu4.3) ... debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

dpkg: error processing package xserver-xorg-legacy (--configure): installed xserver-xorg-legacy package post-installation script subprocess returned error exit status 1 

dpkg: dependency problems prevent configuration of ubuntu-standard: ubuntu-standard depends on libpam-systemd; however:  Package libpam-systemd:amd64 is not configured yet. 

dpkg: error processing package ubuntu-standard (--configure): dependency problems - leaving unconfigured 

dpkg: dependency problems prevent configuration of linux-headers-4.15.0-55-generic:                               linux-headers-4.15.0-55-generic depends on libssl1.1 (>= 1.1.0); however:                                Package libssl1.1:amd64 is not configured yet. 

dpkg: error processing package linux-headers-4.15.0-55-generic (--configure): dependency problems - leaving unconfigured 

dpkg: dependency problems prevent configuration of linux-headers-generic: linux-headers-generic depends on linux-headers-4.15.0-55-generic; however:  Package linux-headers-4.15.0-55-generic is not configured yet. 

dpkg: error processing package linux-headers-generic (--configure): dependency problems - leaving unconfigured 

dpkg: dependency problems prevent configuration of linux-generic: linux-generic depends on linux-headers-generic (= 4.15.0.55.57); however:  Package linux-headers-generic is not configured yet. 

dpkg: error processing package linux-generic (--configure): dependency problems - leaving unconfigured Processing triggers for libc-bin (2.27-3ubuntu1) ... 

Errors were encountered while processing: 
libpam-systemd:amd64 
tzdata 
libssl1.1:amd64 
openssl 
ubuntu-minimal 
sane-utils 
xserver-xorg-legacy 
ubuntu-standard 
linux-headers-4.15.0-55-generic 
linux-headers-generic 
linux-generic
[CODE]
```[/CODE]

---

