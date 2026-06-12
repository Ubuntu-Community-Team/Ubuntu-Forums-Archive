---
title: "Nothing Works!"
date: 2008-04-21
forum: General Help
---

### Post by MosMusy on 2008-04-21
None of the system apps work now. I try to open let's say (add/remove) and it just stalls while loading something and always at the same spot. This happened after I installed the Armenian language interphase, and now I am trying to get that off, but the language support is doing the same thing! Can't ubuntu work right once!!

---

### Post by indiecast on 2008-04-21
try rebooting

---

### Post by articpenguin on 2008-04-21
I cant think of a reason for Ubuntu to stall when opening up an applocation. What are the specs of your computer?

---

### Post by MosMusy on 2008-04-21
This is what I get when I try to open up the (install/remove) app,

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

what should i do?

---

### Post by MosMusy on 2008-04-21
when I try to open synaptic package manager this is what I get:

An error occured

The following details are provided:

E: Read error - read (5 Input/output error)
E: Internal error opening cache (3). Please report.

---

### Post by retrow on 2008-04-21
If you are in gutsy and your sources.list seems broken, you can replace the default values by doing this:

sudo gedit /etc/apt/sources.list

Replace the text with - 

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

Run

```
sudo apt-get update -f
```

Followed by

```
sudo apt-get upgrade
```

---

### Post by MosMusy on 2008-04-21
in the end of the commands you gave me the terminal's last four lines (after a bunch of executions and updates) said:

Fetched 6008kB in 2m4s (48.2kB/s)                                              
Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.

---

### Post by MosMusy on 2008-04-21
you know what, now nothing really seems to be working and it's a shame since I haven't messed around with anything. I'm just going to get rid of Ubuntu and go back to windows, I don't have the nerve nor time to deal with Ubuntu's bugs and failures. All I tried to do is install an Armenian interface, but in return ubuntu just doesn't work, any last minute suggestions or should I just get rid of it?

---

### Post by retrow on 2008-04-21
```
sudo apt-get install -f
```
```
sudo dpkg --configure -a
```

That usually takes care of improperly installed packages. If that doesn't work I'm outta ideas. Someone who knows more than I do will have to step in.

---

### Post by MosMusy on 2008-04-21
no, doesn't work

---

### Post by indiecast on 2008-04-22
may be a bad install?

try reformating and installing again

---

### Post by Black-Diamond on 2008-05-02
I almost have the same problem but when i tried your solution
see what it respond to me


ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ms-sys
ubuntu@ubuntu:~$ sudo ms-sys -w /dev/hda
sudo: ms-sys: command not found
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$

---

