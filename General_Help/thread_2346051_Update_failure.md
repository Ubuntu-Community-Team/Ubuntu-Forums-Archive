---
title: "Update failure"
date: 2016-12-10
forum: General Help
---

### Post by stuart_jones2 on 2016-12-10
My desktop is failing to update. Was away with work for the last few weeks and came home, tried to update via about computer, says either computer up to date or check internet connection. After a while a red triangle appears in the top task bar saying the update information is outdated, it then asks me to check manually with show updates, again the software is up to date. If I then click  install all updates I get the following script,

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/procps/libprocps4_3.3.10-4ubuntu2.2_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/procps/libprocps4_3.3.10-4ubuntu2.2_amd64.deb) 404  Not Found [IP: 91.189.88.162 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.3.10-4ubuntu2.2_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.3.10-4ubuntu2.2_amd64.deb) 404  Not Found [IP: 91.189.88.162 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/ubuntu-software_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/ubuntu-software_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_amd64.deb) 404  Not Found [IP: 91.189.88.162 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/gnome-software_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/gnome-software_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_amd64.deb) 404  Not Found [IP: 91.189.88.162 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/gnome-software-common_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/gnome-software-common_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_all.deb) 404  Not Found [IP: 91.189.88.162 80]

I would have last updated around 28th/ 29th Dec
Thanks in advance for any help

---

### Post by Bashing-om on 2016-12-10
stuart_jones2; Hello;

Certainly something to be concerned about.
What release is this ?
show:
```

lsb_release -a

```
And what does the package manager relate from terminal ?
```

sudo apt update
sudo apt upgrade

```

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by stuart_jones2 on 2016-12-10
Hi Bashing-om,
the release is

LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:printing-9.20160110ubuntu0.2-amd64:printing-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

sudo apt update=

Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease
Err:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease                     
  At least one invalid signature was encountered.
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Err:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease  
  At least one invalid signature was encountered.
Err:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease
  At least one invalid signature was encountered.
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]
Err:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease
  At least one invalid signature was encountered.
Fetched 306 kB in 2s (140 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
7 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease: At least one invalid signature was encountered.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease: At least one invalid signature was encountered.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease: At least one invalid signature was encountered.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease: At least one invalid signature was encountered.
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/xenial/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/xenial/InRelease)  At least one invalid signature was encountered.
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/xenial-updates/InRelease)  At least one invalid signature was encountered.
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease](http://gb.archive.ubuntu.com/ubuntu/dists/xenial-backports/InRelease)  At least one invalid signature was encountered.
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease](http://security.ubuntu.com/ubuntu/dists/xenial-security/InRelease)  At least one invalid signature was encountered.
W: Some index files failed to download. They have been ignored, or old ones used instead.

sudo apt upgrade =

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  gstreamer0.10-gconf gstreamer0.10-plugins-good gstreamer0.10-pulseaudio
  gstreamer0.10-x libcdaudio1 libfaac0 libslv2-9 linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-headers-4.4.0-34
  linux-headers-4.4.0-34-generic linux-headers-4.4.0-36
  linux-headers-4.4.0-36-generic linux-headers-4.4.0-38
  linux-headers-4.4.0-38-generic linux-headers-4.4.0-42
  linux-headers-4.4.0-42-generic linux-headers-4.4.0-43
  linux-headers-4.4.0-43-generic linux-image-4.4.0-31-generic
  linux-image-4.4.0-34-generic linux-image-4.4.0-36-generic
  linux-image-4.4.0-38-generic linux-image-4.4.0-42-generic
  linux-image-4.4.0-43-generic linux-image-extra-4.4.0-31-generic
  linux-image-extra-4.4.0-34-generic linux-image-extra-4.4.0-36-generic
  linux-image-extra-4.4.0-38-generic linux-image-extra-4.4.0-42-generic
  linux-image-extra-4.4.0-43-generic linux-signed-image-4.4.0-31-generic
  linux-signed-image-4.4.0-34-generic linux-signed-image-4.4.0-36-generic
  linux-signed-image-4.4.0-38-generic linux-signed-image-4.4.0-42-generic
  linux-signed-image-4.4.0-43-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  gnome-software gnome-software-common libprocps4 procps ubuntu-software
  update-notifier update-notifier-common
7 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 2,750 kB/2,961 kB of archives.
After this operation, 2,048 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libprocps4 amd64 2:3.3.10-4ubuntu2.2
  404  Not Found [IP: 91.189.88.161 80]
Err:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 procps amd64 2:3.3.10-4ubuntu2.2
  404  Not Found [IP: 91.189.88.161 80]
Err:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 ubuntu-software amd64 3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1
  404  Not Found [IP: 91.189.88.161 80]
Err:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 gnome-software amd64 3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1
  404  Not Found [IP: 91.189.88.161 80]
Err:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main i386 gnome-software-common all 3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1
  404  Not Found [IP: 91.189.88.161 80]
Err:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main i386 gnome-software-common all 3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1
  404  Not Found [IP: 91.189.88.161 80]
E: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/procps/libprocps4_3.3.10-4ubuntu2.2_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/procps/libprocps4_3.3.10-4ubuntu2.2_amd64.deb)  404  Not Found [IP: 91.189.88.161 80]

E: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.3.10-4ubuntu2.2_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.3.10-4ubuntu2.2_amd64.deb)  404  Not Found [IP: 91.189.88.161 80]

E: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/ubuntu-software_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/ubuntu-software_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_amd64.deb)  404  Not Found [IP: 91.189.88.161 80]

E: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/gnome-software_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_amd64.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/gnome-software_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_amd64.deb)  404  Not Found [IP: 91.189.88.161 80]

E: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/gnome-software-common_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/gnome-software-common_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_all.deb)  404  Not Found [IP: 91.189.88.161 80]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by oldos2er on 2016-12-10
Do you mean to say you haven't updated for almost a year?

I only checked the first file in your list, but indeed it does not exist at [http://gb.archive.ubuntu.com/ubuntu/pool/main/p/procps/](http://gb.archive.ubuntu.com/ubuntu/pool/main/p/procps/)

---

### Post by stuart_jones2 on 2016-12-10
Hi oldos2er, 
sorry 28th/ 29th 2016, just before I went away with work, I'm set to receive automatic updates

---

### Post by oldos2er on 2016-12-10
Ok.

I would try switching to the main server, then rerun ```
sudo apt-get update
```

---

### Post by #&amp;thj^% on 2016-12-10
You can try do this in the following way:

Open Terminal & run:

```
sudo -H gedit /etc/apt/sources.list

```
Replace url in.all "archive.ubuntu.com" and "security.ubuntu.com" with "old-releases.ubuntu.com"

save and close it.

Now run 
```
sudo apt update 
sudo apt autoremove
```

Now I would do a reboot and again run:
```
sudo apt update
sudo apt upgrade
sudo apt full-ugrade

```
Nin-jed by  oldos2er:D

---

### Post by stuart_jones2 on 2016-12-10
Sorry, how do I switch to the main server?

Hi 1fallen,
ran your first line, a second terminal opened and got this txt,

```
# deb cdrom:[Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
```

---

### Post by oldos2er on 2016-12-10
Open Software Center, click Software Sources. Click the dropdown menu next to Download from:, main server.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by #&amp;thj^% on 2016-12-10
> **stuart_jones2 said:**
> Hi 1fallen,
ran your first line, a second terminal opened and got this txt,

First do what oldos2er has advised as this might fix it... if not we will continue with the other method.:D

---

### Post by stuart_jones2 on 2016-12-11
Hi oldos2er,
ran the update from the main server, got the following,

```
stuart@stuart-ubuntu:~$ sudo apt-get update
[sudo] password for stuart: 
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease [247 kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]
Ign:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease     
Ign:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]
Ign:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main Sources [868 kB]
Ign:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease
Get:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/restricted Sources [4,808 B]     
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe Sources [7,728 kB]      
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/multiverse Sources [179 kB]      
Get:9 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 Packages [1,201 kB]   
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main i386 Packages [1,196 kB]   
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main Translation-en_GB [426 kB] 
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main Translation-en [568 kB]    
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 DEP-11 Metadata [733 kB]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main DEP-11 64x64 Icons [409 kB]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/restricted amd64 Packages [8,344 B]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/restricted i386 Packages [8,684 B]
Get:17 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/restricted Translation-en_GB [2,556 B]
Get:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/restricted Translation-en [2,908 B]
Get:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/restricted amd64 DEP-11 Metadata [186 B]
Get:20 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages [7,532 kB]
Get:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe i386 Packages [7,512 kB]
Get:22 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe Translation-en_GB [3,040 kB]
Get:23 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe Translation-en [4,354 kB]
Get:24 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 DEP-11 Metadata [3,410 kB]
Get:25 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe DEP-11 64x64 Icons [7,448 kB]
Get:26 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/multiverse amd64 Packages [144 kB]
Get:27 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/multiverse i386 Packages [140 kB]
Get:28 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/multiverse Translation-en_GB [88.1 kB]
Get:29 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/multiverse Translation-en [106 kB]
Get:30 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/multiverse amd64 DEP-11 Metadata [63.8 kB]
Get:31 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/multiverse DEP-11 64x64 Icons [230 kB]
Get:32 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main Sources [210 kB]   
Get:33 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/restricted Sources [1,804 B]
Get:34 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe Sources [112 kB]
Get:35 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/multiverse Sources [3,648 B]
Get:36 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [440 kB]
Get:37 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [433 kB]
Get:38 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en [171 kB]
Get:39 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [292 kB]
Get:40 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [184 kB]
Get:41 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/restricted amd64 Packages [6,576 B]
Get:42 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/restricted i386 Packages [6,528 B]
Get:43 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/restricted Translation-en [2,016 B]
Get:44 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/restricted amd64 DEP-11 Metadata [157 B]
Get:45 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [368 kB]
Get:46 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [364 kB]
Get:47 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en [134 kB]
Get:48 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [121 kB]
Get:49 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [145 kB]
Get:50 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 Packages [7,384 B]
Get:51 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/multiverse i386 Packages [6,172 B]
Get:52 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/multiverse Translation-en [2,988 B]
Get:53 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [2,520 B]
Get:54 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/multiverse DEP-11 64x64 Icons [7,765 B]
Get:55 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main Sources [3,252 B]
Get:56 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/universe Sources [1,868 B]
Get:57 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main amd64 Packages [4,396 B]
Get:58 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main i386 Packages [4,400 B]
Get:59 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main Translation-en [3,104 B]
Get:60 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [208 B]
Get:61 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main DEP-11 64x64 Icons [29 B]
Get:62 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/restricted amd64 DEP-11 Metadata [194 B]
Get:63 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 Packages [2,412 B]
Get:64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/universe i386 Packages [2,412 B]
Get:65 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/universe Translation-en [1,216 B]
Get:66 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [212 B]
Get:67 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/universe DEP-11 64x64 Icons [29 B]
Get:68 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/multiverse amd64 DEP-11 Metadata [216 B]
Get:69 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/multiverse DEP-11 64x64 Icons [29 B]
Get:70 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main Sources [52.5 kB] 
Get:71 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/restricted Sources [1,804 B]
Get:72 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/universe Sources [14.9 kB]
Get:73 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/multiverse Sources [728 B]
Get:74 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [189 kB]
Get:75 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main i386 Packages [184 kB]
Get:76 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main Translation-en [77.7 kB]
Get:77 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [68.0 kB]
Get:78 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [41.3 kB]
Get:79 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/restricted amd64 Packages [6,576 B]
Get:80 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/restricted i386 Packages [6,528 B]
Get:81 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/restricted Translation-en [2,016 B]
Get:82 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/restricted amd64 DEP-11 Metadata [200 B]
Get:83 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages [64.5 kB]
Get:84 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/universe i386 Packages [62.3 kB]
Get:85 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/universe Translation-en [35.1 kB]
Get:86 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [19.4 kB]
Get:87 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [25.6 kB]
Get:88 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/multiverse amd64 Packages [2,764 B]
Get:89 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/multiverse i386 Packages [2,928 B]
Get:90 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/multiverse Translation-en [1,124 B]
Get:91 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/multiverse amd64 DEP-11 Metadata [212 B]
Get:92 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security/multiverse DEP-11 64x64 Icons [29 B]
Fetched 51.9 MB in 4min 41s (184 kB/s)                                         
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease: At least one invalid signature was encountered.
W: The repository 'http://archive.ubuntu.com/ubuntu xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease: At least one invalid signature was encountered.
W: The repository 'http://archive.ubuntu.com/ubuntu xenial-updates InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease: At least one invalid signature was encountered.
W: The repository 'http://archive.ubuntu.com/ubuntu xenial-backports InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease: At least one invalid signature was encountered.
W: The repository 'http://archive.ubuntu.com/ubuntu xenial-security InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

then the update icon appeared, I clicked update, it said requires updates from untrusted packages, I click OK and it disapears

---

### Post by oldos2er on 2016-12-11
> AppStream cache update completed, but some metadata was ignored due to errors. This is a known bug, see [https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1644498](https://bugs.launchpad.net/ubuntu/+source/appstream/+bug/1644498)

There is some information on the W:GPG errors [here,]("http://askubuntu.com/questions/768569/ubuntu-16-04-update-manager-error") in particular see post #3. You can use the Software Sources program again to remove any PPAs and keys. Is there some reason you have backports enabled?

---

### Post by stuart_jones2 on 2016-12-11
Hi oldos2er,
you will need to bare with me, my knowledge and skill level is low, so to be completely honest I do not know what to do, I do not know what blackports are or how to enable/ disable them
sorry and thanks for your time so far

---

### Post by #&amp;thj^% on 2016-12-11
What happens when you run this:
```
sudo apt-key update
```
Post back the return.
Hang in here with us i think we can get this resolved.
It happened to me Early in the Development cycle and I got mine fixed.
Lets move a little slow at first...it is a process.

---

### Post by oldos2er on 2016-12-11
> **stuart_jones2 said:**
> Hi oldos2er,
you will need to bare with me, my knowledge and skill level is low, so to be completely honest I do not know what to do, I do not know what blackports are or how to enable/ disable them
sorry and thanks for your time so far

Not blackports, backports. From your earlier post:

```

Get:55 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main Sources [3,252 B]
Get:56 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/universe Sources [1,868 B]
Get:57 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main amd64 Packages [4,396 B]
Get:58 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main i386 Packages [4,400 B]
Get:59 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main Translation-en [3,104 B]
Get:60 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [208 B]
Get:61 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/main DEP-11 64x64 Icons [29 B]
Get:62 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/restricted amd64 DEP-11 Metadata [194 B]
Get:63 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 Packages [2,412 B]
Get:64 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/universe i386 Packages [2,412 B]
Get:65 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/universe Translation-en [1,216 B]
Get:66 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [212 B]
Get:67 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/universe DEP-11 64x64 Icons [29 B]
Get:68 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/multiverse amd64 DEP-11 Metadata [216 B]
Get:69 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports/multiverse DEP-11 64x64 Icons [29 B]
```

The backports repository is not enabled by default (at least I don't think it is, could be wrong) so you or someone with access to your system would have had to purposely enable it. Go back to Software & Updates, and under the Updates tab untick backports.

---

### Post by stuart_jones2 on 2016-12-12
Have unticked Backports

---

### Post by oldos2er on 2016-12-12
Ok, so run ```
sudo apt-key update
``` as 1fallen advised, followed by ```
sudo apt-get update
``` Please post the output here.

---

### Post by stuart_jones2 on 2016-12-12
```
stuart@stuart-ubuntu:~$ sudo apt-key update
[sudo] password for stuart: 
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
stuart@stuart-ubuntu:~$ sudo apt-get update
Get:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease [247 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]
Ign:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease  
Ign:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Ign:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security InRelease
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe Sources [112 kB]
Get:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [293 kB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [184 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [368 kB]
Get:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [364 kB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [121 kB]
Get:10 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [145 kB]
Get:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [2,516 B]
Get:12 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [68.2 kB]
Get:13 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [43.1 kB]
Get:14 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [19.4 kB]
Get:15 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [25.6 kB]
Get:16 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/multiverse amd64 DEP-11 Metadata [212 B]
Fetched 2,196 kB in 11s (185 kB/s)                                             
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
W: GPG error: [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease: At least one invalid signature was encountered.
W: The repository 'http://gb.archive.ubuntu.com/ubuntu xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease: At least one invalid signature was encountered.
W: The repository 'http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security InRelease: At least one invalid signature was encountered.
W: The repository 'http://gb.archive.ubuntu.com/ubuntu xenial-security InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

---

### Post by #&amp;thj^% on 2016-12-12
Yep that is just about the same outcome I expected to see.
Even if you were to when testing the signatures with gpg, you may even see errors like this:
The below is just informational only.."DO NOT FOLLOW"
```
#  cd /var/lib/apt/list
#  gpg --trustdb-name /etc/apt/trusted.gpg --verify  archive.ubuntu.com_ubuntu_dists_xenial-updates_Release
#  gpg: Signature made Sat 08 Oct 2016 04:33:51 NZDT using DSA key ID 437D05B5
#  gpg: 0: read expected rec type 1, got 153
#  gpg: fatal: /etc/apt/trusted.gpg: invalid trustdb
#  secmem usage: 1408/1408 bytes in 2/2 blocks of pool 1408/65536
```
My Fix Went exactly like this:
I Fix it by rebuilding the trust db **"As Root"**.
```
cd /etc/apt
mkdir save
mv trustdb.gpg trusted.gpg*  save/

```
Then try apt-get update again
```
sudo apt-get update
```
Now we "should" have some sigs working and some specific ones still missing for manually added repos keys.
Add individual missing keys left
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv <Key ID>

```
And if you are more comfortable waiting to see if oldos2er agrees... by all means wait for that conformation.

---

### Post by stuart_jones2 on 2016-12-12
Thanks again 1fallen,
started to input the code but got this response, so stopped,

stuart@stuart-ubuntu:~$ cd /etc/apt
stuart@stuart-ubuntu:/etc/apt$ mkdir save
mkdir: cannot create directory &#8216;save&#8217;: Permission denied
stuart@stuart-ubuntu:/etc/apt$

---

### Post by #&amp;thj^% on 2016-12-12
> **stuart_jones2 said:**
> Thanks again 1fallen,
started to input the code but got this response, so stopped,

stuart@stuart-ubuntu:~$ cd /etc/apt
stuart@stuart-ubuntu:/etc/apt$ mkdir save
mkdir: cannot create directory &#8216;save&#8217;: Permission denied
stuart@stuart-ubuntu:/etc/apt$

Please Read my post very carefully...as it clearly states "As Root"
It is better that you move slowly with a better understanding of what is being done here...(I'm not lecturing here just adding wisdom)
```
cd /etc/apt
```
Now we go to Super user or Root
```
sudo mkdir save
```
And continue
```
sudo mv trustdb.gpg trusted.gpg*  save/
```
And Now run:
```
sudo apt-get update
```

---

### Post by stuart_jones2 on 2016-12-12
Thanks 1fallen, I do not see you as lecturing, I do need to be told what to do, so I appreciate simple wisdom,
this is what came up, 

stuart@stuart-ubuntu:~$ cd /etc/apt
stuart@stuart-ubuntu:/etc/apt$ sudo mkdir save
[sudo] password for stuart: 
stuart@stuart-ubuntu:/etc/apt$ sudo mv trustdb.gpg trusted.gpg* secring.gpg save/
mv: cannot stat 'trustdb.gpg': No such file or directory
mv: cannot stat 'secring.gpg': No such file or directory
stuart@stuart-ubuntu:/etc/apt$

---

### Post by #&amp;thj^% on 2016-12-12
While in that same Directory "/etc/apt"
What is listed there...I do things a bit different at times.
Just to be sure:
```
cd /etc/apt
ls
```
Paste back what shows;)

---

### Post by stuart_jones2 on 2016-12-12
stuart@stuart-ubuntu:~$ cd /etc/apt
stuart@stuart-ubuntu:/etc/apt$ ls
apt.conf.d     save          sources.list.d            sources.list.save
preferences.d  sources.list  sources.list.distUpgrade
stuart@stuart-ubuntu:/etc/apt$

---

### Post by #&amp;thj^% on 2016-12-12
Can you navigate with your File manager to /etc/apt and check to see if there is a Folder in there Named "saved"...and if there is...see if there is also a folder named "trusted.gpd.d" in there...That is in the "saved" folder if it exists.

---

### Post by stuart_jones2 on 2016-12-12
Sorry, how do I find file manager? it does not show up in a search

---

### Post by #&amp;thj^% on 2016-12-12
If you are using Unity...the file manager will be nautilus.. And if you are not using unity...
give me the output of this from the terminal:
```
echo $DESKTOP_SESSION
```

---

### Post by stuart_jones2 on 2016-12-12
stuart@stuart-ubuntu:~$ echo $DESKTOP_SESSION
ubuntu
stuart@stuart-ubuntu:~$

---

### Post by #&amp;thj^% on 2016-12-12
Ok then yes Nautilus will be your file manager. "Or a search for files" from your launcher.
And you will have to look in the left side of Nautilus and find Other or Computer to find /etc...then /apt and open and check for what I had asked to see if there is a Folder in there Named **"saved"**...and if there is...see if  there is also a folder named "**trusted.gpd.d" **in there...That should be in the  **"saved" folder**" if it exists. That is what i need to know.
Screenshot included to help.

---

### Post by #&amp;thj^% on 2016-12-12
Hello stuart_jones2 Did I lose you?
Requesting a update for this
**EDIT: i**f this is easier for you...open the terminal and issue this:
```
cd /etc/apt/save
###and now show me the contents there###
ls
```
Paste them back here...I just need to know there are these 3 files in there:
"**trusted.gpd.d**" and "**trusted.gpd**" and it is not really important if this one is not in it "**trusted.gpd~**"
And if those are there you can now go ahead and run this:
```
sudo apt-key update
sudo apt update
```
Post back the results....and from there we will begin to fix the missing "keys"

---

### Post by stuart_jones2 on 2016-12-13
Hi 1fallen, sorry I didn't reply last night either my internet or the forum crashed.
I have the foldertrusted.gpd.d in contains 2 items, jockey-drivers.gpg twice, but I do not have permission to open them

---

### Post by stuart_jones2 on 2016-12-13
stuart@stuart-ubuntu:~$ cd etc/apt/save
bash: cd: etc/apt/save: No such file or directory
stuart@stuart-ubuntu:~$

---

### Post by #&amp;thj^% on 2016-12-13
> **stuart_jones2 said:**
> Hi 1fallen, sorry I didn't reply last night either my internet or the forum crashed.
I have the foldertrusted.gpd.d in contains 2 items, jockey-drivers.gpg twice, but I do not have permission to open them
Yes I was also noticing the forums glitch.
And yes you will need elevated privileges to open them...But we **do not need to open them** at this point.
> **stuart_jones2 said:**
> stuart@stuart-ubuntu:~$ cd etc/apt/save
bash: cd: etc/apt/save: No such file or directory
stuart@stuart-ubuntu:~$
You entered the wrong code...or i told you the wrong code...but it goes as follows:
Here is mine:
```
cd /etc/apt/save
me@me-System-Product-Name:/etc/apt/save$ ls
[COLOR=#ff0000]trusted.gpg[/COLOR]  trusted.gpg~ [COLOR=#ff0000] trusted.gpg.d[/COLOR]

```
The highlighted in red is what I wanted to be sure was there...it is a back-up if we need it later.
I know you are at work today so I will just keep my eye on this thread...and we will resume when you are ready.
Good News though we are just about done here.;)

---

### Post by stuart_jones2 on 2016-12-13
Thanks again for your patience 1fallen, it is appreciated.
This is what I got this time,

stuart@stuart-ubuntu:~$ cd /etc/apt/save
stuart@stuart-ubuntu:/etc/apt/save$ me@me-System-Product-Name:/etc/apt/save$ ls
bash: me@me-System-Product-Name:/etc/apt/save$: No such file or directory
stuart@stuart-ubuntu:/etc/apt/save$

---

### Post by #&amp;thj^% on 2016-12-13
Greetings..Ok we will do this one step at a time...first
```
cd /etc/apt/save
```
And then:
```
ls
```
Paste back just the return of the "ls"

---

### Post by stuart_jones2 on 2016-12-13
trusted.gpg  trusted.gpg~  trusted.gpg.d

---

### Post by #&amp;thj^% on 2016-12-13
Ya buddy... that is what I wanted to see:KS...
Now we do this:
```
sudo apt-key update
```
Followed by:
```
sudo apt update
```
Now this will be a Long out put...and it would be very helpful to me if you could wrap that return in Code Tags...if not just paste it back here as to not confuse this any more.

---

### Post by stuart_jones2 on 2016-12-13
```
stuart@stuart-ubuntu:~$ sudo apt-key update
[sudo] password for stuart: 
stuart@stuart-ubuntu:~$ sudo apt update
Get:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease [247 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]   
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main Sources [211 kB] 
Get:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe Sources [113 kB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/multiverse Sources [3,640 B]
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [440 kB]
Get:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [433 kB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en [171 kB]
Get:10 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [293 kB]
Get:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [187 kB]
Get:12 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [370 kB]
Get:13 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [366 kB]
Get:14 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en [134 kB]
Get:15 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [121 kB]
Get:16 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [145 kB]
Get:17 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 Packages [7,376 B]
Get:18 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/multiverse i386 Packages [6,172 B]
Get:19 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [2,520 B]
Get:20 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/main Sources [53.0 kB]
Get:21 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/universe Sources [15.3 kB]
Get:22 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/multiverse Sources [724 B]
Get:23 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [191 kB]
Get:24 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/main i386 Packages [185 kB]
Get:25 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/main Translation-en [78.7 kB]
Get:26 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [68.1 kB]
Get:27 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [44.1 kB]
Get:28 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages [64.8 kB]
Get:29 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/universe i386 Packages [62.6 kB]
Get:30 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/universe Translation-en [35.5 kB]
Get:31 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [19.4 kB]
Get:32 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [25.6 kB]
Get:33 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/multiverse amd64 Packages [2,756 B]
Get:34 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/multiverse i386 Packages [2,928 B]
Get:35 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-security/multiverse amd64 DEP-11 Metadata [212 B]
Fetched 4,303 kB in 25s (169 kB/s)                                             
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
85 packages can be upgraded. Run 'apt list --upgradable' to see them.
stuart@stuart-ubuntu:~$ 
```

Should I run the last line??

---

### Post by #&amp;thj^% on 2016-12-13
Ya I forgot about that one...I seen it yesterday but thought it would be ok just to ignore ATM
But yes...lets have a look:
```
sudo apt list --upgradable
```
Paste back again

---

### Post by stuart_jones2 on 2016-12-13
```
stuart@stuart-ubuntu:~$ sudo apt list --upgradable
Listing... Done
apport/xenial-updates,xenial-updates 2.20.1-0ubuntu2.2 all [upgradable from: 2.20.1-0ubuntu2.1]
apport-gtk/xenial-updates,xenial-updates 2.20.1-0ubuntu2.2 all [upgradable from: 2.20.1-0ubuntu2.1]
apt/xenial-updates,xenial-security 1.2.15ubuntu0.2 amd64 [upgradable from: 1.2.15]
apt-transport-https/xenial-updates,xenial-security 1.2.15ubuntu0.2 amd64 [upgradable from: 1.2.15]
apt-utils/xenial-updates,xenial-security 1.2.15ubuntu0.2 amd64 [upgradable from: 1.2.15]
bind9-host/xenial-updates 1:9.10.3.dfsg.P4-8ubuntu1.3 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
dnsutils/xenial-updates 1:9.10.3.dfsg.P4-8ubuntu1.3 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
firefox/xenial-updates,xenial-security 50.1.0+build2-0ubuntu0.16.04.1 amd64 [upgradable from: 50.0+build2-0ubuntu0.16.04.2]
firefox-locale-en/xenial-updates,xenial-security 50.1.0+build2-0ubuntu0.16.04.1 amd64 [upgradable from: 50.0+build2-0ubuntu0.16.04.2]
flashplugin-installer/xenial-updates,xenial-security 24.0.0.186ubuntu0.16.04.1 amd64 [upgradable from: 11.2.202.644ubuntu0.16.04.1]
ghostscript/xenial-updates,xenial-security 9.18~dfsg~0-0ubuntu2.3 amd64 [upgradable from: 9.18~dfsg~0-0ubuntu2]
ghostscript-x/xenial-updates,xenial-security 9.18~dfsg~0-0ubuntu2.3 amd64 [upgradable from: 9.18~dfsg~0-0ubuntu2]
gnome-software/xenial-updates 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 amd64 [upgradable from: 3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1]
gnome-software-common/xenial-updates,xenial-updates 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 all [upgradable from: 3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1]
gstreamer0.10-gconf/xenial-updates,xenial-security 0.10.31-3+nmu4ubuntu2.16.04.2 amd64 [upgradable from: 0.10.31-3+nmu4ubuntu2.16.04.1]
gstreamer0.10-plugins-good/xenial-updates,xenial-security 0.10.31-3+nmu4ubuntu2.16.04.2 amd64 [upgradable from: 0.10.31-3+nmu4ubuntu2.16.04.1]
gstreamer0.10-pulseaudio/xenial-updates,xenial-security 0.10.31-3+nmu4ubuntu2.16.04.2 amd64 [upgradable from: 0.10.31-3+nmu4ubuntu2.16.04.1]
gstreamer1.0-plugins-good/xenial-updates,xenial-security 1.8.2-1ubuntu0.3 amd64 [upgradable from: 1.8.2-1ubuntu0.2]
gstreamer1.0-pulseaudio/xenial-updates,xenial-security 1.8.2-1ubuntu0.3 amd64 [upgradable from: 1.8.2-1ubuntu0.2]
im-config/xenial-updates,xenial-updates 0.29-1ubuntu12.3 all [upgradable from: 0.29-1ubuntu12.2]
imagemagick/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.3 amd64 [upgradable from: 8:6.8.9.9-7ubuntu5.2]
imagemagick-6.q16/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.3 amd64 [upgradable from: 8:6.8.9.9-7ubuntu5.2]
imagemagick-common/xenial-updates,xenial-updates,xenial-security,xenial-security 8:6.8.9.9-7ubuntu5.3 all [upgradable from: 8:6.8.9.9-7ubuntu5.2]
libapt-inst2.0/xenial-updates,xenial-security 1.2.15ubuntu0.2 amd64 [upgradable from: 1.2.15]
libapt-pkg5.0/xenial-updates,xenial-security 1.2.15ubuntu0.2 amd64 [upgradable from: 1.2.15]
libbind9-140/xenial-updates 1:9.10.3.dfsg.P4-8ubuntu1.3 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
libc-bin/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu4]
libc-dev-bin/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu4]
libc6/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu4]
libc6-dbg/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu4]
libc6-dev/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu4]
libc6-i386/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu4]
libdns-export162/xenial-updates 1:9.10.3.dfsg.P4-8ubuntu1.3 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
libdns162/xenial-updates 1:9.10.3.dfsg.P4-8ubuntu1.3 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
libgme0/xenial-updates,xenial-security 0.6.0-3ubuntu0.16.04.1 amd64 [upgradable from: 0.6.0-3]
libgs9/xenial-updates,xenial-security 9.18~dfsg~0-0ubuntu2.3 amd64 [upgradable from: 9.18~dfsg~0-0ubuntu2]
libgs9-common/xenial-updates,xenial-updates,xenial-security,xenial-security 9.18~dfsg~0-0ubuntu2.3 all [upgradable from: 9.18~dfsg~0-0ubuntu2]
libgstreamer-plugins-good1.0-0/xenial-updates,xenial-security 1.8.2-1ubuntu0.3 amd64 [upgradable from: 1.8.2-1ubuntu0.2]
libisc-export160/xenial-updates 1:9.10.3.dfsg.P4-8ubuntu1.3 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
libisc160/xenial-updates 1:9.10.3.dfsg.P4-8ubuntu1.3 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
libisccc140/xenial-updates 1:9.10.3.dfsg.P4-8ubuntu1.3 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
libisccfg140/xenial-updates 1:9.10.3.dfsg.P4-8ubuntu1.3 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
liblwres141/xenial-updates 1:9.10.3.dfsg.P4-8ubuntu1.3 amd64 [upgradable from: 1:9.10.3.dfsg.P4-8ubuntu1.2]
libmagickcore-6.q16-2/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.3 amd64 [upgradable from: 8:6.8.9.9-7ubuntu5.2]
libmagickcore-6.q16-2-extra/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.3 amd64 [upgradable from: 8:6.8.9.9-7ubuntu5.2]
libmagickwand-6.q16-2/xenial-updates,xenial-security 8:6.8.9.9-7ubuntu5.3 amd64 [upgradable from: 8:6.8.9.9-7ubuntu5.2]
liboxideqt-qmlplugin/xenial-updates,xenial-security 1.19.4-0ubuntu0.16.04.1 amd64 [upgradable from: 1.18.3-0ubuntu0.16.04.1]
liboxideqtcore0/xenial-updates,xenial-security 1.19.4-0ubuntu0.16.04.1 amd64 [upgradable from: 1.18.3-0ubuntu0.16.04.1]
liboxideqtquick0/xenial-updates,xenial-security 1.19.4-0ubuntu0.16.04.1 amd64 [upgradable from: 1.18.3-0ubuntu0.16.04.1]
libprocps4/xenial-updates 2:3.3.10-4ubuntu2.3 amd64 [upgradable from: 2:3.3.10-4ubuntu2]
linux-generic/xenial-updates,xenial-security 4.4.0.53.56 amd64 [upgradable from: 4.4.0.47.50]
linux-headers-generic/xenial-updates,xenial-security 4.4.0.53.56 amd64 [upgradable from: 4.4.0.47.50]
linux-image-generic/xenial-updates,xenial-security 4.4.0.53.56 amd64 [upgradable from: 4.4.0.47.50]
linux-libc-dev/xenial-updates,xenial-security 4.4.0-53.74 amd64 [upgradable from: 4.4.0-47.68]
linux-signed-generic/xenial-updates,xenial-security 4.4.0.53.56 amd64 [upgradable from: 4.4.0.47.50]
linux-signed-image-generic/xenial-updates,xenial-security 4.4.0.53.56 amd64 [upgradable from: 4.4.0.47.50]
locales/xenial-updates,xenial-updates 2.23-0ubuntu5 all [upgradable from: 2.23-0ubuntu4]
multiarch-support/xenial-updates 2.23-0ubuntu5 amd64 [upgradable from: 2.23-0ubuntu4]
oxideqt-codecs-extra/xenial-updates,xenial-security 1.19.4-0ubuntu0.16.04.1 amd64 [upgradable from: 1.18.3-0ubuntu0.16.04.1]
procps/xenial-updates 2:3.3.10-4ubuntu2.3 amd64 [upgradable from: 2:3.3.10-4ubuntu2]
python-apport/xenial-updates,xenial-updates 2.20.1-0ubuntu2.2 all [upgradable from: 2.20.1-0ubuntu2.1]
python-cryptography/xenial-updates,xenial-security 1.2.3-1ubuntu0.1 amd64 [upgradable from: 1.2.3-1]
python-problem-report/xenial-updates,xenial-updates 2.20.1-0ubuntu2.2 all [upgradable from: 2.20.1-0ubuntu2.1]
python3-apport/xenial-updates,xenial-updates 2.20.1-0ubuntu2.2 all [upgradable from: 2.20.1-0ubuntu2.1]
python3-cryptography/xenial-updates,xenial-security 1.2.3-1ubuntu0.1 amd64 [upgradable from: 1.2.3-1]
python3-distupgrade/xenial-updates,xenial-updates 1:16.04.19 all [upgradable from: 1:16.04.18]
python3-problem-report/xenial-updates,xenial-updates 2.20.1-0ubuntu2.2 all [upgradable from: 2.20.1-0ubuntu2.1]
python3-software-properties/xenial-updates,xenial-updates 0.96.20.5 all [upgradable from: 0.96.20.4]
snapd/xenial-updates 2.17.1ubuntu1 amd64 [upgradable from: 2.16ubuntu3]
software-properties-common/xenial-updates,xenial-updates 0.96.20.5 all [upgradable from: 0.96.20.4]
software-properties-gtk/xenial-updates,xenial-updates 0.96.20.5 all [upgradable from: 0.96.20.4]
thunderbird/xenial-updates,xenial-security 1:45.5.1+build1-0ubuntu0.16.04.1 amd64 [upgradable from: 1:45.4.0+build1-0ubuntu0.16.04.1]
thunderbird-gnome-support/xenial-updates,xenial-security 1:45.5.1+build1-0ubuntu0.16.04.1 amd64 [upgradable from: 1:45.4.0+build1-0ubuntu0.16.04.1]
thunderbird-locale-en/xenial-updates,xenial-security 1:45.5.1+build1-0ubuntu0.16.04.1 amd64 [upgradable from: 1:45.4.0+build1-0ubuntu0.16.04.1]
thunderbird-locale-en-us/xenial-updates,xenial-updates,xenial-security,xenial-security 1:45.5.1+build1-0ubuntu0.16.04.1 all [upgradable from: 1:45.4.0+build1-0ubuntu0.16.04.1]
tzdata/xenial-updates,xenial-updates,xenial-security,xenial-security 2016j-0ubuntu0.16.04 all [upgradable from: 2016h-0ubuntu0.16.04]
ubuntu-release-upgrader-core/xenial-updates,xenial-updates 1:16.04.19 all [upgradable from: 1:16.04.18]
ubuntu-release-upgrader-gtk/xenial-updates,xenial-updates 1:16.04.19 all [upgradable from: 1:16.04.18]
ubuntu-software/xenial-updates 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 amd64 [upgradable from: 3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1]
update-notifier/xenial-updates 3.168.2 amd64 [upgradable from: 3.168.1]
update-notifier-common/xenial-updates,xenial-updates 3.168.2 all [upgradable from: 3.168.1]
vim-common/xenial-updates,xenial-security 2:7.4.1689-3ubuntu1.2 amd64 [upgradable from: 2:7.4.1689-3ubuntu1.1]
vim-tiny/xenial-updates,xenial-security 2:7.4.1689-3ubuntu1.2 amd64 [upgradable from: 2:7.4.1689-3ubuntu1.1]
xserver-xorg-video-intel/xenial-updates 2:2.99.917+git20160325-1ubuntu1.2 amd64 [upgradable from: 2:2.99.917+git20160325-1ubuntu1.1]
stuart@stuart-ubuntu:~$
```

---

### Post by #&amp;thj^% on 2016-12-13
Ok... Holy Cow you are in need of some updates:o
Do this:
```
cd /etc/apt
```
```
sudo mv sources.list.distUpgrade save/
```
Now run 
```
sudo apt clean
```
And Again
```
sudo apt update
```
and paste back

---

### Post by stuart_jones2 on 2016-12-13
```
stuart@stuart-ubuntu:~$ cd /etc/apt
stuart@stuart-ubuntu:/etc/apt$ sudo mv sources.list.distUpgrade save/
[sudo] password for stuart: 
stuart@stuart-ubuntu:/etc/apt$ sudo apt clean
stuart@stuart-ubuntu:/etc/apt$ sudo apt update
Hit:1 http://gb.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Fetched 204 kB in 6s (32.5 kB/s)                                               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
85 packages can be upgraded. Run 'apt list --upgradable' to see them.
stuart@stuart-ubuntu:/etc/apt$
```

---

### Post by #&amp;thj^% on 2016-12-13
Ok now you should get a lot of updates with
```
cd
```
And:
```
sudo apt upgrade
```
Might as well get the mother-load also.
With
```
sudo apt full-upgrade
```
Let me know how all this goes.

---

### Post by stuart_jones2 on 2016-12-13
I think it's updating, but I have a slow internet, about 40 mins to it completing, my next reply might be in a while!!

---

### Post by #&amp;thj^% on 2016-12-13
I'll be here.;)
But after this I'm taking a Long Vacation...:lolflag:

---

### Post by stuart_jones2 on 2016-12-13
To be fair your patience deserves it

---

### Post by #&amp;thj^% on 2016-12-13
All in a Days Work.
And Most importantly maybe you have learned a little more along the way.:)

---

### Post by stuart_jones2 on 2016-12-13
What I have learnt, is as always the forums are full of brilliant and helpful people, who without, I would have to use windows and that would pain me!!!
At 68%!!

---

### Post by #&amp;thj^% on 2016-12-13
You know this is one of.. if not the "Nicest little Community" you will find on the web.
I have grown to be quite found of UF over the years...and I have learned or at least had the opportunity to grow from some Very Brilliant users and Developers and Staff here.
And not to sound sappy here but my life is that much more enriched from the experience.

---

### Post by stuart_jones2 on 2016-12-13
```
stuart@stuart-ubuntu:/etc/apt$ cd
stuart@stuart-ubuntu:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  gstreamer0.10-gconf gstreamer0.10-plugins-good gstreamer0.10-pulseaudio
  gstreamer0.10-x libcdaudio1 libfaac0 libslv2-9 linux-headers-4.4.0-31
  linux-headers-4.4.0-31-generic linux-headers-4.4.0-34
  linux-headers-4.4.0-34-generic linux-headers-4.4.0-36
  linux-headers-4.4.0-36-generic linux-headers-4.4.0-38
  linux-headers-4.4.0-38-generic linux-headers-4.4.0-42
  linux-headers-4.4.0-42-generic linux-headers-4.4.0-43
  linux-headers-4.4.0-43-generic linux-image-4.4.0-31-generic
  linux-image-4.4.0-34-generic linux-image-4.4.0-36-generic
  linux-image-4.4.0-38-generic linux-image-4.4.0-42-generic
  linux-image-4.4.0-43-generic linux-image-extra-4.4.0-31-generic
  linux-image-extra-4.4.0-34-generic linux-image-extra-4.4.0-36-generic
  linux-image-extra-4.4.0-38-generic linux-image-extra-4.4.0-42-generic
  linux-image-extra-4.4.0-43-generic linux-signed-image-4.4.0-31-generic
  linux-signed-image-4.4.0-34-generic linux-signed-image-4.4.0-36-generic
  linux-signed-image-4.4.0-38-generic linux-signed-image-4.4.0-42-generic
  linux-signed-image-4.4.0-43-generic ubuntu-core-launcher
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed
  libsnapd-glib1 linux-headers-4.4.0-53 linux-headers-4.4.0-53-generic
  linux-image-4.4.0-53-generic linux-image-extra-4.4.0-53-generic
  linux-signed-image-4.4.0-53-generic snapd-login-service
The following packages will be upgraded:
  apport apport-gtk apt apt-transport-https apt-utils bind9-host dnsutils
  firefox firefox-locale-en flashplugin-installer ghostscript ghostscript-x
  gnome-software gnome-software-common gstreamer0.10-gconf
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio
  gstreamer1.0-plugins-good gstreamer1.0-pulseaudio im-config imagemagick
  imagemagick-6.q16 imagemagick-common libapt-inst2.0 libapt-pkg5.0
  libbind9-140 libc-bin libc-dev-bin libc6 libc6:i386 libc6-dbg libc6-dev
  libc6-i386 libdns-export162 libdns162 libgme0 libgs9 libgs9-common
  libgstreamer-plugins-good1.0-0 libisc-export160 libisc160 libisccc140
  libisccfg140 liblwres141 libmagickcore-6.q16-2 libmagickcore-6.q16-2-extra
  libmagickwand-6.q16-2 liboxideqt-qmlplugin liboxideqtcore0 liboxideqtquick0
  libprocps4 linux-generic linux-headers-generic linux-image-generic
  linux-libc-dev linux-signed-generic linux-signed-image-generic locales
  multiarch-support oxideqt-codecs-extra procps python-apport
  python-cryptography python-problem-report python3-apport
  python3-cryptography python3-distupgrade python3-problem-report
  python3-software-properties snapd software-properties-common
  software-properties-gtk thunderbird thunderbird-gnome-support
  thunderbird-locale-en thunderbird-locale-en-us tzdata
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk ubuntu-software
  update-notifier update-notifier-common vim-common vim-tiny
  xserver-xorg-video-intel
85 to upgrade, 7 to newly install, 0 to remove and 0 not to upgrade.
Need to get 229 MB of archives.
After this operation, 300 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6-dbg amd64 2.23-0ubuntu5 [3,685 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6-dev amd64 2.23-0ubuntu5 [2,078 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc-dev-bin amd64 2.23-0ubuntu5 [68.7 kB]
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-libc-dev amd64 4.4.0-53.74 [835 kB]
Get:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6-i386 amd64 2.23-0ubuntu5 [2,329 kB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc6 amd64 2.23-0ubuntu5 [2,589 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main i386 libc6 i386 2.23-0ubuntu5 [2,268 kB]
Get:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 locales all 2.23-0ubuntu5 [3,215 kB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libc-bin amd64 2.23-0ubuntu5 [638 kB]
Get:10 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libapt-pkg5.0 amd64 1.2.15ubuntu0.2 [702 kB]
Get:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libapt-inst2.0 amd64 1.2.15ubuntu0.2 [55.7 kB]
Get:12 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 apt amd64 1.2.15ubuntu0.2 [1,042 kB]
Get:13 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 apt-utils amd64 1.2.15ubuntu0.2 [196 kB]
Get:14 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libmagickwand-6.q16-2 amd64 8:6.8.9.9-7ubuntu5.3 [288 kB]
Get:15 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libmagickcore-6.q16-2 amd64 8:6.8.9.9-7ubuntu5.3 [1,576 kB]
Get:16 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 imagemagick-common all 8:6.8.9.9-7ubuntu5.3 [42.0 kB]
Get:17 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 ubuntu-release-upgrader-gtk all 1:16.04.19 [9,366 B]
Get:18 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 ubuntu-release-upgrader-core all 1:16.04.19 [29.3 kB]
Get:19 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 python3-distupgrade all 1:16.04.19 [104 kB]
Get:20 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 update-notifier amd64 3.168.2 [48.2 kB]
Get:21 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 update-notifier-common all 3.168.2 [163 kB]
Get:22 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 multiarch-support amd64 2.23-0ubuntu5 [6,832 B]
Get:23 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libprocps4 amd64 2:3.3.10-4ubuntu2.3 [32.8 kB]
Get:24 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 procps amd64 2:3.3.10-4ubuntu2.3 [222 kB]
Get:25 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 tzdata all 2016j-0ubuntu0.16.04 [168 kB]
Get:26 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libisc-export160 amd64 1:9.10.3.dfsg.P4-8ubuntu1.3 [152 kB]
Get:27 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libdns-export162 amd64 1:9.10.3.dfsg.P4-8ubuntu1.3 [666 kB]
Get:28 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 vim-tiny amd64 2:7.4.1689-3ubuntu1.2 [445 kB]
Get:29 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 vim-common amd64 2:7.4.1689-3ubuntu1.2 [103 kB]
Get:30 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 apt-transport-https amd64 1.2.15ubuntu0.2 [26.0 kB]
Get:31 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 dnsutils amd64 1:9.10.3.dfsg.P4-8ubuntu1.3 [89.2 kB]
Get:32 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 bind9-host amd64 1:9.10.3.dfsg.P4-8ubuntu1.3 [38.4 kB]
Get:33 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libisc160 amd64 1:9.10.3.dfsg.P4-8ubuntu1.3 [214 kB]
Get:34 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libdns162 amd64 1:9.10.3.dfsg.P4-8ubuntu1.3 [877 kB]
Get:35 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libisccc140 amd64 1:9.10.3.dfsg.P4-8ubuntu1.3 [16.3 kB]
Get:36 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libisccfg140 amd64 1:9.10.3.dfsg.P4-8ubuntu1.3 [40.6 kB]
Get:37 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 liblwres141 amd64 1:9.10.3.dfsg.P4-8ubuntu1.3 [33.0 kB]
Get:38 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libbind9-140 amd64 1:9.10.3.dfsg.P4-8ubuntu1.3 [23.6 kB]
Get:39 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 python3-problem-report all 2.20.1-0ubuntu2.2 [9,894 B]
Get:40 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 python3-apport all 2.20.1-0ubuntu2.2 [79.5 kB]
Get:41 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 apport all 2.20.1-0ubuntu2.2 [120 kB]
Get:42 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 apport-gtk all 2.20.1-0ubuntu2.2 [9,456 B]
Get:43 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 firefox amd64 50.1.0+build2-0ubuntu0.16.04.1 [45.8 MB]
Get:44 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 firefox-locale-en amd64 50.1.0+build2-0ubuntu0.16.04.1 [638 kB]
Get:45 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 flashplugin-installer amd64 24.0.0.186ubuntu0.16.04.1 [6,804 B]
Get:46 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 ghostscript amd64 9.18~dfsg~0-0ubuntu2.3 [40.9 kB]
Get:47 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 ghostscript-x amd64 9.18~dfsg~0-0ubuntu2.3 [34.3 kB]
Get:48 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libgs9-common all 9.18~dfsg~0-0ubuntu2.3 [2,981 kB]
Get:49 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libgs9 amd64 9.18~dfsg~0-0ubuntu2.3 [2,059 kB]
Get:50 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 ubuntu-software amd64 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 [11.6 kB]
Get:51 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 gnome-software amd64 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 [227 kB]
Get:52 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 gnome-software-common all 3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1 [2,257 kB]
Get:53 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libsnapd-glib1 amd64 1.2-0ubuntu1.1~xenial [35.5 kB]
Get:54 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 gstreamer0.10-gconf amd64 0.10.31-3+nmu4ubuntu2.16.04.2 [68.7 kB]
Get:55 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 gstreamer0.10-plugins-good amd64 0.10.31-3+nmu4ubuntu2.16.04.2 [1,517 kB]
Get:56 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 gstreamer0.10-pulseaudio amd64 0.10.31-3+nmu4ubuntu2.16.04.2 [104 kB]
Get:57 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 gstreamer1.0-plugins-good amd64 1.8.2-1ubuntu0.3 [1,529 kB]
Get:58 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libgstreamer-plugins-good1.0-0 amd64 1.8.2-1ubuntu0.3 [32.7 kB]
Get:59 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 gstreamer1.0-pulseaudio amd64 1.8.2-1ubuntu0.3 [55.9 kB]
Get:60 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 im-config all 0.29-1ubuntu12.3 [23.2 kB]
Get:61 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 imagemagick amd64 8:6.8.9.9-7ubuntu5.3 [44.8 kB]
Get:62 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 imagemagick-6.q16 amd64 8:6.8.9.9-7ubuntu5.3 [388 kB]
Get:63 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 libgme0 amd64 0.6.0-3ubuntu0.16.04.1 [122 kB]
Get:64 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libmagickcore-6.q16-2-extra amd64 8:6.8.9.9-7ubuntu5.3 [59.4 kB]
Get:65 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-image-4.4.0-53-generic amd64 4.4.0-53.74 [19.2 MB]
Get:66 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-image-extra-4.4.0-53-generic amd64 4.4.0-53.74 [38.6 MB]
Get:67 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-generic amd64 4.4.0.53.56 [1,786 B]
Get:68 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-image-generic amd64 4.4.0.53.56 [2,302 B]
Get:69 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-signed-image-4.4.0-53-generic amd64 4.4.0-53.74 [4,002 B]
Get:70 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-signed-generic amd64 4.4.0.53.56 [1,820 B]
Get:71 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-signed-image-generic amd64 4.4.0.53.56 [2,342 B]
Get:72 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-headers-4.4.0-53 all 4.4.0-53.74 [9,953 kB]
Get:73 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-headers-4.4.0-53-generic amd64 4.4.0-53.74 [782 kB]
Get:74 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-headers-generic amd64 4.4.0.53.56 [2,274 B]
Get:75 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 python-problem-report all 2.20.1-0ubuntu2.2 [9,802 B]
Get:76 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 python-apport all 2.20.1-0ubuntu2.2 [79.3 kB]
Get:77 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 python-cryptography amd64 1.2.3-1ubuntu0.1 [199 kB]
Get:78 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 python3-cryptography amd64 1.2.3-1ubuntu0.1 [199 kB]
Get:79 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 software-properties-common all 0.96.20.5 [9,432 B]
Get:80 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 software-properties-gtk all 0.96.20.5 [47.2 kB]
Get:81 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 python3-software-properties all 0.96.20.5 [19.9 kB]
Get:82 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 snapd amd64 2.17.1ubuntu1 [6,115 kB]
Get:83 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 snapd-login-service amd64 1.2-0ubuntu1.1~xenial [11.1 kB]
Get:84 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 thunderbird-locale-en amd64 1:45.5.1+build1-0ubuntu0.16.04.1 [384 kB]
Get:85 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 thunderbird amd64 1:45.5.1+build1-0ubuntu0.16.04.1 [35.5 MB]
Get:86 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 thunderbird-gnome-support amd64 1:45.5.1+build1-0ubuntu0.16.04.1 [8,542 B]
Get:87 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 thunderbird-locale-en-us all 1:45.5.1+build1-0ubuntu0.16.04.1 [9,510 B]
Get:88 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 xserver-xorg-video-intel amd64 2:2.99.917+git20160325-1ubuntu1.2 [717 kB]
Get:89 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 liboxideqt-qmlplugin amd64 1.19.4-0ubuntu0.16.04.1 [168 kB]
Get:90 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 liboxideqtquick0 amd64 1.19.4-0ubuntu0.16.04.1 [271 kB]
Get:91 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 liboxideqtcore0 amd64 1.19.4-0ubuntu0.16.04.1 [32.4 MB]
Get:92 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 oxideqt-codecs-extra amd64 1.19.4-0ubuntu0.16.04.1 [902 kB]
Fetched 229 MB in 26min 50s (142 kB/s)                                         
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 476193 files and directories currently installed.)
Preparing to unpack .../libc6-dbg_2.23-0ubuntu5_amd64.deb ...
Unpacking libc6-dbg:amd64 (2.23-0ubuntu5) over (2.23-0ubuntu4) ...
Preparing to unpack .../libc6-dev_2.23-0ubuntu5_amd64.deb ...
Unpacking libc6-dev:amd64 (2.23-0ubuntu5) over (2.23-0ubuntu4) ...
Preparing to unpack .../libc-dev-bin_2.23-0ubuntu5_amd64.deb ...
Unpacking libc-dev-bin (2.23-0ubuntu5) over (2.23-0ubuntu4) ...
Preparing to unpack .../linux-libc-dev_4.4.0-53.74_amd64.deb ...
Unpacking linux-libc-dev:amd64 (4.4.0-53.74) over (4.4.0-47.68) ...
Preparing to unpack .../libc6-i386_2.23-0ubuntu5_amd64.deb ...
Unpacking libc6-i386 (2.23-0ubuntu5) over (2.23-0ubuntu4) ...
Replaced by files in installed package libc6:i386 (2.23-0ubuntu4) ...
Preparing to unpack .../libc6_2.23-0ubuntu5_i386.deb ...
De-configuring libc6:amd64 (2.23-0ubuntu4) ...
Unpacking libc6:i386 (2.23-0ubuntu5) over (2.23-0ubuntu4) ...
Preparing to unpack .../libc6_2.23-0ubuntu5_amd64.deb ...
Unpacking libc6:amd64 (2.23-0ubuntu5) over (2.23-0ubuntu4) ...
Setting up libc6:amd64 (2.23-0ubuntu5) ...
Setting up libc6:i386 (2.23-0ubuntu5) ...
Processing triggers for libc-bin (2.23-0ubuntu4) ...
Processing triggers for man-db (2.7.5-1) ...
(Reading database ... 476193 files and directories currently installed.)
Preparing to unpack .../locales_2.23-0ubuntu5_all.deb ...
Unpacking locales (2.23-0ubuntu5) over (2.23-0ubuntu4) ...
Preparing to unpack .../libc-bin_2.23-0ubuntu5_amd64.deb ...
Unpacking libc-bin (2.23-0ubuntu5) over (2.23-0ubuntu4) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libc-bin (2.23-0ubuntu5) ...
(Reading database ... 476193 files and directories currently installed.)
Preparing to unpack .../libapt-pkg5.0_1.2.15ubuntu0.2_amd64.deb ...
Unpacking libapt-pkg5.0:amd64 (1.2.15ubuntu0.2) over (1.2.15) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Setting up libapt-pkg5.0:amd64 (1.2.15ubuntu0.2) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
(Reading database ... 476193 files and directories currently installed.)
Preparing to unpack .../libapt-inst2.0_1.2.15ubuntu0.2_amd64.deb ...
Unpacking libapt-inst2.0:amd64 (1.2.15ubuntu0.2) over (1.2.15) ...
Preparing to unpack .../apt_1.2.15ubuntu0.2_amd64.deb ...
Unpacking apt (1.2.15ubuntu0.2) over (1.2.15) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up apt (1.2.15ubuntu0.2) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
(Reading database ... 476193 files and directories currently installed.)
Preparing to unpack .../apt-utils_1.2.15ubuntu0.2_amd64.deb ...
Unpacking apt-utils (1.2.15ubuntu0.2) over (1.2.15) ...
Preparing to unpack .../libmagickwand-6.q16-2_8%3a6.8.9.9-7ubuntu5.3_amd64.deb ...
Unpacking libmagickwand-6.q16-2:amd64 (8:6.8.9.9-7ubuntu5.3) over (8:6.8.9.9-7ubuntu5.2) ...
Preparing to unpack .../libmagickcore-6.q16-2_8%3a6.8.9.9-7ubuntu5.3_amd64.deb ...
Unpacking libmagickcore-6.q16-2:amd64 (8:6.8.9.9-7ubuntu5.3) over (8:6.8.9.9-7ubuntu5.2) ...
Preparing to unpack .../imagemagick-common_8%3a6.8.9.9-7ubuntu5.3_all.deb ...
Unpacking imagemagick-common (8:6.8.9.9-7ubuntu5.3) over (8:6.8.9.9-7ubuntu5.2) ...
Preparing to unpack .../ubuntu-release-upgrader-gtk_1%3a16.04.19_all.deb ...
Unpacking ubuntu-release-upgrader-gtk (1:16.04.19) over (1:16.04.18) ...
Preparing to unpack .../ubuntu-release-upgrader-core_1%3a16.04.19_all.deb ...
Unpacking ubuntu-release-upgrader-core (1:16.04.19) over (1:16.04.18) ...
Preparing to unpack .../python3-distupgrade_1%3a16.04.19_all.deb ...
Unpacking python3-distupgrade (1:16.04.19) over (1:16.04.18) ...
Preparing to unpack .../update-notifier_3.168.2_amd64.deb ...
Unpacking update-notifier (3.168.2) over (3.168.1) ...
Preparing to unpack .../update-notifier-common_3.168.2_all.deb ...
Unpacking update-notifier-common (3.168.2) over (3.168.1) ...
Preparing to unpack .../multiarch-support_2.23-0ubuntu5_amd64.deb ...
Unpacking multiarch-support (2.23-0ubuntu5) over (2.23-0ubuntu4) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.48.1-1~ubuntu16.04.1) ...
Setting up multiarch-support (2.23-0ubuntu5) ...
(Reading database ... 476193 files and directories currently installed.)
Preparing to unpack .../libprocps4_2%3a3.3.10-4ubuntu2.3_amd64.deb ...
Unpacking libprocps4:amd64 (2:3.3.10-4ubuntu2.3) over (2:3.3.10-4ubuntu2) ...
Preparing to unpack .../procps_2%3a3.3.10-4ubuntu2.3_amd64.deb ...
Unpacking procps (2:3.3.10-4ubuntu2.3) over (2:3.3.10-4ubuntu2) ...
Preparing to unpack .../tzdata_2016j-0ubuntu0.16.04_all.deb ...
Unpacking tzdata (2016j-0ubuntu0.16.04) over (2016h-0ubuntu0.16.04) ...
Preparing to unpack .../libisc-export160_1%3a9.10.3.dfsg.P4-8ubuntu1.3_amd64.deb ...
Unpacking libisc-export160 (1:9.10.3.dfsg.P4-8ubuntu1.3) over (1:9.10.3.dfsg.P4-8ubuntu1.2) ...
Preparing to unpack .../libdns-export162_1%3a9.10.3.dfsg.P4-8ubuntu1.3_amd64.deb ...
Unpacking libdns-export162 (1:9.10.3.dfsg.P4-8ubuntu1.3) over (1:9.10.3.dfsg.P4-8ubuntu1.2) ...
Preparing to unpack .../vim-tiny_2%3a7.4.1689-3ubuntu1.2_amd64.deb ...
Unpacking vim-tiny (2:7.4.1689-3ubuntu1.2) over (2:7.4.1689-3ubuntu1.1) ...
Preparing to unpack .../vim-common_2%3a7.4.1689-3ubuntu1.2_amd64.deb ...
Unpacking vim-common (2:7.4.1689-3ubuntu1.2) over (2:7.4.1689-3ubuntu1.1) ...
Preparing to unpack .../apt-transport-https_1.2.15ubuntu0.2_amd64.deb ...
Unpacking apt-transport-https (1.2.15ubuntu0.2) over (1.2.15) ...
Preparing to unpack .../dnsutils_1%3a9.10.3.dfsg.P4-8ubuntu1.3_amd64.deb ...
Unpacking dnsutils (1:9.10.3.dfsg.P4-8ubuntu1.3) over (1:9.10.3.dfsg.P4-8ubuntu1.2) ...
Preparing to unpack .../bind9-host_1%3a9.10.3.dfsg.P4-8ubuntu1.3_amd64.deb ...
Unpacking bind9-host (1:9.10.3.dfsg.P4-8ubuntu1.3) over (1:9.10.3.dfsg.P4-8ubuntu1.2) ...
Preparing to unpack .../libisc160_1%3a9.10.3.dfsg.P4-8ubuntu1.3_amd64.deb ...
Unpacking libisc160:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.3) over (1:9.10.3.dfsg.P4-8ubuntu1.2) ...
Preparing to unpack .../libdns162_1%3a9.10.3.dfsg.P4-8ubuntu1.3_amd64.deb ...
Unpacking libdns162:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.3) over (1:9.10.3.dfsg.P4-8ubuntu1.2) ...
Preparing to unpack .../libisccc140_1%3a9.10.3.dfsg.P4-8ubuntu1.3_amd64.deb ...
Unpacking libisccc140:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.3) over (1:9.10.3.dfsg.P4-8ubuntu1.2) ...
Preparing to unpack .../libisccfg140_1%3a9.10.3.dfsg.P4-8ubuntu1.3_amd64.deb ...
Unpacking libisccfg140:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.3) over (1:9.10.3.dfsg.P4-8ubuntu1.2) ...
Preparing to unpack .../liblwres141_1%3a9.10.3.dfsg.P4-8ubuntu1.3_amd64.deb ...
Unpacking liblwres141:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.3) over (1:9.10.3.dfsg.P4-8ubuntu1.2) ...
Preparing to unpack .../libbind9-140_1%3a9.10.3.dfsg.P4-8ubuntu1.3_amd64.deb ...
Unpacking libbind9-140:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.3) over (1:9.10.3.dfsg.P4-8ubuntu1.2) ...
Preparing to unpack .../python3-problem-report_2.20.1-0ubuntu2.2_all.deb ...
Unpacking python3-problem-report (2.20.1-0ubuntu2.2) over (2.20.1-0ubuntu2.1) ...
Preparing to unpack .../python3-apport_2.20.1-0ubuntu2.2_all.deb ...
Unpacking python3-apport (2.20.1-0ubuntu2.2) over (2.20.1-0ubuntu2.1) ...
Preparing to unpack .../apport_2.20.1-0ubuntu2.2_all.deb ...
Unpacking apport (2.20.1-0ubuntu2.2) over (2.20.1-0ubuntu2.1) ...
Preparing to unpack .../apport-gtk_2.20.1-0ubuntu2.2_all.deb ...
Unpacking apport-gtk (2.20.1-0ubuntu2.2) over (2.20.1-0ubuntu2.1) ...
Preparing to unpack .../firefox_50.1.0+build2-0ubuntu0.16.04.1_amd64.deb ...
Unpacking firefox (50.1.0+build2-0ubuntu0.16.04.1) over (50.0+build2-0ubuntu0.16.04.2) ...
Preparing to unpack .../firefox-locale-en_50.1.0+build2-0ubuntu0.16.04.1_amd64.deb ...
Unpacking firefox-locale-en (50.1.0+build2-0ubuntu0.16.04.1) over (50.0+build2-0ubuntu0.16.04.2) ...
Preparing to unpack .../flashplugin-installer_24.0.0.186ubuntu0.16.04.1_amd64.deb ...
Unpacking flashplugin-installer (24.0.0.186ubuntu0.16.04.1) over (11.2.202.644ubuntu0.16.04.1) ...
Preparing to unpack .../ghostscript_9.18~dfsg~0-0ubuntu2.3_amd64.deb ...
Unpacking ghostscript (9.18~dfsg~0-0ubuntu2.3) over (9.18~dfsg~0-0ubuntu2) ...
Preparing to unpack .../ghostscript-x_9.18~dfsg~0-0ubuntu2.3_amd64.deb ...
Unpacking ghostscript-x (9.18~dfsg~0-0ubuntu2.3) over (9.18~dfsg~0-0ubuntu2) ...
Preparing to unpack .../libgs9-common_9.18~dfsg~0-0ubuntu2.3_all.deb ...
Unpacking libgs9-common (9.18~dfsg~0-0ubuntu2.3) over (9.18~dfsg~0-0ubuntu2) ...
Preparing to unpack .../libgs9_9.18~dfsg~0-0ubuntu2.3_amd64.deb ...
Unpacking libgs9:amd64 (9.18~dfsg~0-0ubuntu2.3) over (9.18~dfsg~0-0ubuntu2) ...
Preparing to unpack .../ubuntu-software_3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1_amd64.deb ...
Unpacking ubuntu-software (3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1) over (3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1) ...
Preparing to unpack .../gnome-software_3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1_amd64.deb ...
Unpacking gnome-software (3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1) over (3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1) ...
Preparing to unpack .../gnome-software-common_3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1_all.deb ...
Unpacking gnome-software-common (3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1) over (3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1) ...
Selecting previously unselected package libsnapd-glib1:amd64.
Preparing to unpack .../libsnapd-glib1_1.2-0ubuntu1.1~xenial_amd64.deb ...
Unpacking libsnapd-glib1:amd64 (1.2-0ubuntu1.1~xenial) ...
Preparing to unpack .../gstreamer0.10-gconf_0.10.31-3+nmu4ubuntu2.16.04.2_amd64.deb ...
Unpacking gstreamer0.10-gconf:amd64 (0.10.31-3+nmu4ubuntu2.16.04.2) over (0.10.31-3+nmu4ubuntu2.16.04.1) ...
Preparing to unpack .../gstreamer0.10-plugins-good_0.10.31-3+nmu4ubuntu2.16.04.2_amd64.deb ...
Unpacking gstreamer0.10-plugins-good:amd64 (0.10.31-3+nmu4ubuntu2.16.04.2) over (0.10.31-3+nmu4ubuntu2.16.04.1) ...
Preparing to unpack .../gstreamer0.10-pulseaudio_0.10.31-3+nmu4ubuntu2.16.04.2_amd64.deb ...
Unpacking gstreamer0.10-pulseaudio:amd64 (0.10.31-3+nmu4ubuntu2.16.04.2) over (0.10.31-3+nmu4ubuntu2.16.04.1) ...
Preparing to unpack .../gstreamer1.0-plugins-good_1.8.2-1ubuntu0.3_amd64.deb ...
Unpacking gstreamer1.0-plugins-good:amd64 (1.8.2-1ubuntu0.3) over (1.8.2-1ubuntu0.2) ...
Preparing to unpack .../libgstreamer-plugins-good1.0-0_1.8.2-1ubuntu0.3_amd64.deb ...
Unpacking libgstreamer-plugins-good1.0-0:amd64 (1.8.2-1ubuntu0.3) over (1.8.2-1ubuntu0.2) ...
Preparing to unpack .../gstreamer1.0-pulseaudio_1.8.2-1ubuntu0.3_amd64.deb ...
Unpacking gstreamer1.0-pulseaudio:amd64 (1.8.2-1ubuntu0.3) over (1.8.2-1ubuntu0.2) ...
Preparing to unpack .../im-config_0.29-1ubuntu12.3_all.deb ...
Unpacking im-config (0.29-1ubuntu12.3) over (0.29-1ubuntu12.2) ...
Preparing to unpack .../imagemagick_8%3a6.8.9.9-7ubuntu5.3_amd64.deb ...
Unpacking imagemagick (8:6.8.9.9-7ubuntu5.3) over (8:6.8.9.9-7ubuntu5.2) ...
Preparing to unpack .../imagemagick-6.q16_8%3a6.8.9.9-7ubuntu5.3_amd64.deb ...
Unpacking imagemagick-6.q16 (8:6.8.9.9-7ubuntu5.3) over (8:6.8.9.9-7ubuntu5.2) ...
Preparing to unpack .../libgme0_0.6.0-3ubuntu0.16.04.1_amd64.deb ...
Unpacking libgme0:amd64 (0.6.0-3ubuntu0.16.04.1) over (0.6.0-3) ...
Preparing to unpack .../libmagickcore-6.q16-2-extra_8%3a6.8.9.9-7ubuntu5.3_amd64.deb ...
Unpacking libmagickcore-6.q16-2-extra:amd64 (8:6.8.9.9-7ubuntu5.3) over (8:6.8.9.9-7ubuntu5.2) ...
Selecting previously unselected package linux-image-4.4.0-53-generic.
Preparing to unpack .../linux-image-4.4.0-53-generic_4.4.0-53.74_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-53-generic (4.4.0-53.74) ...
Selecting previously unselected package linux-image-extra-4.4.0-53-generic.
Preparing to unpack .../linux-image-extra-4.4.0-53-generic_4.4.0-53.74_amd64.deb ...
Unpacking linux-image-extra-4.4.0-53-generic (4.4.0-53.74) ...
Preparing to unpack .../linux-generic_4.4.0.53.56_amd64.deb ...
Unpacking linux-generic (4.4.0.53.56) over (4.4.0.47.50) ...
Preparing to unpack .../linux-image-generic_4.4.0.53.56_amd64.deb ...
Unpacking linux-image-generic (4.4.0.53.56) over (4.4.0.47.50) ...
Selecting previously unselected package linux-signed-image-4.4.0-53-generic.
Preparing to unpack .../linux-signed-image-4.4.0-53-generic_4.4.0-53.74_amd64.deb ...
Unpacking linux-signed-image-4.4.0-53-generic (4.4.0-53.74) ...
Preparing to unpack .../linux-signed-generic_4.4.0.53.56_amd64.deb ...
Unpacking linux-signed-generic (4.4.0.53.56) over (4.4.0.47.50) ...
Preparing to unpack .../linux-signed-image-generic_4.4.0.53.56_amd64.deb ...
Unpacking linux-signed-image-generic (4.4.0.53.56) over (4.4.0.47.50) ...
Selecting previously unselected package linux-headers-4.4.0-53.
Preparing to unpack .../linux-headers-4.4.0-53_4.4.0-53.74_all.deb ...
Unpacking linux-headers-4.4.0-53 (4.4.0-53.74) ...
Selecting previously unselected package linux-headers-4.4.0-53-generic.
Preparing to unpack .../linux-headers-4.4.0-53-generic_4.4.0-53.74_amd64.deb ...
Unpacking linux-headers-4.4.0-53-generic (4.4.0-53.74) ...
Preparing to unpack .../linux-headers-generic_4.4.0.53.56_amd64.deb ...
Unpacking linux-headers-generic (4.4.0.53.56) over (4.4.0.47.50) ...
Preparing to unpack .../python-problem-report_2.20.1-0ubuntu2.2_all.deb ...
Unpacking python-problem-report (2.20.1-0ubuntu2.2) over (2.20.1-0ubuntu2.1) ...
Preparing to unpack .../python-apport_2.20.1-0ubuntu2.2_all.deb ...
Unpacking python-apport (2.20.1-0ubuntu2.2) over (2.20.1-0ubuntu2.1) ...
Preparing to unpack .../python-cryptography_1.2.3-1ubuntu0.1_amd64.deb ...
Unpacking python-cryptography (1.2.3-1ubuntu0.1) over (1.2.3-1) ...
Preparing to unpack .../python3-cryptography_1.2.3-1ubuntu0.1_amd64.deb ...
Unpacking python3-cryptography (1.2.3-1ubuntu0.1) over (1.2.3-1) ...
Preparing to unpack .../software-properties-common_0.96.20.5_all.deb ...
Unpacking software-properties-common (0.96.20.5) over (0.96.20.4) ...
Preparing to unpack .../software-properties-gtk_0.96.20.5_all.deb ...
Unpacking software-properties-gtk (0.96.20.5) over (0.96.20.4) ...
Preparing to unpack .../python3-software-properties_0.96.20.5_all.deb ...
Unpacking python3-software-properties (0.96.20.5) over (0.96.20.4) ...
Preparing to unpack .../snapd_2.17.1ubuntu1_amd64.deb ...
Warning: Stopping snapd.service, but it can still be activated by:
  snapd.socket
Unpacking snapd (2.17.1ubuntu1) over (2.16ubuntu3) ...
Selecting previously unselected package snapd-login-service.
Preparing to unpack .../snapd-login-service_1.2-0ubuntu1.1~xenial_amd64.deb ...
Unpacking snapd-login-service (1.2-0ubuntu1.1~xenial) ...
Preparing to unpack .../thunderbird-locale-en_1%3a45.5.1+build1-0ubuntu0.16.04.1_amd64.deb ...
Unpacking thunderbird-locale-en (1:45.5.1+build1-0ubuntu0.16.04.1) over (1:45.4.0+build1-0ubuntu0.16.04.1) ...
Preparing to unpack .../thunderbird_1%3a45.5.1+build1-0ubuntu0.16.04.1_amd64.deb ...
Unpacking thunderbird (1:45.5.1+build1-0ubuntu0.16.04.1) over (1:45.4.0+build1-0ubuntu0.16.04.1) ...
Preparing to unpack .../thunderbird-gnome-support_1%3a45.5.1+build1-0ubuntu0.16.04.1_amd64.deb ...
Unpacking thunderbird-gnome-support (1:45.5.1+build1-0ubuntu0.16.04.1) over (1:45.4.0+build1-0ubuntu0.16.04.1) ...
Preparing to unpack .../thunderbird-locale-en-us_1%3a45.5.1+build1-0ubuntu0.16.04.1_all.deb ...
Unpacking thunderbird-locale-en-us (1:45.5.1+build1-0ubuntu0.16.04.1) over (1:45.4.0+build1-0ubuntu0.16.04.1) ...
Preparing to unpack .../xserver-xorg-video-intel_2%3a2.99.917+git20160325-1ubuntu1.2_amd64.deb ...
Unpacking xserver-xorg-video-intel (2:2.99.917+git20160325-1ubuntu1.2) over (2:2.99.917+git20160325-1ubuntu1.1) ...
Preparing to unpack .../liboxideqt-qmlplugin_1.19.4-0ubuntu0.16.04.1_amd64.deb ...
Unpacking liboxideqt-qmlplugin:amd64 (1.19.4-0ubuntu0.16.04.1) over (1.18.3-0ubuntu0.16.04.1) ...
Preparing to unpack .../liboxideqtquick0_1.19.4-0ubuntu0.16.04.1_amd64.deb ...
Unpacking liboxideqtquick0:amd64 (1.19.4-0ubuntu0.16.04.1) over (1.18.3-0ubuntu0.16.04.1) ...
Preparing to unpack .../liboxideqtcore0_1.19.4-0ubuntu0.16.04.1_amd64.deb ...
Unpacking liboxideqtcore0:amd64 (1.19.4-0ubuntu0.16.04.1) over (1.18.3-0ubuntu0.16.04.1) ...
Preparing to unpack .../oxideqt-codecs-extra_1.19.4-0ubuntu0.16.04.1_amd64.deb ...
Unpacking oxideqt-codecs-extra:amd64 (1.19.4-0ubuntu0.16.04.1) over (1.18.3-0ubuntu0.16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for systemd (229-4ubuntu12) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Processing triggers for libglib2.0-0:amd64 (2.48.1-1~ubuntu16.04.1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for dbus (1.10.6-1ubuntu3.1) ...
Setting up libc6-dbg:amd64 (2.23-0ubuntu5) ...
Setting up libc-dev-bin (2.23-0ubuntu5) ...
Setting up linux-libc-dev:amd64 (4.4.0-53.74) ...
Setting up libc6-dev:amd64 (2.23-0ubuntu5) ...
Setting up libc6-i386 (2.23-0ubuntu5) ...
Setting up locales (2.23-0ubuntu5) ...
Generating locales (this might take a while)...
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZM.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.
Setting up libapt-inst2.0:amd64 (1.2.15ubuntu0.2) ...
Setting up apt-utils (1.2.15ubuntu0.2) ...
Setting up imagemagick-common (8:6.8.9.9-7ubuntu5.3) ...
Setting up libmagickcore-6.q16-2:amd64 (8:6.8.9.9-7ubuntu5.3) ...
Setting up libmagickwand-6.q16-2:amd64 (8:6.8.9.9-7ubuntu5.3) ...
Setting up python3-distupgrade (1:16.04.19) ...
Setting up ubuntu-release-upgrader-core (1:16.04.19) ...
Setting up ubuntu-release-upgrader-gtk (1:16.04.19) ...
Setting up update-notifier-common (3.168.2) ...
ttf-mscorefonts-installer: processing...
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Err:1 [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
  404  Not Found
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/andale32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
E: Failed to fetch [https://heanet.dl.sourceforge.net/project/corefonts/the](https://heanet.dl.sourceforge.net/project/corefonts/the) fonts/final/andale32.exe  404  Not Found

E: Download Failed
flashplugin-installer: processing...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20161213.1.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20161213.1.orig.tar.gz)
Get:1 [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20161213.1.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20161213.1.orig.tar.gz) [31.8 MB]
Fetched 31.8 MB in 4min 23s (121 kB/s)                                         
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/adobe-flashplugin_20161213.1.orig.tar.gz' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
Installing from local file /var/lib/update-notifier/package-data-downloads/partial/adobe-flashplugin_20161213.1.orig.tar.gz
Flash Plugin installed.
Setting up update-notifier (3.168.2) ...
Setting up libprocps4:amd64 (2:3.3.10-4ubuntu2.3) ...
Setting up procps (2:3.3.10-4ubuntu2.3) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up tzdata (2016j-0ubuntu0.16.04) ...

Current default time zone: 'Europe/London'
Local time is now:      Tue Dec 13 23:16:34 GMT 2016.
Universal Time is now:  Tue Dec 13 23:16:34 UTC 2016.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

Setting up libisc-export160 (1:9.10.3.dfsg.P4-8ubuntu1.3) ...
Setting up libdns-export162 (1:9.10.3.dfsg.P4-8ubuntu1.3) ...
Setting up vim-common (2:7.4.1689-3ubuntu1.2) ...
Setting up vim-tiny (2:7.4.1689-3ubuntu1.2) ...
Setting up apt-transport-https (1.2.15ubuntu0.2) ...
Setting up libisc160:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.3) ...
Setting up libdns162:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.3) ...
Setting up libisccc140:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.3) ...
Setting up libisccfg140:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.3) ...
Setting up libbind9-140:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.3) ...
Setting up liblwres141:amd64 (1:9.10.3.dfsg.P4-8ubuntu1.3) ...
Setting up bind9-host (1:9.10.3.dfsg.P4-8ubuntu1.3) ...
Setting up dnsutils (1:9.10.3.dfsg.P4-8ubuntu1.3) ...
Setting up python3-problem-report (2.20.1-0ubuntu2.2) ...
Setting up python3-apport (2.20.1-0ubuntu2.2) ...
Setting up apport (2.20.1-0ubuntu2.2) ...
Setting up apport-gtk (2.20.1-0ubuntu2.2) ...
Setting up firefox (50.1.0+build2-0ubuntu0.16.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-locale-en (50.1.0+build2-0ubuntu0.16.04.1) ...
Setting up flashplugin-installer (24.0.0.186ubuntu0.16.04.1) ...
Setting up libgs9-common (9.18~dfsg~0-0ubuntu2.3) ...
Setting up libgs9:amd64 (9.18~dfsg~0-0ubuntu2.3) ...
Setting up ghostscript (9.18~dfsg~0-0ubuntu2.3) ...
Setting up ghostscript-x (9.18~dfsg~0-0ubuntu2.3) ...
Setting up gnome-software-common (3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1) ...
Setting up libsnapd-glib1:amd64 (1.2-0ubuntu1.1~xenial) ...
Setting up gnome-software (3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1) ...
Setting up ubuntu-software (3.20.1+git20161013.0.d77d6cf-0ubuntu2~xenial1) ...
Setting up gstreamer0.10-gconf:amd64 (0.10.31-3+nmu4ubuntu2.16.04.2) ...
Setting up gstreamer0.10-plugins-good:amd64 (0.10.31-3+nmu4ubuntu2.16.04.2) ...
Setting up gstreamer0.10-pulseaudio:amd64 (0.10.31-3+nmu4ubuntu2.16.04.2) ...
Setting up libgstreamer-plugins-good1.0-0:amd64 (1.8.2-1ubuntu0.3) ...
Setting up gstreamer1.0-plugins-good:amd64 (1.8.2-1ubuntu0.3) ...
Setting up gstreamer1.0-pulseaudio:amd64 (1.8.2-1ubuntu0.3) ...
Setting up im-config (0.29-1ubuntu12.3) ...
Setting up imagemagick-6.q16 (8:6.8.9.9-7ubuntu5.3) ...
Setting up imagemagick (8:6.8.9.9-7ubuntu5.3) ...
Setting up libgme0:amd64 (0.6.0-3ubuntu0.16.04.1) ...
Setting up libmagickcore-6.q16-2-extra:amd64 (8:6.8.9.9-7ubuntu5.3) ...
Setting up linux-image-4.4.0-53-generic (4.4.0-53.74) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-extra-4.4.0-53-generic (4.4.0-53.74) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-generic (4.4.0.53.56) ...
Setting up linux-headers-4.4.0-53 (4.4.0-53.74) ...
Setting up linux-headers-4.4.0-53-generic (4.4.0-53.74) ...
Setting up linux-headers-generic (4.4.0.53.56) ...
Setting up linux-generic (4.4.0.53.56) ...
Setting up linux-signed-image-4.4.0-53-generic (4.4.0-53.74) ...
warning: file-aligned section .text extends beyond end of file
warning: checksum areas are greater than image size. Invalid section table?
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-43-generic
Found initrd image: /boot/initrd.img-4.4.0-43-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-signed-image-generic (4.4.0.53.56) ...
Setting up linux-signed-generic (4.4.0.53.56) ...
Setting up python-problem-report (2.20.1-0ubuntu2.2) ...
Setting up python-apport (2.20.1-0ubuntu2.2) ...
Setting up python-cryptography (1.2.3-1ubuntu0.1) ...
Setting up python3-cryptography (1.2.3-1ubuntu0.1) ...
Setting up python3-software-properties (0.96.20.5) ...
Setting up software-properties-common (0.96.20.5) ...
Setting up software-properties-gtk (0.96.20.5) ...
Setting up snapd (2.17.1ubuntu1) ...
Setting up snapd-login-service (1.2-0ubuntu1.1~xenial) ...
Setting up thunderbird (1:45.5.1+build1-0ubuntu0.16.04.1) ...
Setting up thunderbird-locale-en (1:45.5.1+build1-0ubuntu0.16.04.1) ...
Setting up thunderbird-gnome-support (1:45.5.1+build1-0ubuntu0.16.04.1) ...
Setting up thunderbird-locale-en-us (1:45.5.1+build1-0ubuntu0.16.04.1) ...
Setting up xserver-xorg-video-intel (2:2.99.917+git20160325-1ubuntu1.2) ...
Setting up oxideqt-codecs-extra:amd64 (1.19.4-0ubuntu0.16.04.1) ...
Setting up liboxideqtcore0:amd64 (1.19.4-0ubuntu0.16.04.1) ...
Setting up liboxideqtquick0:amd64 (1.19.4-0ubuntu0.16.04.1) ...
Setting up liboxideqt-qmlplugin:amd64 (1.19.4-0ubuntu0.16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for dbus (1.10.6-1ubuntu3.1) ...
stuart@stuart-ubuntu:~$
```

---

### Post by stuart_jones2 on 2016-12-13
It's experience that makes us who we are, and people who support us that makes us stronger.
going to restart, back in a mo

---

### Post by #&amp;thj^% on 2016-12-13
Hey Hey! Looks Good.
EDIT: I see you are going to reboot now..
Now lets keep your /Boot nice and tidy avoiding another headache down the road.
Run:
[s]```
sudo apt autoremove
```[/s]
And I would now Reboot your system...and just for good measure...after you are up and running from the reboot run this again:
 ```
sudo apt autoremove
```
Try this for a couple of days and i will post another reply (here in this thread) to clean-up what we did in "/etc/apt/save"
See that wasn't so bad was it?:lolflag:

---

### Post by stuart_jones2 on 2016-12-13
Not going to paste what the list from that code was, don't think we need page 15!! will see if  I update in the next few days and let you know.
Once again, I really appreciate your patience and time. If beans and karma are the same, you have a lot of good coming your way

---

### Post by #&amp;thj^% on 2016-12-13
When satisfied...would you mark this as "solved" as to help other looking for the same.
And also when satisfied with your results...to clean-up what we did...use the following:
tidy up with:
```
sudo rm -rf /etc/apt/save
```
It won't hurt anything if you just leave it...but I like a clean house...so it's up to you.
And Your Welcome...Enjoy!:D

---

### Post by stuart_jones2 on 2016-12-13
The last code didn't seem to do anything??
I have that work thing tomorrow, and again a trip to the wall, but will let you know of progress after that, and hope to mark this as solved, again, your support and patience has been excellent, thanks, your spirit is well and truly applauded

---

### Post by #&amp;thj^% on 2016-12-13
It did what it was supposed to do...you just would not know it at least from the terminal.
Best Regards
And A special thanks to Irihapeti and the other Staff members for adding Code Tags.
Cheers

---

### Post by vasa1 on 2016-12-13
@stuart_jones, as you can see, several of your posts have been edited by forum staff to "add code tags". We'd appreciate if you do this yourself. Here's how:

Please use **[noparse]```
[/noparse]** and **[noparse]
```[/noparse]** tags to enclose *terminal output*. The reason is that terminal output (usually) uses a fixed-witdh font so that columns are properly aligned and spaced.

[LIST]
[*]*If you start a new thread*, just select the text you've pasted and click on the **[SIZE=4]#[/SIZE]** icon above the text box _or_ first click the **#** icon and then paste the terminal output between the code tags.
[*]*If you reply to a post by clicking the large **+Reply to Thread** below the last post in a thread*, the same process applies.
[*]*If you reply to any post by clicking on "Adv Reply" or "Reply With Quote"*, the same applies.
[*]However, *if you click on "Quick Reply"*, you'll see fewer icons above the text area and the **#** icon will be missing. In that case, either type in the [noparse]```
[/noparse] and [noparse]
```[/noparse] tags yourself for each bit of terminal output or click on "Go Advanced" to give you all the editing options the forum provides including the **#** icon.
[/LIST]

---

### Post by stuart_jones2 on 2016-12-16
Hi 1fallen, just to let you know, I have had automatic updates, all seems well. A final thanks for your time and patience. 

Thanks vasa1, will note that next time I use the forum

---

### Post by #&amp;thj^% on 2016-12-16
Thanks for Marking as Solved.
Best Regards

---

