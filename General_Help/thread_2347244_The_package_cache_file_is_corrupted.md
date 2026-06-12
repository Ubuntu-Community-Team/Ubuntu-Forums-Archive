---
title: "The package cache file is corrupted"
date: 2016-12-22
forum: General Help
---

### Post by lar762 on 2016-12-22
When trying to get updates on Ubuntu 16.04 I receive the following error: 
```
E: Sub-process returned an error code
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_binary-all_Packages (1)
W: You may want to run apt-get update to correct these problems
E: The package cache file is corrupted
```
Can anyone give me an idea on how to correct this issue?

---

### Post by deadflowr on 2016-12-22
What was the command you ran that produced the output?

Was it from the suggested command:
> You may want to run **apt-get update** to correct these problems
or something else...

---

### Post by lar762 on 2016-12-23
That is the command ( **apt-get update) **that I ran when I got those errors.

---

### Post by Bashing-om on 2016-12-23
lar762; Hello;

I have to wonder if the control file exist.
What shows:
```

cat /etc/apt/sources.list

```

And if all that is proper ......
Then can you talk to the outside world ?
```

ping -c3 8.8.8.8
ping -c3 ubuntu.com

```

[INDENT][INDENT]we have a failure to communicate
[/INDENT][/INDENT]

---

### Post by kingneutron on 2016-12-23
--Couple of ideas:

- Is your disk running out of space? Check ' df ' - you may have to do some cleanup. I recommend Midnight Commander for this.

- Disk may need a fsck - see this link:
[https://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](https://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)

- Check your /etc/apt/sources.list , you may need to change it.  I recommend using ' synaptic ' if you have it installed to find the fastest mirror, on 14.04 I was using lug.mtu.edu in /etc/apt/sources.list and suddenly it stopped working right. Changing to mirror.lstn.net fixed the issue.

REF:
[https://www.unixmen.com/find-fastest-mirror-debian-derivatives/](https://www.unixmen.com/find-fastest-mirror-debian-derivatives/)

[http://askubuntu.com/questions/39922/how-do-you-select-the-fastest-mirror-from-the-command-line/141536#141536](http://askubuntu.com/questions/39922/how-do-you-select-the-fastest-mirror-from-the-command-line/141536#141536)

[https://linuxconfig.org/how-to-select-the-fastest-apt-mirror-on-ubuntu-linux](https://linuxconfig.org/how-to-select-the-fastest-apt-mirror-on-ubuntu-linux)

---

### Post by lar762 on 2016-12-23
Seems like plenty of disk space
```
Filesystem     1K-blocks     Used Available Use% Mounted on
udev             1008204        0   1008204   0% /dev
tmpfs             205380     6668    198712   4% /run
/dev/sda1      151649444 10863536 133059472   8% /
tmpfs            1026900      212   1026688   1% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs            1026900        0   1026900   0% /sys/fs/cgroup
cgmfs                100        0       100   0% /run/cgmanager/fs
tmpfs             205380       60    205320   1% /run/user/1000
```

---

### Post by lar762 on 2016-12-23
cat /etc/apt/sources.list
```
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140417)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
```

Being that I am new at using Ubuntu I am not sure what this result means

---

### Post by Bashing-om on 2016-12-23
lar762; Well;

That file is as we hoped it to be .. so that is not the base of the issue.

able to get out to the world ?
what do the ping results indicate ?

> 
Being that I am new at using Ubuntu I am not sure

all in the process of learning, none of us were born knowing.

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by lar762 on 2016-12-23
```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=52 time=12.8 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=52 time=13.4 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=52 time=11.1 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 11.198/12.486/13.435/0.944 ms
```
```
larry@larry-1005HA:~$ ping -c3 ubuntu.com
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=52 time=82.1 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=2 ttl=52 time=79.8 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=3 ttl=52 time=81.9 ms

--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 79.854/81.331/82.152/1.046 ms
```

---

### Post by Bashing-om on 2016-12-23
lar762l Humm ......

Not making much sense now, huh ? As you can talk to the world at large.
Show - between code tags - :
```

sudo apt update

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

See now what results.

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by lar762 on 2016-12-23
```

Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease          
Hit:4 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty InRelease
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 DEP-11 Metadata [68.2 kB]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [30.4 kB]
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe i386 DEP-11 Metadata [19.4 kB]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse i386 DEP-11 Metadata [212 B]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main Sources [212 kB]
Ign:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted Sources   
Ign:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe Sources     
Ign:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse Sources   
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [436 kB]
Ign:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en  
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 DEP-11 Metadata [303 kB]
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [184 kB]
Ign:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted i386 Packages
Ign:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted Translation-en
Ign:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted i386 DEP-11 Metadata
Get:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [367 kB]
Ign:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en
Get:24 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 DEP-11 Metadata [121 kB]
Get:25 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [145 kB]
Ign:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse i386 Packages
Get:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse Translation-en [3,080 B]
Get:28 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse i386 DEP-11 Metadata [2,516 B]
Ign:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse DEP-11 64x64 Icons
Ign:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted Sources   
Ign:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe Sources     
Ign:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse Sources   
Ign:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en  
Ign:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted i386 Packages
Ign:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted Translation-en
Ign:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted i386 DEP-11 Metadata
Ign:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en
Get:30 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main i386 DEP-11 Metadata [208 B]
Get:31 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe i386 DEP-11 Metadata [212 B]
Get:32 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/multiverse i386 DEP-11 Metadata [212 B]
Ign:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse i386 Packages
Ign:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse DEP-11 64x64 Icons
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted Sources [1,872 B]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe Sources [141 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse Sources [4,157 B]
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en [240 kB]
Get:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted i386 Packages [11.7 kB]
Get:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted Translation-en [2,044 B]
Err:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/restricted i386 DEP-11 Metadata
  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_dep11_Components-i386.yml.gz - open (13: Permission denied) [IP: 91.189.91.23 80]
Get:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en [178 kB]
Get:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse i386 Packages [6,741 B]
Ign:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse DEP-11 64x64 Icons
Fetched 1,766 kB in 10s (164 kB/s)                                             

** (appstreamcli:4144): WARNING **: No origin found for file us.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_dep11_Components-i386.yml.gz

** (appstreamcli:4144): WARNING **: No origin found for file us.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_dep11_Components-i386.yml.gz

** (appstreamcli:4144): WARNING **: No origin found for file us.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_dep11_Components-i386.yml.gz

** (appstreamcli:4144): WARNING **: No origin found for file us.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_dep11_Components-i386.yml.gz
AppStream data pool was loaded, but some metadata was ignored due to errors.
Reading package lists... Error!
W: [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/trusty/InRelease:](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/trusty/InRelease:) Signature by key 883E8688397576B6C509DF495A9A06AEF9CB8DB0 uses weak digest algorithm (SHA1)
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/restricted/dep11/Components-i386.yml](http://us.archive.ubuntu.com/ubuntu/dists/xenial-updates/restricted/dep11/Components-i386.yml)  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_dep11_Components-i386.yml.gz - open (13: Permission denied) [IP: 91.189.91.23 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamcli refresh-cache > /dev/null; fi'
E: Sub-process returned an error code
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_binary-all_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_main_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_restricted_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_universe_i18n_Translation-en (1)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_binary-i386_Packages (1)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-updates_multiverse_binary-all_Packages (1)
W: You may want to run apt-get update to correct these problems
E: The package cache file is corrupted

```

---

### Post by Bashing-om on 2016-12-24
lar762; Humm .....

Sorta stuck now, not sure what to think.
What is the base architecture we are dealing with ?
```

uname -a

```
As the errors relate to 32 bit packages.
We want to make sure of what we have and then address:
> 
The package cache file is corrupted


I tell you that the package manager does not lie and our next step just might be to rebuild the control files.

[INDENT][INDENT]there is a path that seems right
[INDENT][INDENT]but leads to a broken system
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by deadflowr on 2016-12-24
Try clearing them:
```
sudo rm -r /var/lib/apt/lists/*
sudo apt-get update
```

If that works, then see what's up with the ubuntu-wine ppa...
(But that's is of little importance as it is only a warning about weak key, see:
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1558331]("https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1558331")
as a quick reference point on that warning)

---

### Post by lar762 on 2016-12-26
uname -a
Linux larry-1005HA 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:46:51 UTC 2016 i686 i686 i686 GNU/Linux

---

### Post by lar762 on 2016-12-26
sudo rm -r /var/lib/apt/lists/*
[sudo] password for larry: 
rm: cannot remove '/var/lib/apt/lists/*': No such file or directory

Looks like there is no file or directory to remove

---

### Post by Bashing-om on 2016-12-26
lar762; Yuk !

These files have to exist in order for the package manager to function ,
Lists are a working tool of apt, part of the way it keeps track of which packages are in which repositories. It's the gears of a text-based database that apt relies upon.
Apt will recreate some of them during the next apt-get update.

Let's see what happens:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt update
sudo apt upgrade

```

[INDENT][INDENT]ready to have fun now
[/INDENT][/INDENT]

---

### Post by lar762 on 2016-12-26
After running 
sudo rm -r /var/lib/apt/lists/* and then sudo apt-get update I am no longer receiving the error regarding the package cache file is corrupted. Looks like we have corrected that issue. Appreciate your assistance with my problem.[h=2][/h]

---

### Post by Bashing-om on 2016-12-26
lar762' Well !

now running:
```

ls -al /var/lib/apt/lists/*

```
You get a wall of text ?
and 
```

sudo apt upgrade

```
completes with no errors and all is 0's ?
> 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Then :
[INDENT][INDENT]we done good work
[/INDENT][/INDENT]

---

### Post by lar762 on 2016-12-26
Thanks for your assistance on this issue!

---

### Post by Bashing-om on 2016-12-26
lar762; Hey ....

Glad to be of assistance.

If this matter is now concluded
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

