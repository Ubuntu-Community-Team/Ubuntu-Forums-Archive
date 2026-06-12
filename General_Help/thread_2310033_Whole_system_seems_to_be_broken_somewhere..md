---
title: "Whole system seems to be broken somewhere."
date: 2016-01-15
forum: General Help
---

### Post by jake93 on 2016-01-15
Everything seems to run, but I cannot update anything and constantly get "cannot change locale" notifications from the system and perl. When I try to install anything it can't install and claims there are held broken packages. to fix the locale errors i tried to install locale, which it claims is not installed, and i get this:
```
leapcow@TehServer:~$ sudo apt-get install locales
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apache2 : Depends: apache2.2-common (= 2.2.22-1ubuntu1.10) but it is not going to be installed
 apache2-mpm-event : Depends: apache2.2-common (= 2.2.22-1ubuntu1.10) but it is not going to be installed
 apache2.2-bin : Depends: libapr1 (>= 1.4.2) but it is not going to be installed
                 Depends: libaprutil1 (>= 1.3.2+dfsg) but it is not going to be installed
                 Depends: libaprutil1-dbd-sqlite3 but it is not going to be installed or
                          libaprutil1-dbd-mysql but it is not going to be installed or
                          libaprutil1-dbd-odbc but it is not going to be installed or
                          libaprutil1-dbd-pgsql but it is not going to be installed or
                          libaprutil1-dbd-freetds but it is not going to be installed
                 Depends: libaprutil1-ldap but it is not going to be installed
                 Depends: libc6 (>= 2.14) but it is not going to be installed
                 Depends: libcap2 (>= 2.10) but it is not going to be installed
                 Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
                 Depends: libpcre3 (>= 8.10) but it is not going to be installed
                 Depends: libssl1.0.0 (>= 1.0.1) but it is not going to be installed
                 Depends: zlib1g (>= 1:1.1.4) but it is not going to be installed
 locales : Depends: libc6 (>= 2.9-0ubuntu10) but it is not going to be installed or
                    libc6.1 (>= 2.9-0ubuntu10) but it is not installable
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

I've been working on trying to correct this for about 3 days now with no ground recovered. any ideas on where to start?

---

### Post by Vladlenin5000 on 2016-01-15
Hi and welcome.

Start by posting what Ubuntu version you're running. Also the full error messages (if any) of all the following commands (in order):
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by jake93 on 2016-01-15
It's ubuntu server too if that's relevant

version:
```
leapcow@TehServer:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
```

apt-update:
```
leapcow@TehServer:~$ sudo apt-get update
[sudo] password for leapcow: 
Ign http://us.archive.ubuntu.com precise InRelease
Get:1 http://us.archive.ubuntu.com precise-updates InRelease [196 kB]          
Get:2 http://security.ubuntu.com precise-security InRelease [54.5 kB]          
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://extras.ubuntu.com precise Release                          
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://us.archive.ubuntu.com precise-backports InRelease                   
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:3 http://security.ubuntu.com precise-security/main Sources [138 kB]        
Get:4 http://us.archive.ubuntu.com precise-updates/main Sources [495 kB]    
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Get:5 http://security.ubuntu.com precise-security/restricted Sources [4476 B]  
Get:6 http://us.archive.ubuntu.com precise-updates/restricted Sources [8708 B] 
Get:7 http://us.archive.ubuntu.com precise-updates/universe Sources [124 kB]   
Get:8 http://security.ubuntu.com precise-security/universe Sources [45.1 kB]   
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:9 http://us.archive.ubuntu.com precise-updates/multiverse Sources [9759 B] 
Get:10 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [967 kB]
Get:11 http://security.ubuntu.com precise-security/multiverse Sources [2201 B]
Get:12 http://security.ubuntu.com precise-security/main amd64 Packages [578 kB]
Get:13 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [16.2 kB]
Get:14 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [271 kB]
Get:15 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [16.6 kB]
Get:16 http://us.archive.ubuntu.com precise-updates/main i386 Packages [1027 kB]
Get:17 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [16.1 kB]
Get:18 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [281 kB]
Get:19 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [16.7 kB]
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Get:20 http://security.ubuntu.com precise-security/restricted amd64 Packages [11.6 kB]
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Get:21 http://security.ubuntu.com precise-security/universe amd64 Packages [128 kB]
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise Release                               
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Get:22 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2699 B]
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources     
Get:23 http://security.ubuntu.com precise-security/main i386 Packages [636 kB]
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages 
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages 
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en      
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en    
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                 
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Get:24 http://security.ubuntu.com precise-security/restricted i386 Packages [11.6 kB]
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Get:25 http://security.ubuntu.com precise-security/universe i386 Packages [136 kB]
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Get:26 http://security.ubuntu.com precise-security/multiverse i386 Packages [2875 B]
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages  
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en   
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Fetched 5197 kB in 8s (640 kB/s)                                               
Reading package lists... Done
```

apt-get upgrade:
```
leapcow@TehServer:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  openjdk-7-jdk openjdk-7-jre openjdk-7-jre-headless
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

apt-get dist-upgrade
```
leapcow@TehServer:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libsctp1 lksctp-tools
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libsctp1 lksctp-tools
The following packages have been kept back:
  openjdk-7-jdk openjdk-7-jre openjdk-7-jre-headless
0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
Need to get 56.4 kB of archives.
After this operation, 254 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main libsctp1 amd64 1.0.11+dfsg-2 [8102 B]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main lksctp-tools amd64 1.0.11+dfsg-2 [48.3 kB]
Fetched 56.4 kB in 0s (140 kB/s)      
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = (unset),
    LC_ALL = "en_US.UTF-8",
    LC_CTYPE = "en_ZA.UTF-8",
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Selecting previously unselected package libsctp1.
(Reading database ... 68210 files and directories currently installed.)
Preparing to unpack .../libsctp1_1.0.11+dfsg-2_amd64.deb ...
Unpacking libsctp1 (1.0.11+dfsg-2) ...
Selecting previously unselected package lksctp-tools.
Preparing to unpack .../lksctp-tools_1.0.11+dfsg-2_amd64.deb ...
Unpacking lksctp-tools (1.0.11+dfsg-2) ...
Processing triggers for man-db (2.6.7.1-1) ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up libsctp1 (1.0.11+dfsg-2) ...
Setting up lksctp-tools (1.0.11+dfsg-2) ...
Processing triggers for libc-bin (2.15-0ubuntu10.12) ...
ldconfig deferred processing now taking place
```

---

### Post by QDR06VV9 on 2016-01-15
I see conflicts in your lsb_release -a
It shows [B]Ubuntu 14.04.1 LTS
[/B]But your package manager is reading from [B]12.04 precise 
They do not co-habit together nicely..
[/B]Did you try to upgrade to trusty??

---

### Post by Bashing-om on 2016-01-15
jake93; et all .....

3rd party openjdk-7-jdk ? What have we in the 3rd party sources directory ?
```

tail -v -n +1 /etc/apt/sources.list.d/* 

```

[INDENT][INDENT]maybe a tale gets told
[/INDENT][/INDENT]

---

### Post by jake93 on 2016-01-15
> **runrickus said:**
> I see conflicts in your lsb_release -a
It shows [B]Ubuntu 14.04.1 LTS
[/B]But your package manager is reading from [B]12.04 precise 
They do not co-habit together nicely..
[/B]Did you try to upgrade to trusty??

Not that I know of. to the best of my knowledge i've only ever done apt-update. in fact i never even did a apt-upgrade. that was a new command to me when trying to trouble shoot this.

> **Bashing-om said:**
> jake93; et all .....

3rd party openjdk-7-jdk ? What have we in the 3rd party sources directory ?
```

tail -v -n +1 /etc/apt/sources.list.d/* 

```[INDENT][INDENT]maybe a tale gets told
[/INDENT]
[/INDENT]


```
leapcow@TehServer:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.bak <==
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
```

I wouldn't say i'm completely new to ubuntu, but this level of stuff i'm pretty foggy on. Now that you mention java there might of been a 3rd party java install i did for a minecraft server install.

---

### Post by QDR06VV9 on 2016-01-15
Try editing the [FONT=Ubuntu Mono][COLOR=#000000]/etc/apt/sources.list[/COLOR][/FONT]
[FONT=Ubuntu Mono][COLOR=#000000]And commenting out the line [/COLOR][/FONT][COLOR=#000000][FONT=Ubuntu Mono]deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main
So they both look like this
[/FONT][/COLOR]```
#[COLOR=#000000][FONT=Ubuntu Mono]deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]# deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
Then try again with 
[/FONT][/COLOR]```
sudo apt-get update
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get upgrade[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
Post back any errors

[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-01-15
jake93; Hummm ...

Nope, no tale told there .

So, what are we working with ? as 14.04's libsctp1 version is:
```

sysop@1404mini:~$ apt-cache show libsctp1
Version: 1.0.15+dfsg-1
Filename: pool/main/l/lksctp-tools/libsctp1_1.0.15+dfsg-1_amd64.deb

```
And your system wants version " Setting up libsctp1 (1.0.11+dfsg-2) " .
and :
> 
 libsctp1 (source: lksctp-tools): user-space access to Linux Kernel SCTP - shared library. In component main, is optional. Version 1.0.11+dfsg-2 [color=green](precise)[/color], package size 8 kB, installed size 64 kB

confirms you are pulling from the precise repo .

So what gives ?
Maybe best to look at what you are fetching .
```

cat -n /etc/apt/sources.list

```

[INDENT][INDENT][INDENT]which way did he go. George
[/INDENT][/INDENT][/INDENT]

---

### Post by jake93 on 2016-01-15
> **runrickus said:**
> Try editing the [FONT=Ubuntu Mono][COLOR=#000000]/etc/apt/sources.list[/COLOR][/FONT]
[FONT=Ubuntu Mono][COLOR=#000000]And commenting out the line [/COLOR][/FONT][COLOR=#000000][FONT=Ubuntu Mono]deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main
So they both look like this
[/FONT][/COLOR]```
#[COLOR=#000000][FONT=Ubuntu Mono]deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]# deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) trusty main[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
Then try again with 
[/FONT][/COLOR]```
sudo apt-get update
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get upgrade[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
Post back any errors

[/FONT][/COLOR]

i don't have trusty main at the bottom i have precise main. maybe that's part of the problem?

> **Bashing-om said:**
> jake93; Hummm ...

Nope, no tale told there .

So, what are we working with ? as 14.04's libsctp1 version is:
```

sysop@1404mini:~$ apt-cache show libsctp1
Version: 1.0.15+dfsg-1
Filename: pool/main/l/lksctp-tools/libsctp1_1.0.15+dfsg-1_amd64.deb

```
And your system wants version " Setting up libsctp1 (1.0.11+dfsg-2) " .
and :

confirms you are pulling from the precise repo .

So what gives ?
Maybe best to look at what you are fetching .
```

cat -n /etc/apt/sources.list

```[INDENT][INDENT][INDENT]which way did he go. George
[/INDENT]
[/INDENT]
[/INDENT]


```
leapcow@TehServer:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta i386 (20120421)]/ precise main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
     6    deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    11    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://us.archive.ubuntu.com/ubuntu/ precise universe
    17    deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
    18    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    19    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    27    deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    28    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    29    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    37    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu precise-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    41    deb http://security.ubuntu.com/ubuntu precise-security universe
    42    deb-src http://security.ubuntu.com/ubuntu precise-security universe
    43    deb http://security.ubuntu.com/ubuntu precise-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu precise partner
    51    # deb-src http://archive.canonical.com/ubuntu precise partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu precise main
    56    deb-src http://extras.ubuntu.com/ubuntu precise main
```

I may of screwed this one up... when i thought the list was bad i found a "default" list... might of pulled from the wrong distro.

---

### Post by Bashing-om on 2016-01-15
jake93; Ouch !

All precise (12.04) .. as the sources list .
Trying to make heads or tails out of this and back to post #1 with the system screaming about ' libc6' related packages.

What have we on the system ?
```

apt-cache policy libc6

```
which shows what is installed, and what the system has available and from where.

Also what does the system show from a different perspective of what the release is ?
what also returns:
```

cat /etc/issue

```

[INDENT][INDENT]don't know
[INDENT][INDENT][INDENT]willing to find out
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jake93 on 2016-01-15
> **Bashing-om said:**
> jake93; Ouch !

All precise (12.04) .. as the sources list .
Trying to make heads or tails out of this and back to post #1 with the system screaming about ' libc6' related packages.

What have we on the system ?
```

apt-cache policy libc6

```
which shows what is installed, and what the system has available and from where.

Also what does the system show from a different perspective of what the release is ?
what also returns:
```

cat /etc/issue

```
[INDENT][INDENT]don't know[INDENT][INDENT][INDENT]willing to find out
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


```
leapcow@TehServer:~$ apt-cache policy libc6
libc6:
  Installed: 2.21-6
  Candidate: 2.21-6
  Version table:
 *** 2.21-6 0
        100 /var/lib/dpkg/status
     2.15-0ubuntu10.12 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
     2.15-0ubuntu10.11 0
        500 http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
     2.15-0ubuntu10 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
```

```
leapcow@TehServer:~$ cat /etc/issue
Debian GNU/Linux stretch/sid \n \l
```

---

### Post by Bashing-om on 2016-01-15
jake93; Hummm ...

As the plot thickens :

What should be:
> 
You have searched for packages that names contain libc6 in suite(s) precise-updates, all sections, and all architectures.
precise-updates (libs): Embedded GNU C Library: Shared libraries 
2.15-0ubuntu10.12: amd64 i386 


what is installed on your debian system:
> 
Depends: libc6 (>= 2.14) but it is not going to be installed
-bk-
libc6:
  Installed: 2.21-6
  Candidate: 2.21-6


Which of course, begs the question; Where is this elevated version coming from ?
even release 14.04 does not have such a high version:
```

sysop@1404mini:~$ dpkg -l libc6
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  libc6:amd64    2.19-0ubuntu amd64        Embedded GNU C Library: Shared li
sysop@1404mini:~$ 

```

I going to rest on this and consider; as I am not afraid of anything - and messing about with libc6 scares me pee-waddling . We will tread lightly ---- carry a BIG stick .

Or maybe not so scared as :
```

apt-cache depends libc6

```
says it is not such a big deal after all ....

Ouch ... but but but
```

apt-cache rdepends libc6

```
 says we have reason to be deeply concerned. looks as if the whole system is dependent on libc6 !!

[INDENT][INDENT]sometimes I do wonder
[INDENT][INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jake93 on 2016-01-15
at this point it seems like nothing is changeable because it's stuck in an infinite loop of missing dependencies. I'd rather not have to start over but i'm very afraid of how screwed up the system really is.

What's most annoying is that everything runs fine, i just can't install anything new or update anything...

---

### Post by Bashing-om on 2016-01-15
jake93; Uh Huh ///

I am tacking my brain trying to come up with a safer approach .

Not secure with the thought that I have . 

[INDENT][INDENT]careful
[INDENT][INDENT][INDENT]is no accident
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jake93 on 2016-01-15
i did try completely removing libc6 and reinstalling once... honestly i saw no difference :P so that was kind of scary, but i am willing to try interesting solutions. if we break the system will i be able to still pull files from the drive?

---

### Post by ian-weisser on 2016-01-16
> **jake93 said:**
> if we break the system will i be able to still pull files from the drive?

Yes, if you have another bootable working system (like a LiveUSB) handy. The files still exist on a disk that can be mounted.
You have *already* broken your system, yet it is still bootable and trying to work as best it can.

Your libc6 should be 2.15 from your 12.04 sources.
Your installed libc6 from dpkg -l is 2.19 from 14.04.
Your installed libc6 from apt cache is 2.21 from 15.10/16.04.

Any idea where you are getting 15.10/16.04 packages from? Are you manually downloading debs and installing them? (If so, stop doing that)

I'm seeing three tough nuts here
1) Mixed-versions-on-the-same-system is not supported, the system is already broken.
2) Downgrading is not supported. Trying to downgrade packages back to a 12.04 state (four years ago!) will likely cause more breakage along the way. Risk of breaking bootability.
3) We don't know what other inappropriate package upgrades have been installed, so such downgrading will be step-by-step, touch and feel.

If you want to pursue downgrading, one place to start is by using dpkg to uninstall all the extra services you have added: SQL, Apache, Minecraft, Java, etc. They will all need to be downgraded anyway. Downgrading this way may take a few days.

The simplest solution seems a backup-and-reinstall with a fresh copy of  14.04. Backup-and-restore will be a lot less tedious and suspenseful than downgrading, most of your services will be back up in about two or three hours.

---

### Post by jake93 on 2016-01-16
ya i don't remember ever downloading and installing anything by myself except for maybe java. all updates and installs were done through apt-get.... so i have no idea how the system got this mixed up. is there a way to get everything synchronized and at least looking at the same libraries without completely re-installing? if not i guess that will have to be the next step.

---

### Post by Bashing-om on 2016-01-16
jake93; Well ...
@ian-weisser :) Your advise and input is so welcome !

Ian's advise is the more apt ... Believe me, He does KNOW.

That said, I have no heartburn in attempting to repair this install ... It is linux and with a liveDVD is always fixable; just takes time and lots of effort in your case. Maybe serious breakage to the point recovery is in a full change root environment - we can do that too .
After a night's sleep on it, and due consideration I know of no better way forward than to install the proper versions of all packages for release 12.04 . My considered opinion however, is stability is a fresh clean install of 14.04 .

It is your call, if ya want to try and salvage this install ... well that is what we do . I am all for this learning experience .

With repairing in mind .. let's see what is going to happen when we rip the heart of the OS out by removing libc6 .
```

sudo apt-get remove -s libc6

```
where the -s switch is "simulate" what the package manager will do if we tell it to .
From this we get an inkling of what we are going to have to do.
Post the output and we roll our sleeves up and go to work on this.

[INDENT][INDENT]nothing easy about this
[/INDENT][/INDENT]

---

### Post by jake93 on 2016-01-16
```
leapcow@TehServer:~$ sudo apt-get remove -s libc6
[sudo] password for leapcow: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apache2 : Depends: apache2.2-common (= 2.2.22-1ubuntu1.10) but it is not going to be installed
 apache2-mpm-event : Depends: apache2.2-common (= 2.2.22-1ubuntu1.10) but it is not going to be installed
 apache2.2-bin : Depends: libapr1 (>= 1.4.2) but it is not going to be installed
                 Depends: libaprutil1 (>= 1.3.2+dfsg) but it is not going to be installed
                 Depends: libaprutil1-dbd-sqlite3 but it is not going to be installed or
                          libaprutil1-dbd-mysql but it is not going to be installed or
                          libaprutil1-dbd-odbc but it is not going to be installed or
                          libaprutil1-dbd-pgsql but it is not going to be installed or
                          libaprutil1-dbd-freetds but it is not going to be installed
                 Depends: libaprutil1-ldap but it is not going to be installed
                 Depends: libc6 (>= 2.14) but it is not going to be installed
                 Depends: libcap2 (>= 2.10) but it is not going to be installed
                 Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
                 Depends: libpcre3 (>= 8.10) but it is not going to be installed
                 Depends: libssl1.0.0 (>= 1.0.1) but it is not going to be installed
                 Depends: zlib1g (>= 1:1.1.4) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

am i reading this correctly in that it's not even able to remove those packages?

learning a lot here either way which i'm very happy about.

---

### Post by Bashing-om on 2016-01-16
jake93; Well ...

The screaming is in regards to apache2 .. and it is the correct version for release 12.04 :
> 
You have searched for packages that names contain apache2 in suite(s) precise-updates, all sections, and all architectures.
precise-updates (web): Apache HTTP Server metapackage 
2.2.22-1ubuntu1.10: amd64 i386 
also provided by: apache2-mpm-event, apache2-mpm-itk, apache2-mpm-prefork, apache2-mpm-worker


I think the way forward here is to go ahead and remove the current libc6 and attempt to install the 12.04 version:
```

sudo apt remove libc6
sudo apt install libc6

```

What gives ? Does libc6 version 2.15 install ... if so we got to make all the other packages compatible with that version of libc6 .

[INDENT][INDENT][INDENT]fingers crossed, here goes nothing
[/INDENT][/INDENT][/INDENT]

---

### Post by jake93 on 2016-01-16
```
leapcow@TehServer:~$ sudo apt remove libc6
[sudo] password for leapcow: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apache2 : Depends: apache2.2-common (= 2.2.22-1ubuntu1.10) but it is not going to be installed
 apache2-mpm-event : Depends: apache2.2-common (= 2.2.22-1ubuntu1.10) but it is not going to be installed
 apache2.2-bin : Depends: libapr1 (>= 1.4.2) but it is not going to be installed
                 Depends: libaprutil1 (>= 1.3.2+dfsg) but it is not going to be installed
                 Depends: libaprutil1-dbd-sqlite3 but it is not going to be installed or
                          libaprutil1-dbd-mysql but it is not going to be installed or
                          libaprutil1-dbd-odbc but it is not going to be installed or
                          libaprutil1-dbd-pgsql but it is not going to be installed or
                          libaprutil1-dbd-freetds but it is not going to be installed
                 Depends: libaprutil1-ldap but it is not going to be installed
                 Depends: libc6 (>= 2.14) but it is not going to be installed
                 Depends: libcap2 (>= 2.10) but it is not going to be installed
                 Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
                 Depends: libpcre3 (>= 8.10) but it is not going to be installed
                 Depends: libssl1.0.0 (>= 1.0.1) but it is not going to be installed
                 Depends: zlib1g (>= 1:1.1.4) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
leapcow@TehServer:~$ sudo apt install libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
The following packages were automatically installed and are no longer required:
  libsctp1 lksctp-tools
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

---

### Post by Bashing-om on 2016-01-16
jake93; Ouch !

I had not even considered the possibility that we could not remove libc6 !

We got to do something to relieve the stress... looks to be apache2.

How about we remove apache2 ?
```

apt get purge --remove apache2

```
I think "purge" to remove the config files also, as it appears that presently apache2 is non-functional .

There is no doubt in my mind that libc6 has to be downgraded. whatever it may take to make that so .

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by jake93 on 2016-01-17
apache2 is actually currently functioning believe it or not.

now trying to remove:

```
leapcow@TehServer:~$ sudo apt-get purge --remove apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apache2-mpm-worker apache2-utils apache2.2-bin apache2.2-common libapr1
  libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap libsctp1 lksctp-tools
  ssl-cert
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apache2*
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
After this operation, 29.7 kB disk space will be freed.
Do you want to continue? [Y/n] y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = "en_US.UTF-8",
        LC_CTYPE = "en_ZA.UTF-8",
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 68232 files and directories currently installed.)
Removing apache2 (2.2.22-1ubuntu1.10) ...


```

---

### Post by Bashing-om on 2016-01-17
jake93; OK;

How about we re-focus our attention for a bit to :
> 
0 upgraded, 0 newly installed, 1 to remove and [color=red]3 not upgraded]/color].


See if resolving this helps in being able to remove libc6 to re-install with the 12.04 version.
```

sudo apt update
sudo apt full-upgrade

```

[INDENT][INDENT]any little bit that helps, here
[/INDENT][/INDENT]

---

### Post by jake93 on 2016-01-17
```
leapcow@TehServer:~$ sudo apt update
[sudo] password for leapcow:
Hit http://security.ubuntu.com precise-security InRelease
Ign http://us.archive.ubuntu.com precise InRelease
Hit http://us.archive.ubuntu.com precise-updates InRelease
Ign http://extras.ubuntu.com precise InRelease
Hit http://us.archive.ubuntu.com precise-backports InRelease
Hit http://security.ubuntu.com precise-security/main Sources
Hit http://us.archive.ubuntu.com precise Release.gpg
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://us.archive.ubuntu.com precise-updates/main Sources
Hit http://security.ubuntu.com precise-security/restricted Sources
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources
Hit http://security.ubuntu.com precise-security/universe Sources
Hit http://extras.ubuntu.com precise Release
Hit http://us.archive.ubuntu.com precise-updates/universe Sources
Hit http://security.ubuntu.com precise-security/multiverse Sources
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources
Hit http://security.ubuntu.com precise-security/main amd64 Packages
Hit http://extras.ubuntu.com precise/main Sources
Hit http://us.archive.ubuntu.com precise-updates/main amd64 Packages
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://extras.ubuntu.com precise/main amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://extras.ubuntu.com precise/main i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Sources
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources
Hit http://us.archive.ubuntu.com precise-backports/universe Sources
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Hit http://us.archive.ubuntu.com precise Release
Hit http://us.archive.ubuntu.com precise/main Sources
Hit http://us.archive.ubuntu.com precise/restricted Sources
Hit http://us.archive.ubuntu.com precise/universe Sources
Hit http://us.archive.ubuntu.com precise/multiverse Sources
Hit http://us.archive.ubuntu.com precise/main amd64 Packages
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise/main i386 Packages
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise/universe i386 Packages
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en
Reading package lists... Done
leapcow@TehServer:~$ sudo apt full-upgrade]
E: Invalid operation full-upgrade]
leapcow@TehServer:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  apache2-mpm-worker apache2-utils apache2.2-bin apache2.2-common libapr1
  libaprutil1 libaprutil1-dbd-sqlite3 libaprutil1-ldap libsctp1 lksctp-tools
  ssl-cert
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  openjdk-7-jdk openjdk-7-jre openjdk-7-jre-headless
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.


```

---

### Post by Bashing-om on 2016-01-17
jake93; Ouch !


As around and round we go --- been here before !
14.04:
> 
apt-cache show openjdk-7-jdk
Depends: openjdk-7-jre (= 7u91-2.6.3-0ubuntu0.14.04.1), [color=red]libc6 (>= 2.2.5)[/color]

Your libc6 install:
apt-cache policy libc6 >> Installed: 2.21-6

So what have you for 'openjdk' ?
```

apt-cache policy openjdk-7-jdk openjdk-7-jre openjdk-7-jre-headless

```
\As we consider the result of removing these, then see if we can  remove libc6 .

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by jake93 on 2016-01-19
```
leapcow@TehServer:~$ apt-cache policy openjdk-7-jdk-7-jre openjdk-7-jre-headless
openjdk-7-jre-headless:
  Installed: 7u75-2.5.4-1~trusty1
  Candidate: 7u91-2.6.3-0ubuntu0.12.04.1
  Version table:
     7u91-2.6.3-0ubuntu0.12.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/universe amd64 Packages
 *** 7u75-2.5.4-1~trusty1 0
        100 /var/lib/dpkg/status
     7~u3-2.1.1~pre1-1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
N: Unable to locate package openjdk-7-jdk-7-jre
```

---

### Post by Bashing-om on 2016-01-19
jake93; Yuk,,,

This is getting weirder alla the time .
Now we have an old version of openjdk-7-jre-headless installed .
The version we want installed is confirmed to be " 7u91-2.6.3-0ubuntu0.12.04.1 " .
By the way ... that :
```

apt-cache policy openjdk-7-jdk openjdk-7-jre openjdk-7-jre-headless

```
is 3 different packages we want the info on:
openjdk-7-jdk
openjdk-7-jre
openjdk-7-jre-headless

check for your typos.

As I think I do think we are going to remove them, and  try and install the correct versions - after we get libc6 installed properly.

[INDENT][INDENT]right, wrong, or otherwise
[INDENT][INDENT][INDENT]do something to move forward
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jake93 on 2016-01-19
do we want to remove all these then?

ignore that, was lost on my pages :P

do we want to remove the java installs?

---

### Post by Bashing-om on 2016-01-20
jake93; Well ...

A high degree of certainty that we will remove the java packages . BUT, we do need to look before we leap and see what is presently installed as opposed to what should be installed.
Java is not critical to the system, we can safely remove them, and once libc6 is proper we can then re-install the packages we have removed .
```

apt-cache policy openjdk-7-jdk openjdk-7-jre openjdk-7-jre-headless

```

All I know to do is poke at the situation 'till
[INDENT][INDENT][INDENT]something gives
[/INDENT][/INDENT][/INDENT]

---

### Post by jake93 on 2016-01-20
```
leapcow@TehServer:~$ apt-cache policy openjdk-7-jdk openjdk-7-jre openjdk-7-jre-headless
openjdk-7-jdk:
  Installed: 7u75-2.5.4-1~trusty1
  Candidate: 7u91-2.6.3-0ubuntu0.12.04.1
  Version table:
     7u91-2.6.3-0ubuntu0.12.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/universe amd64 Packages
 *** 7u75-2.5.4-1~trusty1 0
        100 /var/lib/dpkg/status
     7~u3-2.1.1~pre1-1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
openjdk-7-jre:
  Installed: 7u75-2.5.4-1~trusty1
  Candidate: 7u91-2.6.3-0ubuntu0.12.04.1
  Version table:
     7u91-2.6.3-0ubuntu0.12.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/universe amd64 Packages
 *** 7u75-2.5.4-1~trusty1 0
        100 /var/lib/dpkg/status
     7~u3-2.1.1~pre1-1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
openjdk-7-jre-headless:
  Installed: 7u75-2.5.4-1~trusty1
  Candidate: 7u91-2.6.3-0ubuntu0.12.04.1
  Version table:
     7u91-2.6.3-0ubuntu0.12.04.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/universe amd64 Packages
 *** 7u75-2.5.4-1~trusty1 0
        100 /var/lib/dpkg/status
     7~u3-2.1.1~pre1-1ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages


```

---

### Post by Bashing-om on 2016-01-20
jake93; Uh Huh .


As we have:
> 
Package openjdk-7-jdk
precise-updates (java): OpenJDK Development Kit (JDK) [universe] 
7u91-2.6.3-0ubuntu0.12.04.1: amd64 i386
Installed: 7u75-2.5.4-1~trusty1

Package openjdk-7-jre
precise-updates (java): OpenJDK Java runtime, using Hotspot JIT [universe] 
7u91-2.6.3-0ubuntu0.12.04.1: amd64 i386
Installed: 7u75-2.5.4-1~trusty1

Package openjdk-7-jre-headless
precise-updates (java): OpenJDK Java runtime, using Hotspot JIT (headless) [universe] 
7u91-2.6.3-0ubuntu0.12.04.1: amd64 i386
Installed: 7u75-2.5.4-1~trusty1


So yeah ! let's remove these old obsolete versions of java:
```

sudo apt remove openjdk-7-jdk openjdk-7-jre openjdk-7-jre-headless

```

Now what results when we attempt now to remove the obstinate libc6
```

sudo apt remove libc6

```

If it is removable, immediately (RE-)install :
```

sudo apt install libc6

```
Does the package manager scream and holler it can not comply ?
does the correct version install ?

[INDENT][INDENT]hey, It could happen
[/INDENT][/INDENT]

---

### Post by jake93 on 2016-01-25
```
  fontconfig gconf2 gdisk gvfs gvfs-common gvfs-daemons gvfs-libs
  hicolor-icon-theme java-common libapr1 libaprutil1 libaprutil1-dbd-sqlite3
  libaprutil1-ldap libasyncns0 libatasmart4 libatk-bridge2.0-0 libatk1.0-0
  libatk1.0-data libatspi2.0-0 libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-glib1 libbonobo2-0 libbonobo2-common
  libcairo-gobject2 libcairo2 libcanberra0 libcolord1 libcolorhug1 libcups2
  libdatrie1 libdconf1 libexif12 libflac8 libfontenc1 libgconf2-4 libgd3
  libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgif4 libgnome2-0 libgnome2-bin
  libgnome2-common libgnomevfs2-0 libgnomevfs2-common libgphoto2-6
  libgphoto2-l10n libgphoto2-port10 libgraphite2-3 libgtk-3-0 libgtk-3-bin
  libgtk-3-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgudev-1.0-0
  libgusb2 libharfbuzz0b libice-dev libice6 libicu52 libieee1284-3 libjasper1
  libjbig0 libjpeg-turbo8 libjpeg8 liblcms2-2 libltdl7 libpango-1.0-0
  libpangocairo-1.0-0 libpangoft2-1.0-0 libpixman-1-0 libpulse0 libsane
  libsane-common libsctp1 libsecret-1-0 libsecret-common libsm-dev libsm6
  libsndfile1 libtdb1 libthai-data libthai0 libtiff5 libudisks2-0 libv4l-0
  libv4lconvert0 libvorbisenc2 libvpx1 libwayland-client0 libwayland-cursor0
  libxaw7 libxcb-shm0 libxcomposite1 libxcursor1 libxi6 libxinerama1
  libxkbcommon0 libxmu6 libxrandr2 libxt-dev libxt6 libxtst6 libxv1
  libxxf86dga1 lksctp-tools policykit-1-gnome sound-theme-freedesktop ssl-cert
  tzdata-java udisks2 x11-common x11-utils
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ca-certificates-java default-jdk default-jre default-jre-headless
  libatk-wrapper-java libatk-wrapper-java-jni openjdk-7-jdk openjdk-7-jre
  openjdk-7-jre-headless
0 upgraded, 0 newly installed, 9 to remove and 1 not upgraded.
After this operation, 79.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = "en_US.UTF-8",
        LC_CTYPE = "en_ZA.UTF-8",
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 68228 files and directories currently installed.)
Removing default-jdk (2:1.7-51) ...
Removing openjdk-7-jdk:amd64 (7u75-2.5.4-1~trusty1) ...
Removing default-jre (2:1.7-51) ...
Removing default-jre-headless (2:1.7-51) ...
Removing ca-certificates-java (20130815ubuntu1) ...
Removing libatk-wrapper-java-jni:amd64 (0.30.4-4) ...
Removing libatk-wrapper-java (0.30.4-4) ...
Removing openjdk-7-jre:amd64 (7u75-2.5.4-1~trusty1) ...
Removing openjdk-7-jre-headless:amd64 (7u75-2.5.4-1~trusty1) ...
Processing triggers for libc-bin (2.15-0ubuntu10.12) ...
ldconfig deferred processing now taking place
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...


```

now removing libc6... taking awhile... will check back in after removal when i try to reinstall libc6

EDIT: um... so i'm seeing this now and it seems to be stuck
```
No PAM profiles have been selected.

No PAM profiles have been selected for use on this system.  This would grant all
users access without authenticating, and is not allowed.  Please select at least
one PAM profile from the available list.
```

---

### Post by Bashing-om on 2016-01-25
jake93; Uhhmmmm ...

Totally unprepared for such an event . Never ever encountered such !
so:
> 
No PAM profiles have been selected. >>

Please select at least
one PAM profile from the available list.


What "available list" is offered here > - any ?

[INDENT][INDENT]not to appear a dunce myself
[INDENT][INDENT][INDENT]but a learning cap is donned .
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2016-01-25
> **jake93 said:**
> 
```
No PAM profiles have been selected.

No PAM profiles have been selected for use on this system.  This would grant all
users access without authenticating, and is not allowed.  Please select at least
one PAM profile from the available list.
```

Fix it using the pam-auth-update command. With sudo, of course.

You should have the following profiles enabled:
- Unix authentication
- Register user sessions in the systemd control group hierarchy
- GNOME Keyring Daemon - Login keyring management
- Inheritable Capabilities Management

---

### Post by jake93 on 2016-01-25
```

No PAM profiles have been selected.

No PAM profiles have been selected for use on this system.  This would grant all
users access without authenticating, and is not allowed.  Please select at least
one PAM profile from the available list.

No PAM profiles have been selected.

No PAM profiles have been selected for use on this system.  This would grant all
users access without authenticating, and is not allowed.  Please select at least
[More] ^Z
[1]+  Stopped                 sudo apt remove libc6
leapcow@TehServer:~/MC$ sudo pam-auth-update
[sudo] password for leapcow:
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = "en_US.UTF-8",
        LC_CTYPE = "en_ZA.UTF-8",
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = "en_US.UTF-8",
        LC_CTYPE = "en_ZA.UTF-8",
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable


```

ctrl z to pause it and i can't run the update thing. safe to stop the deletion in the middle and to fix this?
 update: i tried killing the process and it doesn't seem to even try.

```
leapcow@TehServer:~/MC$ jobs -l
[1]+  2245 Stopped                 sudo apt remove libc6
leapcow@TehServer:~/MC$ sudo kill 2245
leapcow@TehServer:~/MC$ jobs -l
[1]+  2245 Stopped                 sudo apt remove libc6
leapcow@TehServer:~/MC$ sudo kill %1
kill: failed to parse argument: '%1'
leapcow@TehServer:~/MC$ sudo kill 1
leapcow@TehServer:~/MC$ jobs -l
[1]+  2245 Stopped                 sudo apt remove libc6
leapcow@TehServer:~/MC$


```

---

### Post by ian-weisser on 2016-01-25
> **jake93 said:**
> perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:

Try:
```
sudo dpkg-reconfigure locales
```

---

### Post by jake93 on 2016-01-26
```
leapcow@TehServer:~/MC$ sudo dpkg-reconfigure locales
[sudo] password for leapcow:
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = "en_US.UTF-8",
        LC_CTYPE = "en_ZA.UTF-8",
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
leapcow@TehServer:~/MC$


```

how do i stop the remove libc6 job to try and run the pam auth command

on the locales issue, last time i tried it claimed locales wasnt installed, and did the usual can't install thing when i tried to install it

---

### Post by Bashing-om on 2016-01-26
jake93; Well ..

A bit of looking and we have probable solution(s):
> 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory

See:
[http://ubuntuforums.org/showthread.php?t=1346581](http://ubuntuforums.org/showthread.php?t=1346581)
[http://askubuntu.com/questions/162391/how-do-i-fix-my-locale-issue](http://askubuntu.com/questions/162391/how-do-i-fix-my-locale-issue)

[INDENT]? 'nother step forward
[/INDENT]

---

### Post by jake93 on 2016-01-26
i've tried both of those in the past. it says that locales isn't  installed, currently i need to know how to stop the removal of libc6,  it's been stuck in the middle for a few days and kill won't get rid of  it.

---

### Post by Bashing-om on 2016-01-27
jake93; Yuk !

Now we may have a problem.

Is apt still running the removal in a terminal ? Maybe key combo ctl+c will interrupt the process ??

Else can we find the process ID ?
```

ps -e | grep apt
sudo lsof /var/lib/dpkg/lock
sudo fuser -vvv /var/lib/dpkg/lock

```
If we can interrupt the apt process, what now is the state of the package manager ?
run !
```

sudo apt update
sudo apt upgrade

```

get back to the system released, to look at the 'locales' situation.
We must get the system stable before we can mess about with the critical file libc6 - which eventually we have to replace with the correct version.

[INDENT][INDENT]a process
[INDENT][INDENT][INDENT]one thing at a time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jake93 on 2016-01-27
ctrl c doesn't work

trying to find process id

```
leapcow@TehServer:~/MC$ ps -e | grep apt
grep: command not found
leapcow@TehServer:~/MC$ sudo lsof /var/lib/dpkg/lock
[sudo] password for leapcow:
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF     NODE NAME
dpkg    2254 root    3uW  REG    8,1        0 20448179 /var/lib/dpkg/lock
leapcow@TehServer:~/MC$ sudo fuser -vvv /var/lib/dpkg/lock
                     USER        PID ACCESS COMMAND
/var/lib/dpkg/lock:  root       2254 F.... dpkg


```

---

### Post by Bashing-om on 2016-01-28
jake93; Well.

We know it is the backend 'dpkg' that is running, and we now have the process ID " 2254 " .
Let's try and end the dpkg process gracefully:
```

sudo kill -1 2254

```
else we step up our demand for a kill to a higher call ... try as -5 ... and as a last resort is that nuclear one :
```

sudo kill -9 2254

```

[INDENT][INDENT]we want our terminal, back ->
[INDENT][INDENT][INDENT]gotta have it to work with
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-02-01
jake93;  Hey ........

Long time, no hear .
Request for status OR have you taken that nuclear solution and (RE-)installed ?

[INDENT][INDENT]there is that
[/INDENT][/INDENT]

---

### Post by jake93 on 2016-02-02
sorry work has been crazy... so in the middle of that uninstall and trying to kill the process i lost power and now it won't even boot :P i'm afraid the nuclear decision is my best option now :/

---

### Post by Bashing-om on 2016-02-02
jake93; Maybe ... 

Not to be too hasty with that nuclear solution .
Got access to a liveDVD of the same installed release ?

Let's see what a file system check reveals/fixes:
on this liveDVD, terminal commands:
#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```

sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see: man e2fsck
sudo e2fsck -f -y -v /dev/sda1

```

I am often impressed and amazed at what the file system check reveals.

[INDENT][INDENT]maybe
[INDENT][INDENT]just maybe
[/INDENT][/INDENT][/INDENT][/INDENT]

---

