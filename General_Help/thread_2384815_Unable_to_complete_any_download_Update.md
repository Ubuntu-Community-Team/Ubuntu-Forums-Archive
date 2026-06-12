---
title: "Unable to complete any download/ Update"
date: 2018-02-12
forum: General Help
---

### Post by mindbj on 2018-02-12
Hello, I have just installed Ubuntu 17.10 on my PC only to be faced with an issue that my google skills seems unable to get rid of:
I have internet access as I am writing you on the forum from this PC, but I am unable to download any program from "ubuntu software", or to complete updates without an error.

When running  apt-get update I get this following error: "Some index files failed to download. They have been ignored, or old ones used instead."
When installing 3rd party software trough "ubuntu software" the install button turns to "launch" but nothing happens on launch.
When trying to use "software updater" I get the error "Failed to download repository information, check your internet connection"


Steps I have tried to solve the issue:
-Reboot PC,
 -Changed managed=false to managed=true in NetworkManager.conf,
 -Made sure only two lines
auto lo
iface lo inet loopback
are written in /etc/network/interfaces
Changed "downloaded from" canada to "main server" in software and update settings 
-Re-installed ubuntu fresh

Thank you in advance for any help or directions !

---

### Post by deadflowr on 2018-02-12
Open the program called Terminal and post back the results of
```
sudo apt update
```
It'll ask for a password and the password field will seem empty, but it's only invisible. so no worries about that.

---

### Post by #&amp;thj^% on 2018-02-12
> **mindbj said:**
> Hello, I have just installed Ubuntu 17.10 on my PC only to be faced with an issue that my google skills seems unable to get rid of:
I have internet access as I am writing you on the forum from this PC, but I am unable to download any program from "ubuntu software", or to complete updates without an error.

When running  apt-get update I get this following error: "Some index files failed to download. They have been ignored, or old ones used instead."
When installing 3rd party software trough "ubuntu software" the install button turns to "launch" but nothing happens on launch.
When trying to use "software updater" I get the error "Failed to download repository information, check your internet connection"


Steps I have tried to solve the issue:
-Reboot PC,
 -Changed managed=false to managed=true in NetworkManager.conf,
 -Made sure only two lines
auto lo
iface lo inet loopback
are written in /etc/network/interfaces
Changed "downloaded from" canada to "main server" in software and update settings 
-Re-installed ubuntu fresh

Thank you in advance for any help or directions !
First open a terminal and use:
```
sudo apt update
```
Post back all the details listed, using Code Tags: [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)
ninj'ed by deadflowr :)

---

### Post by mindbj on 2018-02-12
Thanks for the quick answer, here is the response I get:
```

mind@mind-desktop:~$ sudo apt update
[sudo] password for mind: 
Hit:2 http://archive.ubuntu.com/ubuntu artful-updates InRelease
Hit:3 http://archive.ubuntu.com/ubuntu artful-backports InRelease
Hit:4 http://archive.ubuntu.com/ubuntu artful-security InRelease
Get:1 http://archive.ubuntu.com/ubuntu artful InRelease [237 kB]
Get:5 http://archive.ubuntu.com/ubuntu artful/restricted Sources [5,392 B]
Get:6 http://archive.ubuntu.com/ubuntu artful/main Sources [849 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Err:7 http://archive.ubuntu.com/ubuntu artful/universe Sources                 
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:8721128 [weak]
   - SHA256:6298549ab4877178bf0941a95889cb00534f556c0dcfa09975531091fca1daef
   - SHA1:6a136584e281a9aa92c3d63fd92f55ee2cd2d57d [weak]
   - MD5Sum:c639236f263143ba819f780d03aebec4 [weak]
  Hashes of received file:
   - SHA256:5a238a098fa2b8510b1842f3135464be45261ee382e6602e1f9317cc42532b91
   - SHA1:5803978562c19db2f3879bc46c99c7cbd469e2c0 [weak]
   - MD5Sum:e29fe30caa9e509e0d9062e00c3b0c5e [weak]
   - Filesize:8721128 [weak]
  Last modification reported: Thu, 19 Oct 2017 09:51:41 +0000
  Release file created at: Thu, 19 Oct 2017 12:55:45 +0000
Get:26 http://archive.ubuntu.com/ubuntu artful/universe i386 Packages [8,066 kB]
Err:26 http://archive.ubuntu.com/ubuntu artful/universe i386 Packages          
  
Get:27 http://archive.ubuntu.com/ubuntu artful/universe amd64 DEP-11 Metadata [2,845 kB]
Err:27 http://archive.ubuntu.com/ubuntu artful/universe amd64 DEP-11 Metadata  
  
Get:28 http://archive.ubuntu.com/ubuntu artful/universe DEP-11 64x64 Icons [7,915 kB]
Err:28 http://archive.ubuntu.com/ubuntu artful/universe DEP-11 64x64 Icons     
  
Fetched 27.8 MB in 24s (1,123 kB/s)                                            
Reading package lists... Done
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/artful/universe/source/by-hash/SHA256/6298549ab4877178bf0941a95889cb00534f556c0dcfa09975531091fca1daef  Hash Sum mismatch
   Hashes of expected file:
    - Filesize:8721128 [weak]
    - SHA256:6298549ab4877178bf0941a95889cb00534f556c0dcfa09975531091fca1daef
    - SHA1:6a136584e281a9aa92c3d63fd92f55ee2cd2d57d [weak]
    - MD5Sum:c639236f263143ba819f780d03aebec4 [weak]
   Hashes of received file:
    - SHA256:5a238a098fa2b8510b1842f3135464be45261ee382e6602e1f9317cc42532b91
    - SHA1:5803978562c19db2f3879bc46c99c7cbd469e2c0 [weak]
    - MD5Sum:e29fe30caa9e509e0d9062e00c3b0c5e [weak]
    - Filesize:8721128 [weak]
   Last modification reported: Thu, 19 Oct 2017 09:51:41 +0000
   Release file created at: Thu, 19 Oct 2017 12:55:45 +0000
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/artful/universe/binary-i386/by-hash/SHA256/4fd48c457f32ebc2dba552e137605194760f9166e6f87562afae03c4059716ec  
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/artful/universe/dep11/by-hash/SHA256/22152e8604d3fc1c0eecd939a3fa78c60cef396f1dc10855f3ed6a036d06b722  
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/artful/universe/dep11/by-hash/SHA256/87517ea9340abe20e43a652dd9e0668bff31dcd20260caf9f17870ed178dba88  
E: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by deadflowr on 2018-02-12
Interesting, so what does your sources.list information tell us
```
cat /etc/apt/sources.list
```
Again, please post back the results.

---

### Post by mindbj on 2018-02-12
```

mind@mind-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 17.10 _Artful Aardvark_ - Release amd64 (20180105.1)]/ artful main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu artful main restricted
deb-src http://archive.ubuntu.com/ubuntu artful main multiverse restricted universe #Added by software-properties
# deb-src http://ca.archive.ubuntu.com/ubuntu/ artful main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu artful-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu artful-updates main multiverse restricted universe #Added by software-properties
# deb-src http://ca.archive.ubuntu.com/ubuntu/ artful-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu artful universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ artful universe
deb http://archive.ubuntu.com/ubuntu artful-updates universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ artful-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu artful multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ artful multiverse
deb http://archive.ubuntu.com/ubuntu artful-updates multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ artful-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu artful-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu artful-backports main restricted universe multiverse #Added by software-properties
# deb-src http://ca.archive.ubuntu.com/ubuntu/ artful-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu artful partner
# deb-src http://archive.canonical.com/ubuntu artful partner

deb http://archive.ubuntu.com/ubuntu artful-security main restricted
deb-src http://archive.ubuntu.com/ubuntu artful-security main multiverse restricted universe #Added by software-properties
# deb-src http://security.ubuntu.com/ubuntu artful-security main restricted
deb http://archive.ubuntu.com/ubuntu artful-security universe
# deb-src http://security.ubuntu.com/ubuntu artful-security universe
deb http://archive.ubuntu.com/ubuntu artful-security multiverse
# deb-src http://security.ubuntu.com/ubuntu artful-security multiverse


```

---

### Post by #&amp;thj^% on 2018-02-12
Are you behind a proxy?

---

### Post by mindbj on 2018-02-12
no proxy, I am connected via ethernet wire to a home modem/router combo with no additional settings required for my connection.

---

### Post by #&amp;thj^% on 2018-02-12
I have seen the same as you are experiencing now with another user here in UF, but there was no solution posted.
About the only thing I would suggest then: run commands given below in the terminal one line at a time:

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt clean
sudo apt update
```
Fingers and Toes Crossed.;)

---

### Post by mindbj on 2018-02-12
Seems like the same error appears (i'm not quite sure as the text is similar but I don't understand it)

```

mind@mind-desktop:~$ sudo rm -rf /var/lib/apt/lists/*
[sudo] password for mind: 
mind@mind-desktop:~$ sudo apt clean
mind@mind-desktop:~$ sudo apt update
Get:1 http://archive.ubuntu.com/ubuntu artful InRelease [237 kB]
Get:2 http://archive.ubuntu.com/ubuntu artful-updates InRelease [78.6 kB]
Get:3 http://archive.ubuntu.com/ubuntu artful-backports InRelease [72.2 kB]
Get:4 http://archive.ubuntu.com/ubuntu artful-security InRelease [78.6 kB]
Get:5 http://archive.ubuntu.com/ubuntu artful/universe Sources [8,721 kB]
Err:5 http://archive.ubuntu.com/ubuntu artful/universe Sources                 
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:8721128 [weak]
   - SHA256:6298549ab4877178bf0941a95889cb00534f556c0dcfa09975531091fca1daef
   - SHA1:6a136584e281a9aa92c3d63fd92f55ee2cd2d57d [weak]
   - MD5Sum:c639236f263143ba819f780d03aebec4 [weak]
  Hashes of received file:
   - SHA256:fd2f93d3e7eac5434081c9bd190453c3f57e7e0077c0e871e2016dadd7a1fcff
   - SHA1:2d8b418922ed78c9292d2363552952c196ab66bc [weak]
   - MD5Sum:76cdab5e1252e8b433a06ad315c1093c [weak]
   - Filesize:8721128 [weak]
  Last modification reported: Thu, 19 Oct 2017 09:51:41 +0000
  Release file created at: Thu, 19 Oct 2017 12:55:45 +0000
Get:6 http://archive.ubuntu.com/ubuntu artful/multiverse Sources [182 kB]      
Get:7 http://archive.ubuntu.com/ubuntu artful/restricted Sources [5,392 B]     
Get:8 http://archive.ubuntu.com/ubuntu artful/main Sources [849 kB]            
Get:9 http://archive.ubuntu.com/ubuntu artful/main i386 Packages [1,067 kB]    
Get:10 http://archive.ubuntu.com/ubuntu artful/main amd64 Packages [1,071 kB]  
Get:11 http://archive.ubuntu.com/ubuntu artful/main Translation-en [542 kB]    
Get:12 http://archive.ubuntu.com/ubuntu artful/main Translation-en_CA [5,448 B]
Get:13 http://archive.ubuntu.com/ubuntu artful/main amd64 DEP-11 Metadata [397 kB]
Get:14 http://archive.ubuntu.com/ubuntu artful/main DEP-11 64x64 Icons [263 kB]
Get:15 http://archive.ubuntu.com/ubuntu artful/restricted amd64 Packages [8,852 B]
Get:16 http://archive.ubuntu.com/ubuntu artful-updates/main Sources [75.7 kB]  
Get:17 http://archive.ubuntu.com/ubuntu artful-updates/multiverse Sources [1,172 B]
Get:18 http://archive.ubuntu.com/ubuntu artful-updates/restricted Sources [960 B]
Get:19 http://archive.ubuntu.com/ubuntu artful-updates/universe Sources [22.4 kB]
Get:20 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 Packages [182 kB]
Get:21 http://archive.ubuntu.com/ubuntu artful-updates/main i386 Packages [180 kB]
Get:22 http://archive.ubuntu.com/ubuntu artful-updates/main Translation-en [82.3 kB]
Get:23 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 DEP-11 Metadata [73.2 kB]
Get:24 http://archive.ubuntu.com/ubuntu artful-updates/main DEP-11 64x64 Icons [49.2 kB]
Get:25 http://archive.ubuntu.com/ubuntu artful-updates/restricted i386 Packages [2,180 B]
Get:26 http://archive.ubuntu.com/ubuntu artful-updates/restricted amd64 Packages [2,192 B]
Get:27 http://archive.ubuntu.com/ubuntu artful-updates/restricted Translation-en [1,284 B]
Get:28 http://archive.ubuntu.com/ubuntu artful-updates/universe i386 Packages [73.1 kB]
Get:29 http://archive.ubuntu.com/ubuntu artful-updates/universe amd64 Packages [73.6 kB]
Get:30 http://archive.ubuntu.com/ubuntu artful-updates/universe Translation-en [42.0 kB]
Get:31 http://archive.ubuntu.com/ubuntu artful-updates/universe amd64 DEP-11 Metadata [49.6 kB]
Get:32 http://archive.ubuntu.com/ubuntu artful-updates/universe DEP-11 64x64 Icons [55.4 kB]
Get:33 http://archive.ubuntu.com/ubuntu artful-updates/multiverse amd64 Packages [1,828 B]
Get:34 http://archive.ubuntu.com/ubuntu artful-updates/multiverse i386 Packages [1,980 B]
Get:35 http://archive.ubuntu.com/ubuntu artful-updates/multiverse Translation-en [1,124 B]
Get:36 http://archive.ubuntu.com/ubuntu artful-backports/universe Sources [1,772 B]
Get:37 http://archive.ubuntu.com/ubuntu artful-backports/main Sources [1,192 B]
Get:38 http://archive.ubuntu.com/ubuntu artful-backports/main i386 Packages [1,512 B]
Get:39 http://archive.ubuntu.com/ubuntu artful-backports/main amd64 Packages [1,516 B]
Get:40 http://archive.ubuntu.com/ubuntu artful-backports/main Translation-en [668 B]
Get:41 http://archive.ubuntu.com/ubuntu artful-backports/universe amd64 Packages [3,408 B]
Get:42 http://archive.ubuntu.com/ubuntu artful-backports/universe i386 Packages [3,396 B]
Get:43 http://archive.ubuntu.com/ubuntu artful-backports/universe Translation-en [1,880 B]
Get:44 http://archive.ubuntu.com/ubuntu artful-backports/universe amd64 DEP-11 Metadata [4,700 B]
Get:45 http://archive.ubuntu.com/ubuntu artful-backports/universe DEP-11 64x64 Icons [2,717 B]
Get:46 http://archive.ubuntu.com/ubuntu artful-security/main Sources [32.1 kB] 
Get:47 http://archive.ubuntu.com/ubuntu artful-security/multiverse Sources [1,172 B]
Get:48 http://archive.ubuntu.com/ubuntu artful-security/universe Sources [9,764 B]
Get:49 http://archive.ubuntu.com/ubuntu artful-security/restricted Sources [960 B]
Get:50 http://archive.ubuntu.com/ubuntu artful-security/main amd64 Packages [84.4 kB]
Get:51 http://archive.ubuntu.com/ubuntu artful-security/main i386 Packages [82.7 kB]
Get:52 http://archive.ubuntu.com/ubuntu artful-security/main Translation-en [39.6 kB]
Get:53 http://archive.ubuntu.com/ubuntu artful-security/main amd64 DEP-11 Metadata [2,924 B]
Get:54 http://archive.ubuntu.com/ubuntu artful-security/main DEP-11 64x64 Icons [4,471 B]
Get:55 http://archive.ubuntu.com/ubuntu artful-security/restricted amd64 Packages [2,192 B]
Get:56 http://archive.ubuntu.com/ubuntu artful-security/restricted i386 Packages [2,180 B]
Get:57 http://archive.ubuntu.com/ubuntu artful-security/restricted Translation-en [1,284 B]
Get:58 http://archive.ubuntu.com/ubuntu artful-security/universe i386 Packages [31.3 kB]
Get:59 http://archive.ubuntu.com/ubuntu artful-security/universe amd64 Packages [31.4 kB]
Get:60 http://archive.ubuntu.com/ubuntu artful-security/universe Translation-en [19.8 kB]
Get:61 http://archive.ubuntu.com/ubuntu artful-security/universe amd64 DEP-11 Metadata [10.4 kB]
Get:62 http://archive.ubuntu.com/ubuntu artful-security/universe DEP-11 64x64 Icons [10.2 kB]
Get:63 http://archive.ubuntu.com/ubuntu artful-security/multiverse amd64 Packages [1,828 B]
Get:64 http://archive.ubuntu.com/ubuntu artful-security/multiverse i386 Packages [1,980 B]
Get:65 http://archive.ubuntu.com/ubuntu artful-security/multiverse Translation-en [1,124 B]
Fetched 14.9 MB in 15s (961 kB/s)                                              
Reading package lists... Done
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/artful/universe/source/by-hash/SHA256/6298549ab4877178bf0941a95889cb00534f556c0dcfa09975531091fca1daef  Hash Sum mismatch
   Hashes of expected file:
    - Filesize:8721128 [weak]
    - SHA256:6298549ab4877178bf0941a95889cb00534f556c0dcfa09975531091fca1daef
    - SHA1:6a136584e281a9aa92c3d63fd92f55ee2cd2d57d [weak]
    - MD5Sum:c639236f263143ba819f780d03aebec4 [weak]
   Hashes of received file:
    - SHA256:fd2f93d3e7eac5434081c9bd190453c3f57e7e0077c0e871e2016dadd7a1fcff
    - SHA1:2d8b418922ed78c9292d2363552952c196ab66bc [weak]
    - MD5Sum:76cdab5e1252e8b433a06ad315c1093c [weak]
    - Filesize:8721128 [weak]
   Last modification reported: Thu, 19 Oct 2017 09:51:41 +0000
   Release file created at: Thu, 19 Oct 2017 12:55:45 +0000
E: Some index files failed to download. They have been ignored, or old ones used instead.



```

---

### Post by #&amp;thj^% on 2018-02-12
I Love challenges, but this might be my end HA HA! :D
Lets see the out put of:
```
lsb_release -sc

```

---

### Post by deadflowr on 2018-02-12
Since the problem seems to be source packages, try turning source code off.
(It's not required unless you plan on installing from source)
You can do this in Software and Updates, just uncheck the Source Code entry.

It, of course, won't be a total fix, but it should allow you to at least run a clean update.
For now.
You might want to also re-run 1fallen's commands from post #9

---

### Post by mindbj on 2018-02-12
> **1fallen said:**
> I Love challenges, but this might be my end HA HA! :D
Lets see the out put of:
```
lsb_release -sc

```

Haha thank you so much for trying, the result gives:

 mind@mind-desktop:~$ lsb_release -sc
artful

When I unchecked "source code" in software and updates, it attempted to update as I closed the window, I still got the error: 
"Failed to download repository information

Check your Internet connection."

---

### Post by #&amp;thj^% on 2018-02-12
> **mindbj said:**
> Haha thank you so much for trying, the result gives:

 mind@mind-desktop:~$ lsb_release -sc
artful

When I unchecked "source code" in software and updates, it attempted to update as I closed the window, I still got the error: 
"Failed to download repository information

Check your Internet connection."

Lets give deadflowr's suggestion a try:
Open the terminal and run:
```
sudo gedit -H /etc/apt/sources.list
```

And put a "#" in front of these 3 entries
```
deb-src http://archive.ubuntu.com/ubuntu artful-updates main multiverse restricted universe
deb-src http://archive.ubuntu.com/ubuntu artful-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu artful-security main multiverse restricted universe
```
So they now look like:
```
# deb-src http://archive.ubuntu.com/ubuntu artful-updates main multiverse restricted universe
# deb-src http://archive.ubuntu.com/ubuntu artful-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu artful-security main multiverse restricted universe
```
And again run: one line at a time:
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt clean
sudo apt update

```

---

### Post by mindbj on 2018-02-12
Found the file to edit but none of the lines are exactly liek the 3 you asked to modify, they all have slight differences here are the contents of the file:
```

# deb cdrom:[Ubuntu 17.10 _Artful Aardvark_ - Release amd64 (20180105.1)]/ artful main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu artful main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu/ artful main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu artful-updates main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu/ artful-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu artful universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ artful universe
deb http://archive.ubuntu.com/ubuntu artful-updates universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ artful-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu artful multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ artful multiverse
deb http://archive.ubuntu.com/ubuntu artful-updates multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ artful-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu artful-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ artful-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu artful partner
# deb-src http://archive.canonical.com/ubuntu artful partner

deb http://archive.ubuntu.com/ubuntu artful-security main restricted
# deb-src http://security.ubuntu.com/ubuntu artful-security main restricted
deb http://archive.ubuntu.com/ubuntu artful-security universe
# deb-src http://security.ubuntu.com/ubuntu artful-security universe
deb http://archive.ubuntu.com/ubuntu artful-security multiverse
# deb-src http://security.ubuntu.com/ubuntu artful-security multiverse

```

---

### Post by #&amp;thj^% on 2018-02-12
Yep looks good, now run this again
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt clean
sudo apt update
```
One line at a time, and if all is good run your updates:
```
sudo apt upgrade
```

---

### Post by mindbj on 2018-02-12
But I changed nothing, this is how the file was looking. Running 
```

sudo rm -rf /var/lib/apt/lists/*
sudo apt clean
sudo apt update

```
again gave me the same result as before I think:
```

mind@mind-desktop:~$ sudo rm -rf /var/lib/apt/lists/*
[sudo] password for mind: 
mind@mind-desktop:~$ sudo apt clean
mind@mind-desktop:~$ sudo apt update
Get:1 http://archive.ubuntu.com/ubuntu artful InRelease [237 kB]
Get:2 http://archive.ubuntu.com/ubuntu artful-updates InRelease [78.6 kB]
Get:3 http://archive.ubuntu.com/ubuntu artful-backports InRelease [72.2 kB]
Get:4 http://archive.ubuntu.com/ubuntu artful-security InRelease [78.6 kB]
Get:5 http://archive.ubuntu.com/ubuntu artful/main amd64 Packages [1,071 kB]
Get:6 http://archive.ubuntu.com/ubuntu artful/main i386 Packages [1,067 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful/main Translation-en [542 kB]
Get:8 http://archive.ubuntu.com/ubuntu artful/main Translation-en_CA [5,448 B]
Get:9 http://archive.ubuntu.com/ubuntu artful/main amd64 DEP-11 Metadata [397 kB]
Get:10 http://archive.ubuntu.com/ubuntu artful/main DEP-11 64x64 Icons [263 kB]
Get:11 http://archive.ubuntu.com/ubuntu artful/restricted amd64 Packages [8,852 B]
Get:12 http://archive.ubuntu.com/ubuntu artful/restricted i386 Packages [8,876 B]
Get:13 http://archive.ubuntu.com/ubuntu artful/restricted Translation-en [2,788 B]
Get:14 http://archive.ubuntu.com/ubuntu artful/universe i386 Packages [8,066 kB]
Err:14 http://archive.ubuntu.com/ubuntu artful/universe i386 Packages          
  Hash Sum mismatch
  Hashes of expected file:
   - Filesize:8066340 [weak]
   - SHA256:4fd48c457f32ebc2dba552e137605194760f9166e6f87562afae03c4059716ec
   - SHA1:d12bb47663590f62a5c95d30b9561d4098b8357f [weak]
   - MD5Sum:17178f6f07dec641aaea6ed48855639a [weak]
  Hashes of received file:
   - SHA256:225b586ae8299b763c39612f1549c2ad8cbc1019135f766ff8b56d4addea9d7e
   - SHA1:8bab4dafb004b34b681fe8f54442f083b2513234 [weak]
   - MD5Sum:51f01728ae5cd4dcbd8d813e43027da8 [weak]
   - Filesize:8066340 [weak]
  Last modification reported: Thu, 19 Oct 2017 12:56:35 +0000
  Release file created at: Thu, 19 Oct 2017 12:55:45 +0000
Get:15 http://archive.ubuntu.com/ubuntu artful/universe amd64 Packages [8,103 kB]
Err:15 http://archive.ubuntu.com/ubuntu artful/universe amd64 Packages         
  
Get:16 http://archive.ubuntu.com/ubuntu artful/universe Translation-en_CA [1,124 B]
Get:17 http://archive.ubuntu.com/ubuntu artful/universe Translation-en [4,789 kB]
Get:18 http://archive.ubuntu.com/ubuntu artful/universe amd64 DEP-11 Metadata [2,845 kB]
Err:18 http://archive.ubuntu.com/ubuntu artful/universe amd64 DEP-11 Metadata  
  
Get:19 http://archive.ubuntu.com/ubuntu artful/universe DEP-11 64x64 Icons [7,915 kB]
Err:19 http://archive.ubuntu.com/ubuntu artful/universe DEP-11 64x64 Icons     
  
Get:20 http://archive.ubuntu.com/ubuntu artful/multiverse amd64 Packages [150 kB]
Get:21 http://archive.ubuntu.com/ubuntu artful/multiverse i386 Packages [143 kB]
Get:22 http://archive.ubuntu.com/ubuntu artful/multiverse Translation-en [108 kB]
Get:23 http://archive.ubuntu.com/ubuntu artful/multiverse amd64 DEP-11 Metadata [43.8 kB]
Get:24 http://archive.ubuntu.com/ubuntu artful/multiverse DEP-11 64x64 Icons [207 kB]
Get:25 http://archive.ubuntu.com/ubuntu artful-updates/main i386 Packages [180 kB]
Get:26 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 Packages [182 kB]
Get:27 http://archive.ubuntu.com/ubuntu artful-updates/main Translation-en [82.3 kB]
Get:28 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 DEP-11 Metadata [73.3 kB]
Get:29 http://archive.ubuntu.com/ubuntu artful-updates/main DEP-11 64x64 Icons [49.2 kB]
Get:30 http://archive.ubuntu.com/ubuntu artful-updates/restricted i386 Packages [2,180 B]
Get:31 http://archive.ubuntu.com/ubuntu artful-updates/restricted amd64 Packages [2,192 B]
Get:32 http://archive.ubuntu.com/ubuntu artful-updates/restricted Translation-en [1,284 B]
Get:33 http://archive.ubuntu.com/ubuntu artful-updates/universe i386 Packages [73.1 kB]
Get:34 http://archive.ubuntu.com/ubuntu artful-updates/universe amd64 Packages [73.6 kB]
Get:35 http://archive.ubuntu.com/ubuntu artful-updates/universe Translation-en [42.0 kB]
Get:36 http://archive.ubuntu.com/ubuntu artful-updates/universe amd64 DEP-11 Metadata [49.5 kB]
Get:37 http://archive.ubuntu.com/ubuntu artful-updates/universe DEP-11 64x64 Icons [55.3 kB]
Get:38 http://archive.ubuntu.com/ubuntu artful-updates/multiverse i386 Packages [1,980 B]
Get:39 http://archive.ubuntu.com/ubuntu artful-updates/multiverse amd64 Packages [1,828 B]
Get:40 http://archive.ubuntu.com/ubuntu artful-updates/multiverse Translation-en [1,124 B]
Get:41 http://archive.ubuntu.com/ubuntu artful-backports/main amd64 Packages [1,516 B]
Get:42 http://archive.ubuntu.com/ubuntu artful-backports/main i386 Packages [1,512 B]
Get:43 http://archive.ubuntu.com/ubuntu artful-backports/main Translation-en [668 B]
Get:44 http://archive.ubuntu.com/ubuntu artful-backports/universe i386 Packages [3,396 B]
Get:45 http://archive.ubuntu.com/ubuntu artful-backports/universe amd64 Packages [3,408 B]
Get:46 http://archive.ubuntu.com/ubuntu artful-backports/universe Translation-en [1,880 B]
Get:47 http://archive.ubuntu.com/ubuntu artful-backports/universe amd64 DEP-11 Metadata [4,700 B]
Get:48 http://archive.ubuntu.com/ubuntu artful-backports/universe DEP-11 64x64 Icons [2,717 B]
Get:49 http://archive.ubuntu.com/ubuntu artful-security/main i386 Packages [82.7 kB]
Get:50 http://archive.ubuntu.com/ubuntu artful-security/main amd64 Packages [84.4 kB]
Get:51 http://archive.ubuntu.com/ubuntu artful-security/main Translation-en [39.6 kB]
Get:52 http://archive.ubuntu.com/ubuntu artful-security/main amd64 DEP-11 Metadata [2,924 B]
Get:53 http://archive.ubuntu.com/ubuntu artful-security/main DEP-11 64x64 Icons [4,471 B]
Get:54 http://archive.ubuntu.com/ubuntu artful-security/restricted amd64 Packages [2,192 B]
Get:55 http://archive.ubuntu.com/ubuntu artful-security/restricted i386 Packages [2,180 B]
Get:56 http://archive.ubuntu.com/ubuntu artful-security/restricted Translation-en [1,284 B]
Get:57 http://archive.ubuntu.com/ubuntu artful-security/universe i386 Packages [31.3 kB]
Get:58 http://archive.ubuntu.com/ubuntu artful-security/universe amd64 Packages [31.4 kB]
Get:59 http://archive.ubuntu.com/ubuntu artful-security/universe Translation-en [19.8 kB]
Get:60 http://archive.ubuntu.com/ubuntu artful-security/universe amd64 DEP-11 Metadata [10.4 kB]
Get:61 http://archive.ubuntu.com/ubuntu artful-security/universe DEP-11 64x64 Icons [10.2 kB]
Get:62 http://archive.ubuntu.com/ubuntu artful-security/multiverse amd64 Packages [1,828 B]
Get:63 http://archive.ubuntu.com/ubuntu artful-security/multiverse i386 Packages [1,980 B]
Get:64 http://archive.ubuntu.com/ubuntu artful-security/multiverse Translation-en [1,124 B]
Fetched 37.4 MB in 36s (1,030 kB/s)                                            
Reading package lists... Done
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/artful/universe/binary-i386/by-hash/SHA256/4fd48c457f32ebc2dba552e137605194760f9166e6f87562afae03c4059716ec  Hash Sum mismatch
   Hashes of expected file:
    - Filesize:8066340 [weak]
    - SHA256:4fd48c457f32ebc2dba552e137605194760f9166e6f87562afae03c4059716ec
    - SHA1:d12bb47663590f62a5c95d30b9561d4098b8357f [weak]
    - MD5Sum:17178f6f07dec641aaea6ed48855639a [weak]
   Hashes of received file:
    - SHA256:225b586ae8299b763c39612f1549c2ad8cbc1019135f766ff8b56d4addea9d7e
    - SHA1:8bab4dafb004b34b681fe8f54442f083b2513234 [weak]
    - MD5Sum:51f01728ae5cd4dcbd8d813e43027da8 [weak]
    - Filesize:8066340 [weak]
   Last modification reported: Thu, 19 Oct 2017 12:56:35 +0000
   Release file created at: Thu, 19 Oct 2017 12:55:45 +0000
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/artful/universe/binary-amd64/by-hash/SHA256/c4b2576639b1cfed7b8aff8be33fc74a8de60b0d8ea5eea6563626ef7849fae3  
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/artful/universe/dep11/by-hash/SHA256/22152e8604d3fc1c0eecd939a3fa78c60cef396f1dc10855f3ed6a036d06b722  
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/artful/universe/dep11/by-hash/SHA256/87517ea9340abe20e43a652dd9e0668bff31dcd20260caf9f17870ed178dba88  
E: Some index files failed to download. They have been ignored, or old ones used instead.


```

The line 
```

sudo apt upgrade

```
launched a download that took a few minutes in terminal, which shows errors that appear similar
```

mind@mind-desktop:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-4.13.0-32 linux-headers-4.13.0-32-generic
  linux-image-4.13.0-32-generic linux-image-extra-4.13.0-32-generic
  linux-signed-image-4.13.0-32-generic
The following packages will be upgraded:
  apparmor bind9-host deja-dup dnsutils firefox firefox-locale-en fwupd
  gir1.2-gdkpixbuf-2.0 gir1.2-javascriptcoregtk-4.0 gir1.2-webkit2-4.0
  iproute2 libapparmor-perl libapparmor1 libbind9-140 libc-bin libc6 libc6-dbg
  libcurl3 libcurl3-gnutls libdfu1 libdns-export162 libdns162 libegl1-mesa
  libfwupd1 libgbm1 libgcab-1.0-0 libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-bin
  libgdk-pixbuf2.0-common libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa
  libgles2-mesa libisc-export160 libisc160 libisccc140 libisccfg140
  libjavascriptcoregtk-4.0-18 liblwres141 libminiupnpc10 libparted2
  libpoppler-glib8 libpoppler68 libtasn1-6 libwayland-egl1-mesa
  libwebkit2gtk-4.0-37 libxatracker2 linux-firmware linux-generic
  linux-headers-generic linux-image-generic linux-signed-generic
  linux-signed-image-generic locales multiarch-support openssh-client parted
  poppler-utils python3-distupgrade python3-update-manager rsync simple-scan
  thunderbird thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-us transmission-common transmission-gtk
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk update-manager
  update-manager-core
72 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 242 MB of archives.
After this operation, 333 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libc6-dbg amd64 2.26-0ubuntu2.1 [4,997 kB]
Get:2 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libc6 amd64 2.26-0ubuntu2.1 [2,780 kB]
Ign:2 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libc6 amd64 2.26-0ubuntu2.1
Get:3 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 locales all 2.26-0ubuntu2.1 [3,128 kB]
Ign:3 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 locales all 2.26-0ubuntu2.1
Get:4 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libc-bin amd64 2.26-0ubuntu2.1 [609 kB]
Get:5 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libtasn1-6 amd64 4.12-2.1ubuntu0.1 [35.8 kB]
Get:6 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 iproute2 amd64 4.9.0-1ubuntu2.1 [628 kB]
Get:7 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libapparmor1 amd64 2.11.0-2ubuntu17.1 [28.9 kB]
Get:8 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libisc-export160 amd64 1:9.10.3.dfsg.P4-12.6ubuntu1.1 [155 kB]
Get:9 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libdns-export162 amd64 1:9.10.3.dfsg.P4-12.6ubuntu1.1 [671 kB]
Get:10 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 multiarch-support amd64 2.26-0ubuntu2.1 [6,828 B]
Get:11 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libapparmor-perl amd64 2.11.0-2ubuntu17.1 [32.2 kB]
Get:12 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 apparmor amd64 2.11.0-2ubuntu17.1 [484 kB]
Err:12 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 apparmor amd64 2.11.0-2ubuntu17.1
  Hash Sum mismatch
  Hashes of expected file:
   - SHA256:24528192b5ded6e6e0c099eb6df51380853e10c822fa34446d57b2aa7b11870e
   - SHA1:ccb5c3fa043b6ec32cbe03bacb093a3d7714f5ad [weak]
   - MD5Sum:75a0d41617638b6bcc1dc1694f491aec [weak]
   - Filesize:484414 [weak]
  Hashes of received file:
   - SHA256:becf550017b6a0218b7f7aae501428c595c3f16a5925b457b260bf0093c52e47
   - SHA1:4dc6ab138368e3495c01062912714d6cc05deed5 [weak]
   - MD5Sum:237d197cc542936253d1f2495dcd4864 [weak]
   - Filesize:484414 [weak]
  Last modification reported: Thu, 01 Feb 2018 13:29:18 +0000
Get:13 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 bind9-host amd64 1:9.10.3.dfsg.P4-12.6ubuntu1.1 [50.1 kB]
Get:14 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 dnsutils amd64 1:9.10.3.dfsg.P4-12.6ubuntu1.1 [105 kB]
Get:15 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libisc160 amd64 1:9.10.3.dfsg.P4-12.6ubuntu1.1 [219 kB]
Get:16 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libdns162 amd64 1:9.10.3.dfsg.P4-12.6ubuntu1.1 [883 kB]
Get:17 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libisccc140 amd64 1:9.10.3.dfsg.P4-12.6ubuntu1.1 [16.6 kB]
Get:18 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libisccfg140 amd64 1:9.10.3.dfsg.P4-12.6ubuntu1.1 [40.9 kB]
Get:19 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 liblwres141 amd64 1:9.10.3.dfsg.P4-12.6ubuntu1.1 [34.5 kB]
Get:20 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libbind9-140 amd64 1:9.10.3.dfsg.P4-12.6ubuntu1.1 [23.9 kB]
Get:21 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 parted amd64 3.2-18ubuntu0.1 [42.3 kB]
Get:22 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libparted2 amd64 3.2-18ubuntu0.1 [123 kB]
Get:23 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 openssh-client amd64 1:7.5p1-10ubuntu0.1 [608 kB]
Get:24 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 ubuntu-release-upgrader-gtk all 1:17.10.9 [9,282 B]
Get:25 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 ubuntu-release-upgrader-core all 1:17.10.9 [24.1 kB]
Get:26 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 update-manager all 1:17.10.13 [548 kB]
Ign:26 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 update-manager all 1:17.10.13
Get:27 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 update-manager-core all 1:17.10.13 [8,410 B]
Get:28 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 python3-distupgrade all 1:17.10.9 [102 kB]
Get:29 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 python3-update-manager all 1:17.10.13 [33.9 kB]
Get:30 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 gir1.2-webkit2-4.0 amd64 2.18.6-0ubuntu0.17.10.1 [67.7 kB]
Get:31 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 gir1.2-javascriptcoregtk-4.0 amd64 2.18.6-0ubuntu0.17.10.1 [20.8 kB]
Get:32 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libwebkit2gtk-4.0-37 amd64 2.18.6-0ubuntu0.17.10.1 [11.2 MB]
Ign:32 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libwebkit2gtk-4.0-37 amd64 2.18.6-0ubuntu0.17.10.1
Get:33 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libjavascriptcoregtk-4.0-18 amd64 2.18.6-0ubuntu0.17.10.1 [4,052 kB]
Get:34 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libwayland-egl1-mesa amd64 17.2.8-0ubuntu0~17.10.1 [5,778 B]
Get:35 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libegl1-mesa amd64 17.2.8-0ubuntu0~17.10.1 [85.3 kB]
Get:36 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libgbm1 amd64 17.2.8-0ubuntu0~17.10.1 [24.4 kB]
Get:37 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libgl1-mesa-glx amd64 17.2.8-0ubuntu0~17.10.1 [130 kB]
Get:38 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libgles2-mesa amd64 17.2.8-0ubuntu0~17.10.1 [13.5 kB]
Get:39 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libglapi-mesa amd64 17.2.8-0ubuntu0~17.10.1 [22.2 kB]
Get:40 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libgl1-mesa-dri amd64 17.2.8-0ubuntu0~17.10.1 [5,707 kB]
Get:41 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libgdk-pixbuf2.0-0 amd64 2.36.11-1ubuntu0.1 [165 kB]
Get:42 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libgdk-pixbuf2.0-common all 2.36.11-1ubuntu0.1 [4,488 B]
Get:43 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 rsync amd64 3.1.2-2ubuntu0.2 [334 kB]
Ign:43 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 rsync amd64 3.1.2-2ubuntu0.2
Get:44 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 deja-dup amd64 36.3-0ubuntu0.1 [478 kB]
Get:45 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 firefox amd64 58.0.1+build1-0ubuntu0.17.10.1 [45.0 MB]
Ign:45 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 firefox amd64 58.0.1+build1-0ubuntu0.17.10.1
Get:46 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 firefox-locale-en amd64 58.0.1+build1-0ubuntu0.17.10.1 [708 kB]
Get:47 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libdfu1 amd64 0.9.7-2ubuntu1 [50.5 kB]
Get:48 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libfwupd1 amd64 0.9.7-2ubuntu1 [45.0 kB]
Get:49 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 fwupd amd64 0.9.7-2ubuntu1 [1,188 kB]
Get:50 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 gir1.2-gdkpixbuf-2.0 amd64 2.36.11-1ubuntu0.1 [7,670 B]
Get:51 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libcurl3 amd64 7.55.1-1ubuntu2.3 [196 kB]
Get:52 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libcurl3-gnutls amd64 7.55.1-1ubuntu2.3 [193 kB]
Get:53 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libgcab-1.0-0 amd64 0.7-4ubuntu0.1 [28.9 kB]
Get:54 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libgdk-pixbuf2.0-bin amd64 2.36.11-1ubuntu0.1 [7,802 B]
Get:55 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libminiupnpc10 amd64 1.9.20140610-4ubuntu1.1 [24.1 kB]
Get:56 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 poppler-utils amd64 0.57.0-2ubuntu4.2 [141 kB]
Get:57 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libpoppler-glib8 amd64 0.57.0-2ubuntu4.2 [108 kB]
Get:58 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libpoppler68 amd64 0.57.0-2ubuntu4.2 [787 kB]
Get:59 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 libxatracker2 amd64 17.2.8-0ubuntu0~17.10.1 [1,078 kB]
Get:60 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 linux-firmware all 1.169.3 [42.5 MB]
Ign:60 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 linux-firmware all 1.169.3
Get:61 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 linux-image-4.13.0-32-generic amd64 4.13.0-32.35 [20.8 MB]
Ign:61 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 linux-image-4.13.0-32-generic amd64 4.13.0-32.35
Get:62 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 linux-image-extra-4.13.0-32-generic amd64 4.13.0-32.35 [31.5 MB]
Ign:62 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 linux-image-extra-4.13.0-32-generic amd64 4.13.0-32.35
Get:63 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 linux-generic amd64 4.13.0.32.34 [1,784 B]
Get:64 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 linux-image-generic amd64 4.13.0.32.34 [2,444 B]
Get:65 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 linux-signed-image-4.13.0-32-generic amd64 4.13.0-32.35 [4,004 B]
Get:66 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 linux-signed-generic amd64 4.13.0.32.34 [1,816 B]
Get:67 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 linux-signed-image-generic amd64 4.13.0.32.34 [2,484 B]
Get:68 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 linux-headers-4.13.0-32 all 4.13.0-32.35 [10.9 MB]
Get:69 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 linux-headers-4.13.0-32-generic amd64 4.13.0-32.35 [691 kB]
Get:70 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 linux-headers-generic amd64 4.13.0.32.34 [2,420 B]
Get:71 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 simple-scan amd64 3.26.3-0ubuntu0.17.10.0 [169 kB]
Get:72 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 thunderbird-locale-en amd64 1:52.6.0+build1-0ubuntu0.17.10.1 [469 kB]
Get:73 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 thunderbird amd64 1:52.6.0+build1-0ubuntu0.17.10.1 [46.5 MB]
Ign:73 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 thunderbird amd64 1:52.6.0+build1-0ubuntu0.17.10.1
Get:74 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 thunderbird-gnome-support amd64 1:52.6.0+build1-0ubuntu0.17.10.1 [8,536 B]
Get:75 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 thunderbird-locale-en-us all 1:52.6.0+build1-0ubuntu0.17.10.1 [9,656 B]
Get:76 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 transmission-common all 2.92-2ubuntu3.1 [237 kB]
Get:77 http://archive.ubuntu.com/ubuntu artful-updates/main amd64 transmission-gtk amd64 2.92-2ubuntu3.1 [322 kB]
Get:2 http://archive.ubuntu.com/ubuntu artful-security/main amd64 libc6 amd64 2.26-0ubuntu2.1 [2,780 kB]
Get:3 http://archive.ubuntu.com/ubuntu artful-updates/main i386 locales all 2.26-0ubuntu2.1 [3,128 kB]
Get:26 http://archive.ubuntu.com/ubuntu artful-updates/main i386 update-manager all 1:17.10.13 [548 kB]
Get:32 http://archive.ubuntu.com/ubuntu artful-security/main amd64 libwebkit2gtk-4.0-37 amd64 2.18.6-0ubuntu0.17.10.1 [11.2 MB]
Err:32 http://archive.ubuntu.com/ubuntu artful-security/main amd64 libwebkit2gtk-4.0-37 amd64 2.18.6-0ubuntu0.17.10.1
  Hash Sum mismatch
  Hashes of expected file:
   - SHA256:79675933d286c9369034077750061e7612795705ccc6a122c18662e1164ce673
   - SHA1:ac3d74ef157a77ff7cbb0ebe015ebf67fcd2b256 [weak]
   - MD5Sum:4f9398db4d5a0fad2bba0703b28e5bcd [weak]
   - Filesize:11194796 [weak]
  Hashes of received file:
   - SHA256:53792402c8a7aa158de17b4b626a1611fa9d84713871a6fb8db3849d1067654c
   - SHA1:6b734b3b9d498969f052da9814fde77ca32bda39 [weak]
   - MD5Sum:720d7fc4a858dcc7a4eca443bf5fdbbb [weak]
   - Filesize:11194796 [weak]
  Last modification reported: Tue, 30 Jan 2018 21:19:22 +0000
Get:43 http://archive.ubuntu.com/ubuntu artful-security/main amd64 rsync amd64 3.1.2-2ubuntu0.2 [334 kB]
Get:45 http://archive.ubuntu.com/ubuntu artful-security/main amd64 firefox amd64 58.0.1+build1-0ubuntu0.17.10.1 [45.0 MB]
Err:45 http://archive.ubuntu.com/ubuntu artful-security/main amd64 firefox amd64 58.0.1+build1-0ubuntu0.17.10.1
  Hash Sum mismatch
  Hashes of expected file:
   - SHA256:ca379b02590870c154207d25bd95b89c5d77158f8bef92f5563b6f7c7536f7cf
   - SHA1:224086a61a15903c4779ccccfd6d68fa3d0d0408 [weak]
   - MD5Sum:6c5227b9e6058b8ca3b58b7379b62d77 [weak]
   - Filesize:45008826 [weak]
  Hashes of received file:
   - SHA256:a260fde189ea5f4aa5564095bbb06681362755de031bc1d6f9d02e1b29faf5f8
   - SHA1:16d6e1dab16bcaf3fe9acd5dd54023060c256c50 [weak]
   - MD5Sum:3f267b5eede4c6e7496ca5bbf4cf44b4 [weak]
   - Filesize:45008826 [weak]
  Last modification reported: Wed, 31 Jan 2018 15:28:29 +0000
Get:60 http://archive.ubuntu.com/ubuntu artful-updates/main i386 linux-firmware all 1.169.3 [42.5 MB]
Err:60 http://archive.ubuntu.com/ubuntu artful-updates/main i386 linux-firmware all 1.169.3
  Hash Sum mismatch
  Hashes of expected file:
   - SHA256:6c047d2d90404b9d4ba31aaaab8ffd05b20fe2251eb13672ee586523e8b96fda
   - SHA1:db77b45ffbcaeb67bc54a86c685eaef923c517a4 [weak]
   - MD5Sum:ecbd0d6030ec1b2c11d68a42fb997b48 [weak]
   - Filesize:42504346 [weak]
  Hashes of received file:
   - SHA256:30e4816ad730380b968599c13ae5ac029ad251adbb67792eaf874f97dd2b8086
   - SHA1:fa64bd51bd1c1717870504971d5eb14621d3e3d3 [weak]
   - MD5Sum:5b40666f43f465330e142256ea3b1270 [weak]
   - Filesize:42504346 [weak]
  Last modification reported: Fri, 26 Jan 2018 10:44:52 +0000
Get:61 http://archive.ubuntu.com/ubuntu artful-security/main amd64 linux-image-4.13.0-32-generic amd64 4.13.0-32.35 [20.8 MB]
Err:61 http://archive.ubuntu.com/ubuntu artful-security/main amd64 linux-image-4.13.0-32-generic amd64 4.13.0-32.35
  Hash Sum mismatch
  Hashes of expected file:
   - SHA256:65fdcabcd741395590b30d423267bd34a331756d26a08e5a89c6c144fd7b8e28
   - SHA1:e5861d7a1b4175c027893dead1d0e33ec5cfccaf [weak]
   - MD5Sum:c866776413112308c52db88c4d985482 [weak]
   - Filesize:20827836 [weak]
  Hashes of received file:
   - SHA256:521f2e9ab850d538a785c9e6acc10d6e7c0c0d9b04da2fc4a6e74df83af0a154
   - SHA1:8950f295b1285297b0fb10b53c665f4273d1ae0c [weak]
   - MD5Sum:2e56c56dd5c33756a44bf06ebd615da2 [weak]
   - Filesize:20827836 [weak]
  Last modification reported: Fri, 26 Jan 2018 00:46:49 +0000
Get:62 http://archive.ubuntu.com/ubuntu artful-security/main amd64 linux-image-extra-4.13.0-32-generic amd64 4.13.0-32.35 [31.5 MB]
Err:62 http://archive.ubuntu.com/ubuntu artful-security/main amd64 linux-image-extra-4.13.0-32-generic amd64 4.13.0-32.35
  Hash Sum mismatch
  Hashes of expected file:
   - SHA256:ab42072fa888fe3bf5bd434e5b5a8f324a351d7beb577723025d566bfc7950c8
   - SHA1:d901ddca6cfe8455ef41b8229c419b587e2551a9 [weak]
   - MD5Sum:1e3265c4c13ef6ebd5c0da2bada4a440 [weak]
   - Filesize:31533336 [weak]
  Hashes of received file:
   - SHA256:4dac333162184ce14f6587cb8fe49d53e620db560c235df343eab62e6b81785e
   - SHA1:14dc3845d452d6b9eb786a6975dcd689511b8766 [weak]
   - MD5Sum:b08593a7f772d3727380342caa9b2ea6 [weak]
   - Filesize:31533336 [weak]
  Last modification reported: Fri, 26 Jan 2018 00:46:35 +0000
Get:73 http://archive.ubuntu.com/ubuntu artful-security/main amd64 thunderbird amd64 1:52.6.0+build1-0ubuntu0.17.10.1 [46.5 MB]
Err:73 http://archive.ubuntu.com/ubuntu artful-security/main amd64 thunderbird amd64 1:52.6.0+build1-0ubuntu0.17.10.1
  Hash Sum mismatch
  Hashes of expected file:
   - SHA256:c62b43abab4b39523d54a70943ff555c65510111005b1c819f16e0a03ce151fc
   - SHA1:afe492987150242eda025bc2e69914e790dafbd4 [weak]
   - MD5Sum:7e3cdbe7523fb4ab7376da6d2b474bfd [weak]
   - Filesize:46453292 [weak]
  Hashes of received file:
   - SHA256:9f21adb696b9d0be860b24ad2aa668b698525095cd1cdd363bd76e85c1068dc0
   - SHA1:ad9624e8df6e04c615a31a56b2c40a9ce631dff2 [weak]
   - MD5Sum:3ac09fd9c9bc3c067caf753bb0212fd2 [weak]
   - Filesize:46453292 [weak]
  Last modification reported: Mon, 29 Jan 2018 10:48:52 +0000
Fetched 447 MB in 7min 18s (1,018 kB/s)                                        
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.11.0-2ubuntu17.1_amd64.deb  Hash Sum mismatch
   Hashes of expected file:
    - SHA256:24528192b5ded6e6e0c099eb6df51380853e10c822fa34446d57b2aa7b11870e
    - SHA1:ccb5c3fa043b6ec32cbe03bacb093a3d7714f5ad [weak]
    - MD5Sum:75a0d41617638b6bcc1dc1694f491aec [weak]
    - Filesize:484414 [weak]
   Hashes of received file:
    - SHA256:becf550017b6a0218b7f7aae501428c595c3f16a5925b457b260bf0093c52e47
    - SHA1:4dc6ab138368e3495c01062912714d6cc05deed5 [weak]
    - MD5Sum:237d197cc542936253d1f2495dcd4864 [weak]
    - Filesize:484414 [weak]
   Last modification reported: Thu, 01 Feb 2018 13:29:18 +0000
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/w/webkit2gtk/libwebkit2gtk-4.0-37_2.18.6-0ubuntu0.17.10.1_amd64.deb  Hash Sum mismatch
   Hashes of expected file:
    - SHA256:79675933d286c9369034077750061e7612795705ccc6a122c18662e1164ce673
    - SHA1:ac3d74ef157a77ff7cbb0ebe015ebf67fcd2b256 [weak]
    - MD5Sum:4f9398db4d5a0fad2bba0703b28e5bcd [weak]
    - Filesize:11194796 [weak]
   Hashes of received file:
    - SHA256:53792402c8a7aa158de17b4b626a1611fa9d84713871a6fb8db3849d1067654c
    - SHA1:6b734b3b9d498969f052da9814fde77ca32bda39 [weak]
    - MD5Sum:720d7fc4a858dcc7a4eca443bf5fdbbb [weak]
    - Filesize:11194796 [weak]
   Last modification reported: Tue, 30 Jan 2018 21:19:22 +0000
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_58.0.1+build1-0ubuntu0.17.10.1_amd64.deb  Hash Sum mismatch
   Hashes of expected file:
    - SHA256:ca379b02590870c154207d25bd95b89c5d77158f8bef92f5563b6f7c7536f7cf
    - SHA1:224086a61a15903c4779ccccfd6d68fa3d0d0408 [weak]
    - MD5Sum:6c5227b9e6058b8ca3b58b7379b62d77 [weak]
    - Filesize:45008826 [weak]
   Hashes of received file:
    - SHA256:a260fde189ea5f4aa5564095bbb06681362755de031bc1d6f9d02e1b29faf5f8
    - SHA1:16d6e1dab16bcaf3fe9acd5dd54023060c256c50 [weak]
    - MD5Sum:3f267b5eede4c6e7496ca5bbf4cf44b4 [weak]
    - Filesize:45008826 [weak]
   Last modification reported: Wed, 31 Jan 2018 15:28:29 +0000
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.169.3_all.deb  Hash Sum mismatch
   Hashes of expected file:
    - SHA256:6c047d2d90404b9d4ba31aaaab8ffd05b20fe2251eb13672ee586523e8b96fda
    - SHA1:db77b45ffbcaeb67bc54a86c685eaef923c517a4 [weak]
    - MD5Sum:ecbd0d6030ec1b2c11d68a42fb997b48 [weak]
    - Filesize:42504346 [weak]
   Hashes of received file:
    - SHA256:30e4816ad730380b968599c13ae5ac029ad251adbb67792eaf874f97dd2b8086
    - SHA1:fa64bd51bd1c1717870504971d5eb14621d3e3d3 [weak]
    - MD5Sum:5b40666f43f465330e142256ea3b1270 [weak]
    - Filesize:42504346 [weak]
   Last modification reported: Fri, 26 Jan 2018 10:44:52 +0000
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-4.13.0-32-generic_4.13.0-32.35_amd64.deb  Hash Sum mismatch
   Hashes of expected file:
    - SHA256:65fdcabcd741395590b30d423267bd34a331756d26a08e5a89c6c144fd7b8e28
    - SHA1:e5861d7a1b4175c027893dead1d0e33ec5cfccaf [weak]
    - MD5Sum:c866776413112308c52db88c4d985482 [weak]
    - Filesize:20827836 [weak]
   Hashes of received file:
    - SHA256:521f2e9ab850d538a785c9e6acc10d6e7c0c0d9b04da2fc4a6e74df83af0a154
    - SHA1:8950f295b1285297b0fb10b53c665f4273d1ae0c [weak]
    - MD5Sum:2e56c56dd5c33756a44bf06ebd615da2 [weak]
    - Filesize:20827836 [weak]
   Last modification reported: Fri, 26 Jan 2018 00:46:49 +0000
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-4.13.0-32-generic_4.13.0-32.35_amd64.deb  Hash Sum mismatch
   Hashes of expected file:
    - SHA256:ab42072fa888fe3bf5bd434e5b5a8f324a351d7beb577723025d566bfc7950c8
    - SHA1:d901ddca6cfe8455ef41b8229c419b587e2551a9 [weak]
    - MD5Sum:1e3265c4c13ef6ebd5c0da2bada4a440 [weak]
    - Filesize:31533336 [weak]
   Hashes of received file:
    - SHA256:4dac333162184ce14f6587cb8fe49d53e620db560c235df343eab62e6b81785e
    - SHA1:14dc3845d452d6b9eb786a6975dcd689511b8766 [weak]
    - MD5Sum:b08593a7f772d3727380342caa9b2ea6 [weak]
    - Filesize:31533336 [weak]
   Last modification reported: Fri, 26 Jan 2018 00:46:35 +0000
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_52.6.0+build1-0ubuntu0.17.10.1_amd64.deb  Hash Sum mismatch
   Hashes of expected file:
    - SHA256:c62b43abab4b39523d54a70943ff555c65510111005b1c819f16e0a03ce151fc
    - SHA1:afe492987150242eda025bc2e69914e790dafbd4 [weak]
    - MD5Sum:7e3cdbe7523fb4ab7376da6d2b474bfd [weak]
    - Filesize:46453292 [weak]
   Hashes of received file:
    - SHA256:9f21adb696b9d0be860b24ad2aa668b698525095cd1cdd363bd76e85c1068dc0
    - SHA1:ad9624e8df6e04c615a31a56b2c40a9ce631dff2 [weak]
    - MD5Sum:3ac09fd9c9bc3c067caf753bb0212fd2 [weak]
    - Filesize:46453292 [weak]
   Last modification reported: Mon, 29 Jan 2018 10:48:52 +0000
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.


```

Thanks again for all this help I don't understand much of this !

---

### Post by #&amp;thj^% on 2018-02-12
> But I changed nothing, this is how the file was looking. Running 
Yes you did>>> "When you unchecked "source code" in software and updates,"
Do you remember where you downloaded your install-medium from?
If not you may want to go here: [https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop) and download again.
16.04 is there also on that page I linked to and is a LTS 5 year supported.(More Stable)
This is just crazy seeing this twice here in UF. with mismatched  Hashes and not a clue insight.:confused:

---

### Post by mindbj on 2018-02-12
Thanks so much, yeah It seems like a weird issue, I had got ubuntu from the same link you provided (which I think is official page), i will re-install with the more stable version thanks again so very much for your time !

---

### Post by #&amp;thj^% on 2018-02-12
I wish I had actually done something to deserve your Thanks! :)
Hope this ends better for you this time, and Good Luck.
Kind Regards

---

### Post by mindbj on 2018-02-12
Just finished installing Ubuntu 16.04 LTS and the issue persists :( I guess it's something with my system that just doesn't work with this OS. I will take a look at BIOS settings, but on defaults it had been ok for windows10 if you ever have any ideas just message !

---

### Post by #&amp;thj^% on 2018-02-12
Well we are both earning our keep today!:)
Seems as if a older bug is making a revist:
[http://www.chiark.greenend.org.uk/~cjwatson/blog/no-more-hash-sum-mismatch-errors.html](http://www.chiark.greenend.org.uk/~cjwatson/blog/no-more-hash-sum-mismatch-errors.html)

This is a known issue, and is made worse for clients behind proxy caches. Some large organisations and "ISPs" (especially in remote parts of the world) have transparent caches of which you may not be aware.
The fundamental issue is that the apt repository format is subject to race conditions when a mirror is updated. This problem particularly affects repositories that change rapidly, such as the development release and point releases.

Please give this a try:

```
sudo sed -i -re 's/\w+\.archive\.ubuntu\.com/archive.ubuntu.com/g' /etc/apt/sources.list

```
Now Clean again with:

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get clean
sudo apt-get update
```

This is just added as another possible solution.
I still use this method even now.
And this is just use the closest mirror to you
apt-get now supports a 'mirror' method that will automatically select a good mirror based on your location. By Putting:

```
deb mirror://mirrors.ubuntu.com/mirrors.txt xenial main restricted universe multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt xenial-updates main restricted universe multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt xenial-backports main restricted universe multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt xenial-security main restricted universe multiverse
```

on the top in your **/etc/apt/sources.list** file should be all that is needed to make it automatically pick a mirror for you based on your geographical location.

Note: that after making the change you need to run 
```
sudo apt-get update 
```
before doing any apt-get install for it to use your closest mirror.
BTW Here in the forums we do not solve threads via PM's everything is done out here in the forums to benefit all users, and future visitors. :)

---

### Post by mindbj on 2018-02-14
Yayy issue is finally resolved !! Sorry I didn't come sooner to say so :( Thank you again so very much I can now start learning some more and using my system.

---

### Post by #&amp;thj^% on 2018-02-14
Hey that's great! ;)
But could you elaborate a bit more on the steps you took to solve this?
And finally using the thread tools in your 1st post to mark Solved, it helps others when searching for solutions.
Thanks && Kind Regards

---

