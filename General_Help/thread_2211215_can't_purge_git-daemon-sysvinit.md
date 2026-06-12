---
title: "can't purge git-daemon-sysvinit"
date: 2014-03-14
forum: General Help
---

### Post by michael122 on 2014-03-14
I am trying to remove git daemon but i can't because of a Sub-process /usr/bin/dpkg returned an error code (1) error

the broken uninstall
```

sudo apt-get purge -f  git-daemon-sysvinit 
[sudo] password for mongodb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  git-daemon-sysvinit
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 501 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 199814 files and directories currently installed.)
Removing git-daemon-sysvinit ...
update-rc.d: /etc/init.d/git-daemon exists during rc.d purge (use -f to force)
dpkg: error processing git-daemon-sysvinit (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Processing triggers for ureadahead ...
Errors were encountered while processing:
 git-daemon-sysvinit
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

lsb_release -a
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise
```

uname -a
```
Linux MongoDB 3.8.0-37-generic #53~precise1-Ubuntu SMP Wed Feb 19 21:39:14 UTC 2014 i686 i686 i386 GNU/Linux

```

sudo dpkg -C
```
The following packages are only half installed, due to problems duringinstallation.  The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 git-daemon-sysvinit  fast, scalable, distributed revision control system (git-

```

sudo dpkg -l git-daemon-sysvinit
```
Desired=Unknown/Install/Remove/Purge/Hold| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                                  Version                                               Description
+++-=====================================================-=====================================================-==========================================================================================================================
pH  git-daemon-sysvinit                                   1:1.7.9.5-1                                           fast, scalable, distributed revision control system (git-daemon service)

```

apt-cache policy git-daemon-sysvinit 
```
git-daemon-sysvinit:  Installed: 1:1.7.9.5-1
  Candidate: 1:1.7.9.5-1
  Version table:
 *** 1:1.7.9.5-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/universe i386 Packages
        100 /var/lib/dpkg/status

```

cat -n /etc/apt/sources.list
```
     1    #      2    
     3    # deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.2)]/ precise main restricted
     4    
     5    #deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.2)]/ precise main restricted
     6    
     7    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     8    # newer versions of the distribution.
     9    deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
    10    deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
    11    
    12    ## Major bug fix updates produced after the final release of the
    13    ## distribution.
    14    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    15    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    16    
    17    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    18    ## team. Also, please note that software in universe WILL NOT receive any
    19    ## review or updates from the Ubuntu security team.
    20    deb http://us.archive.ubuntu.com/ubuntu/ precise universe
    21    deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
    22    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    23    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    24    
    25    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    26    ## team, and may not be under a free licence. Please satisfy yourself as to 
    27    ## your rights to use the software. Also, please note that software in 
    28    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    29    ## security team.
    30    deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    31    deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    32    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    33    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    34    
    35    ## N.B. software from this repository may not have been tested as
    36    ## extensively as that contained in the main release, although it includes
    37    ## newer versions of some applications which may provide useful features.
    38    ## Also, please note that software in backports WILL NOT receive any review
    39    ## or updates from the Ubuntu security team.
    40    deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    41    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    42    
    43    deb http://security.ubuntu.com/ubuntu precise-security main restricted
    44    deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    45    deb http://security.ubuntu.com/ubuntu precise-security universe
    46    deb-src http://security.ubuntu.com/ubuntu precise-security universe
    47    deb http://security.ubuntu.com/ubuntu precise-security multiverse
    48    deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    49    
    50    ## Uncomment the following two lines to add software from Canonical's
    51    ## 'partner' repository.
    52    ## This software is not part of Ubuntu, but is offered by Canonical and the
    53    ## respective vendors as a service to Ubuntu users.
    54    # deb http://archive.canonical.com/ubuntu precise partner
    55    # deb-src http://archive.canonical.com/ubuntu precise partner
    56    
    57    ## Uncomment the following two lines to add software from Ubuntu's
    58    ## 'extras' repository.
    59    ## This software is not part of Ubuntu, but is offered by third-party
    60    ## developers who want to ship their latest software.
    61    # deb http://extras.ubuntu.com/ubuntu precise main
    62    # deb-src http://extras.ubuntu.com/ubuntu precise main



```

la /etc/apt/sources.list.d/
```
mongodb.list
```

---

### Post by Bashing-om on 2014-03-17
michael122; Hello,

Boy, not much to go on is there ?
This:
> 
update-rc.d: /etc/init.d/git-daemon exists during rc.d purge


Maybe the process is running ? -> let's see what gives .
Post back the output:
```

ps aux | grep git-daemon

```
OR maybe because of this output:
> 
sysop@1310mini:~$ apt-cache show git-daemon-sysvinit
<snip>
Depends: git (>> 1:1.8.3.2), git (<< 1:1.8.3.2-.), adduser
<snip>

Let's take a look there also:
```

ps -aux | grep git

```

And this says - may be a bag of worms:
> 
git-daemon-sysvinit
  Depends: git
    git:i386
  Depends: git
    git:i386
###more food for thought##
 Depends: adduser
  [color=red]Conflicts: git-daemon-run[/color]
  Conflicts: <git-daemon-run:i386>
    git-daemon-run
sysop@1310mini:~$ apt-cache rdepends git-daemon-sysvinit
git-daemon-sysvinit
Reverse Depends:
  [color=red]git-daemon-run[/color]
  git-all
  git
sysop@1310mini:~$



But, no crossing bridges 'till we get to them. For now we just want to now if git (or some part of it ) is running.


We got to start poking and prodding somewhere, this looks about as 
[INDENT][INDENT]good as any
[/INDENT][/INDENT]

---

### Post by michael122 on 2014-03-17
ps aux | grep git-daemon
```
mongodb   3735  0.0  0.0   4384   808 pts/2    S+   19:28   0:00 grep --color=auto git-daemon

```

ps -aux | grep git
```
mongodb   3735  0.0  0.0   4384   808 pts/2    S+   19:28   0:00 grep --color=auto git-daemon
```

---

### Post by Bashing-om on 2014-03-17
michael122; welp
Now this : ps -aux | grep git -> --color=auto git-daemon ; does not compute (recon ya copied the "ps aux | grep git-daemon" output instead ).

Let's "assume !" that git is not running, and cover the basic bases; do:
```

sudo apt-get update
sudo apt-get upgrade

```
And let's see what the package manager advises when we try and remove "git-daemon-sysvinit".
```

sudo apt-get remove git-daemon-sysvinit

```

just a poke. we hope
[INDENT][INDENT]in the right direction
[/INDENT][/INDENT]

---

### Post by michael122 on 2014-03-18
could that grep --color=auto be because i have an alias for it?
from my .bashrc
```

    alias grep='grep --color=auto'    
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'

```

apt-get update
```
mongodb@MongoDB:~$ sudo apt-get update[sudo] password for mongodb:
Hit http://downloads-distro.mongodb.org dist Release.gpg
Hit http://us.archive.ubuntu.com precise Release.gpg
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://us.archive.ubuntu.com precise-backports Release.gpg
Hit http://us.archive.ubuntu.com precise Release
Get:2 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]
Hit http://downloads-distro.mongodb.org dist Release
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://us.archive.ubuntu.com precise-backports Release
Hit http://downloads-distro.mongodb.org dist/10gen i386 Packages
Get:4 http://security.ubuntu.com precise-security Release [49.6 kB]
Hit http://us.archive.ubuntu.com precise/main Sources
Hit http://us.archive.ubuntu.com precise/restricted Sources
Hit http://us.archive.ubuntu.com precise/universe Sources
Hit http://us.archive.ubuntu.com precise/multiverse Sources
Hit http://us.archive.ubuntu.com precise/main i386 Packages
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise/universe i386 Packages
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex
Ign http://downloads-distro.mongodb.org dist/10gen TranslationIndex
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Get:5 http://us.archive.ubuntu.com precise-updates/main Sources [453 kB]
Get:6 http://security.ubuntu.com precise-security/main Sources [100 kB]
Get:7 http://us.archive.ubuntu.com precise-updates/restricted Sources [8,028 B]
Get:8 http://us.archive.ubuntu.com precise-updates/universe Sources [105 kB]
Get:9 http://us.archive.ubuntu.com precise-updates/multiverse Sources [8,900 B]
Get:10 http://us.archive.ubuntu.com precise-updates/main i386 Packages [783 kB]
Get:11 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [12.2 kB]
Get:12 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [242 kB]
Get:13 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:14 http://security.ubuntu.com precise-security/universe Sources [30.9 kB]
Get:15 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Get:16 http://security.ubuntu.com precise-security/multiverse Sources [1,789 B]
Get:17 http://security.ubuntu.com precise-security/main i386 Packages [399 kB]
Hit http://us.archive.ubuntu.com precise-backports/main Sources
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources
Hit http://us.archive.ubuntu.com precise-backports/universe Sources
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Ign http://downloads-distro.mongodb.org dist/10gen Translation-en_US
Ign http://downloads-distro.mongodb.org dist/10gen Translation-en
Get:18 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:19 http://security.ubuntu.com precise-security/universe i386 Packages [96.1 kB]
Get:20 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,646 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 2,365 kB in 3s (707 kB/s)
Reading package lists... Done



```

apt-get upgrade
```
mongodb@MongoDB:~$ sudo apt-get upgradeReading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  git-daemon-sysvinit
The following packages will be upgraded:
  tzdata update-manager-core
2 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 181 kB/630 kB of archives.
After this operation, 548 kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main update-manager-core i386 1:0.156.14.12 [181 kB]
Fetched 181 kB in 0s (332 kB/s)
Preconfiguring packages ...
(Reading database ... 199814 files and directories currently installed.)
Removing git-daemon-sysvinit ...
update-rc.d: /etc/init.d/git-daemon exists during rc.d purge (use -f to force)
dpkg: error processing git-daemon-sysvinit (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Processing triggers for ureadahead ...
Errors were encountered while processing:
 git-daemon-sysvinit
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

apt-get remove git-daemon-sysvinit
```
mongodb@MongoDB:~$ sudo apt-get remove git-daemon-sysvinitReading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  git-daemon-sysvinit
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 501 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 199814 files and directories currently installed.)
Removing git-daemon-sysvinit ...
update-rc.d: /etc/init.d/git-daemon exists during rc.d purge (use -f to force)
dpkg: error processing git-daemon-sysvinit (--remove):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
 git-daemon-sysvinit
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by Bashing-om on 2014-03-18
michael122. Umph !

Still no info to proceed on. I am not one to fumble around in the dark, so .
Let's try and (re-)install "git-daemon-sysvinit" : - maybe get some more info -
```

sudo apt-get install --reinstall git-daemon-sysvinit

```
*IF* that runs, let's next take care of this:
> 
0 upgraded, 0 newly installed, 1 to remove and [color=red]2 not upgraded[/color].

By running terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

``` where "dist-upgrade" uses apt-get's smart mode to resolve the held packages.

And Now try and remove "git-daemon-sysvinit" :
```

sudo apt-get purge git-daemon-sysvinit

```
Hey maybe yes.
[INDENT][INDENT]more likely, not so yes
[/INDENT][/INDENT]

---

### Post by michael122 on 2014-03-18
sudo apt-get install --reinstall git-daemon-sysvint 
```
mongodb@MongoDB:~$ sudo apt-get install --reinstall git-daemon-sysvinit[sudo] password for mongodb:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 8,788 B of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/universe git-daemon-sysvinit all 1:1.7.9.5-1 [8,788 B]
Fetched 8,788 B in 0s (36.3 kB/s)
Selecting previously unselected package git-daemon-sysvinit.
(Reading database ... 199814 files and directories currently installed.)
Preparing to replace git-daemon-sysvinit 1:1.7.9.5-1 (using .../git-daemon-sysvinit_1%3a1.7.9.5-1_all.deb) ...
Unpacking replacement git-daemon-sysvinit ...
Processing triggers for ureadahead ...
Setting up git-daemon-sysvinit (1:1.7.9.5-1) ...



```

sudo apt-get upgrade && sudo apt-get dist-upgrade
```
mongodb@MongoDB:~$ sudo apt-get upgradeReading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  tzdata update-manager-core
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/630 kB of archives.
After this operation, 47.1 kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 199820 files and directories currently installed.)
Preparing to replace tzdata 2013g-0ubuntu0.12.04 (using .../tzdata_2014a-0ubuntu0.12.04_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2014a-0ubuntu0.12.04) ...


Current default time zone: 'America/Los_Angeles'
Local time is now:      Tue Mar 18 10:53:58 PDT 2014.
Universal Time is now:  Tue Mar 18 17:53:58 UTC 2014.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


(Reading database ... 199799 files and directories currently installed.)
Preparing to replace update-manager-core 1:0.156.14.11 (using .../update-manager-core_1%3a0.156.14.12_i386.deb) ...
Unpacking replacement update-manager-core ...
Processing triggers for man-db ...
Setting up update-manager-core (1:0.156.14.12) ...
mongodb@MongoDB:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



```

but still unable to remove git-daemon
```
mongodb@MongoDB:~$ sudo apt-get purge git-daemon-sysvinitReading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  git-daemon-sysvinit*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 501 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 199799 files and directories currently installed.)
Removing git-daemon-sysvinit ...
update-rc.d: /etc/init.d/git-daemon exists during rc.d purge (use -f to force)
dpkg: error processing git-daemon-sysvinit (--purge):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
 git-daemon-sysvinit
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Bashing-om on 2014-03-18
michael122; Humm,

Getting nowhere, faster.

Let's poke and see if we can get an idea of what is going on.
what returns from:
```

ls -la ~/.gitconfig

```

Be aware, In my look'n about, there are several bug reports in launchpad in this respect, none with solutions provided !

Let's look:
```

apt-cache depends git-daemon-sysvinit
apt-cache rdepends git-daemon-sysvinit
apt-cache depends git-daemon
apt-cache rdepends git-daemon
apt-cache policy git

```

This my friend is going to be
[INDENT][INDENT]a learning experience
[/INDENT][/INDENT]

---

### Post by michael122 on 2014-03-18
ls -la ~/.gitconfig
```

-rw-rw-r-- 1 mongodb mongodb 69 Mar 13 13:04 /home/mongodb/.gitconfig

```

```


apt-cache depends git-daemon-sysvinit 
[code]
git-daemon-sysvinit
  Depends: git
  Depends: git
  Depends: adduser
  Conflicts: git-daemon-run

```
apt-cache rdepends git-daemon-sysvinit 
```

git-daemon-sysvinit
Reverse Depends:
  git-daemon-run
  git-all
  git

```

apt-cache depends git-daemon
```

E: No packages found

```

apt-cache rdepends git-daemon
```

E: No packages found

```

apt-cache policy git
```

git:
  Installed: 1:1.7.9.5-1
  Candidate: 1:1.7.9.5-1
  Version table:
 *** 1:1.7.9.5-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Bashing-om on 2014-03-18
michael122; surprising ??

What have we here, that "git-daemon-sysvinit " has depends on and reverse depends on the package "git" ??
I do not understand all I do not know. I Will reboot into my 12.04 install later and do some checking .
I do have a glimmer of a thought of how to proceed.

Is this a definition of
[INDENT][INDENT]something else
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-03-18
michael122; 

A little bit wiser. Let's approach this from a different direction, and work from the bottom back up.

Post back :
```

dpkg -l git
apt-cache policy git
ps aux | grep git

```

Will see where this train of thought de-rails at.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by michael122 on 2014-03-19
also as of now this is now an active git server so if you can can you tell me if any commands would affect that. since i'm still a rookie at linux thanks :)

dpkg -l git
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                              Version                           Description
+++-=================================-=================================-==================================================================================
ii  git                               1:1.7.9.5-1                       fast, scalable, distributed revision control system

```

apt-cache policy git
```

git:
  Installed: 1:1.7.9.5-1
  Candidate: 1:1.7.9.5-1
  Version table:
 *** 1:1.7.9.5-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status

```


ps aux | grep git
```

mongodb  19722  0.0  0.0   4384   808 pts/2    S+   00:07   0:00 grep --color=auto git

```

---

### Post by Bashing-om on 2014-03-19
michael122; Hey ;

Regret the delay in getting back to you, my booting problem has popped up again (ATA errors !)

In light of this:
> 
also as of now this is now an active git server


Why then do you want/need to remove "git-daemon-sysvinit " ???????
As "git" is a component of that package though not a dependent, just a "recommendation".
[http://packages.ubuntu.com/precise/git-daemon-sysvinit](http://packages.ubuntu.com/precise/git-daemon-sysvinit)

Maybe things best - left alone - as I presently see no way to remove "git-daemon-sysvinit" without 1st removing "git".
That said, perhaps others with experience with the git-server can advise better.

[INDENT]Time and a place for all things
[INDENT][INDENT]This is not a time for an error
[/INDENT][/INDENT][/INDENT]

---

### Post by michael122 on 2014-03-19
the intended goal was to be able to clone without need of ssh keys. which the git-daemon should of allowed. the cloning was not working and i was going to remove it and try git-daemon-run. it really isn't critical but it would be convenient for admins

---

### Post by Bashing-om on 2014-03-20
michael122; Morning !

Able to boot myself and that is a good thing !

As to "git-daemon-run" that also is a component of "git". That application should run with no conflicts (??).
I do not have it installed, and am not familiar with it; thus I can not test.

There are those times I wonder
[INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT]

---

### Post by michael122 on 2014-03-20
git-daemon-sysvinit slashes with git-daemon-run which is my main problem lol

---

