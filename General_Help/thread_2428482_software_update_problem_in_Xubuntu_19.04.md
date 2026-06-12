---
title: "software update problem in Xubuntu 19.04"
date: 2019-10-04
forum: General Help
---

### Post by brashley46 on 2019-10-04
Hi,
This started a couple of weeks ago. Checking for updates in software-updater fails; checking for updates in Synaptic gives me the following error messages:

```
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
E: Sub-process returned an error code

W: Ignoring file 'd-apt.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: Ignoring file 'd-apt.list.save.1' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
```

I seem to be getting some updates anyway, for instance the kernel updates this morning came through software updater even after it told me it failed to download any.

What can I do about this?

---

### Post by ajgreeny on 2019-10-04
Can you please show the output of terminal commands
```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
```
Please use **Code-Tags** for terminal output to show that text in a more readable format, the same as it is in the terminal, not as plain text. 
See my signature below for a **How-to**

---

### Post by brashley46 on 2019-10-05
Corrected the above original post with code tags, sorry! As for those terminal commands, 

```
brashley@thelinuxlaptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Xubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)]/ bionic main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu disco main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu disco-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu disco universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://archive.ubuntu.com/ubuntu disco-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu disco multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://archive.ubuntu.com/ubuntu disco-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu disco-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://archive.ubuntu.com/ubuntu disco-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://archive.ubuntu.com/ubuntu disco-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://archive.ubuntu.com/ubuntu disco-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
brashley@thelinuxlaptop:~$ ls -l /etc/apt/sources.list.d
total 56
-rw------- 1 root root   1 May 21 17:40 d-apt.list.save
-rw------- 1 root root   1 May 21 17:43 d-apt.list.save.1
-rw-r--r-- 1 root root  98 Sep 10 11:20 dropbox.list
-rw-r--r-- 1 root root  66 May 16 19:14 dropbox.list.distUpgrade
-rw-r--r-- 1 root root  98 Sep 10 11:20 dropbox.list.save
-rw-r--r-- 1 root root 116 Sep 10 11:20 home:stevenpusser.list
-rw-r--r-- 1 root root 116 May 16 19:14 home:stevenpusser.list.distUpgrade
-rw-r--r-- 1 root root 116 Sep 10 11:20 home:stevenpusser.list.save
-rw-r--r-- 1 root root  53 Sep 19 13:01 megasync.list
-rw-r--r-- 1 root root  87 May 16 19:14 megasync.list.distUpgrade
-rw-r--r-- 1 root root  53 Sep 10 11:20 megasync.list.save
-rw-r--r-- 1 root root 178 Sep 10 11:20 nextcloud-devs-ubuntu-client-bionic.list
-rw-r--r-- 1 root root 180 May 16 19:14 nextcloud-devs-ubuntu-client-bionic.list.distUpgrade
-rw-r--r-- 1 root root 178 Sep 10 11:20 nextcloud-devs-ubuntu-client-bionic.list.save
brashley@thelinuxlaptop:~$ 



```

---

### Post by ajgreeny on 2019-10-06
Firstly I suggest you report back here the content of these two items in sources.list.d which are causing a warning to show about an invalid filename extension; perhaps the .1 at the end of one of them.
They are plain text files with the repo url so just copy them back here.```
-rw------- 1 root root   1 May 21 17:40 d-apt.list.save
-rw------- 1 root root   1 May 21 17:43 d-apt.list.save.1
```
I am not sure, however, what the error that is shown below that warning means so I'm not able to go much further with this for you, but perhaps you may find some help from searching the error shown in your first post.

Here's a couple for a start.
[https://askubuntu.com/questions/1041226/problem-with-sudo-apt-update-in-ubuntu-18-04](https://askubuntu.com/questions/1041226/problem-with-sudo-apt-update-in-ubuntu-18-04)
[https://askubuntu.com/questions/1140933/error-when-trying-to-update-ubuntu-using-sudo-apt-get-update](https://askubuntu.com/questions/1140933/error-when-trying-to-update-ubuntu-using-sudo-apt-get-update)

---

### Post by brashley46 on 2019-10-06
```
brashley@thelinuxlaptop:~$ -rw------- 1 root root   1 May 21 17:40 d-apt.list.save
-rw-------: command not found
brashley@thelinuxlaptop:~$ -rw------- 1 root root   1 May 21 17:43 d-apt.list.save.1
-rw-------: command not found

```

---

### Post by brashley46 on 2019-10-06
d-apt.list.save and d-apt.list.save.1 are each totally empty.

---

### Post by Skaperen on 2019-10-06
the commands to do are:```
cat /etc/apt/sources.list.d/d-apt.list.save
cat /etc/apt/sources.list.d/d-apt.list.save.1
```

these one character files are the apparent culprits and it is unknown why they are there.  files in that directory should have one or more lines that are comments or describe additional repositories to use.  a one character file makes no sense in that context.  the 2nd one might be a backup.  it has a later date by about 3 minutes.  they were created or last updated on May 21 of this year.  were you doing anything new on that date around 5:40 PM like adding a repository or two?

you might be running into this issue from Debian:  [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=614398](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=614398)

---

### Post by Skaperen on 2019-10-06
the "one character" might just be a newline character.  try:```
od -t x1 /etc/apt/sources.list.d/d-apt.list.save*
```

to see what it is in hexadecimal.

---

### Post by brashley46 on 2019-10-07
```
brashley@thelinuxlaptop:~$ sudo od -t x1 /etc/apt/sources.list.d/d-apt.list.save*
0000000 0a 0a
0000002
brashley@thelinuxlaptop:~$ 


```

---

### Post by brashley46 on 2019-10-08
So I can think of two alternatives: Await the Xubuntu 19.10 update, or eliminate those two files. Which?

---

### Post by cruzer001 on 2019-10-08
Remove save.1 and update
```
sudo rm /etc/apt/sources.list.d/d-apt.list.save.1
```

---

### Post by deadflowr on 2019-10-08
remove 'em both, if empty.
useless if empty.

If you need the dlang libraries or compilers or other just re-add the repos:
[https://d-apt.sourceforge.io/]("https://d-apt.sourceforge.io/")

---

### Post by brashley46 on 2019-10-09
Thanks ... Tried both of those suggestions. Result in Synaptic is: ```
GPG error: https://netcologne.dl.sourceforge.net/project/d-apt d-apt Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EBCF975E5BA24D5EThe repository 'https://netcologne.dl.sourceforge.net/project/d-apt d-apt Release' is not signed.Updating from such a repository can't be done securely, and is therefore disabled by default.See apt-secure(8) manpage for repository creation and user configuration details.Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'Sub-process returned an error code
```

---

### Post by brashley46 on 2019-10-10
So I ran ```
$ sudo apt-get update --allow-insecure-repositories && sudo apt-get -y --allow-unauthenticated install --reinstall d-apt-keyring && sudo apt-get update
``` again and I think it has solved the update problem ... will let you know if it recurs. Thanks!

---

