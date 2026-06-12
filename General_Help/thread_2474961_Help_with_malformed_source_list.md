---
title: "Help with malformed source list"
date: 2022-05-12
forum: General Help
---

### Post by dowo2 on 2022-05-12
I upgraded to jellyfish but can only boot up from recovery mode. When I do I can't get anywhere, I have no network and get an  error msge when trying to open synaptic package manager. The error is:
Failed to load the package list. This is a serious problem. Details below
E: Malformed line 1 in source list /etc/apt/sources.list (type)
E: The list of sources could not be read
E: _cache->open() failed, please report

Can anyone help with this. Thanks

---

### Post by deadflowr on 2022-05-12
Post the output from /etc/apt/sources.list
Since it states a malformed line 1 probably only need to use head like
```
head /etc/apt/sources.list
```
or for the full output post back the results of
```
cat /etc/apt/sources.list
```

---

### Post by dowo2 on 2022-05-12
```
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jammy main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) focal main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jammy-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) focal-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jammy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) focal universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jammy-updates universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) focal-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jammy multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) focal multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jammy-updates multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) focal-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jammy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse




deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse


# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end o
```

---

### Post by dowo2 on 2022-05-12
Hi below are the results of cat /etc/apt/sources.list

---

### Post by deadflowr on 2022-05-13
I don't see anything odd from the sources.list file
perhaps the full output from apt-get update might convey the issue better.

---

### Post by dowo2 on 2022-05-14
below is the output for apt-get update, also the output from apt-get upgrade.


IdeaPad-3-14IIL05:~$ sudo apt-get update
E: Malformed line 1 in source list /etc/apt/sources.list (type)
E: The list of sources could not be read.

ideaPad-3-14IIL05:~$ apt-get upgrade
E: Malformed line 1 in source list /etc/apt/sources.list (type)
E: The list of sources could not be read.
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?

---

### Post by Bashing-om on 2022-05-14
dowo2; Hey ---

How about we verify for sure what line one is ?
Post back:
```

cat -n /etc/apt/sources.list

```
where the "-n" flag generates line numbers.

[INDENT]gots to be something we are not seeing
[/INDENT]

---

### Post by dowo2 on 2022-05-15
hi - i have managed to get past the malformed source list output and now the output from apt-get update is as follows. any help really appreciated.

IdeaPad-3-14IIL05:~$ sudo apt-get update
Ign:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy InRelease
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Ign:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-updates InRelease
Ign:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-backports InRelease
Ign:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
Ign:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy InRelease
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Ign:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-updates InRelease
Ign:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-backports InRelease
Ign:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
Ign:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy InRelease
Ign:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-updates InRelease
Ign:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-backports InRelease
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Ign:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
Err:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy InRelease
  Temporary failure resolving &#8216;gb.archive.ubuntu.com&#8217;
Err:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-updates InRelease
  Temporary failure resolving &#8216;gb.archive.ubuntu.com&#8217;
Err:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-backports InRelease
  Temporary failure resolving &#8216;gb.archive.ubuntu.com&#8217;
Err:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
  Temporary failure resolving &#8216;dl.google.com&#8217;
Err:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
  Temporary failure resolving &#8216;security.ubuntu.com&#8217;
Reading package lists... Done
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jammy/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/jammy/InRelease)  Temporary failure resolving &#8216;gb.archive.ubuntu.com&#8217;
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease)  Temporary failure resolving &#8216;gb.archive.ubuntu.com&#8217;
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease)  Temporary failure resolving &#8216;gb.archive.ubuntu.com&#8217;
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease](http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease)  Temporary failure resolving &#8216;security.ubuntu.com&#8217;
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/InRelease](http://dl.google.com/linux/chrome/deb/dists/stable/InRelease)  Temporary failure resolving &#8216;dl.google.com&#8217;
W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ActionParsnip on 2022-05-15
If you run
```

echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null
sudo apt update 

```
Do updates run OK?

---

### Post by dowo2 on 2022-05-15
no updates don't run ok. below is the output from sudo apt update after running the nameserver 8.8.8.8 command. i have also posted the output from ping 8.8.8.8 as i get nowhere with that either.

IdeaPad-3-14IIL05:~$ echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null
[sudo] password for dom: 
IdeaPad-3-14IIL05:~$ sudo apt update
Ign:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
Ign:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy InRelease             
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease          
Ign:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-updates InRelease     
Ign:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-backports InRelease
Ign:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy InRelease
Ign:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Ign:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-updates InRelease
Ign:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-backports InRelease
Ign:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy InRelease
Ign:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Ign:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-updates InRelease
Ign:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-backports InRelease
Err:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease
  Temporary failure resolving &#8216;security.ubuntu.com&#8217;
Err:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
  Temporary failure resolving &#8216;dl.google.com&#8217;
Err:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy InRelease
  Temporary failure resolving &#8216;gb.archive.ubuntu.com&#8217;
Err:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-updates InRelease
  Temporary failure resolving &#8216;gb.archive.ubuntu.com&#8217;
Err:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-backports InRelease
  Temporary failure resolving &#8216;gb.archive.ubuntu.com&#8217;
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up-to-date.
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jammy/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/jammy/InRelease)  Temporary failure resolving &#8216;gb.archive.ubuntu.com&#8217;
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease)  Temporary failure resolving &#8216;gb.archive.ubuntu.com&#8217;
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease)  Temporary failure resolving &#8216;gb.archive.ubuntu.com&#8217;
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease](http://security.ubuntu.com/ubuntu/dists/jammy-security/InRelease)  Temporary failure resolving &#8216;security.ubuntu.com&#8217;
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/InRelease](http://dl.google.com/linux/chrome/deb/dists/stable/InRelease)  Temporary failure resolving &#8216;dl.google.com&#8217;
W: Some index files failed to download. They have been ignored, or old ones used instead.
IdeaPad-3-14IIL05:~$ 

IdeaPad-3-14IIL05:~$ ping 8.8.8.8
ping: connect: Network is unreachable
IdeaPad-3-14IIL05:~$

---

