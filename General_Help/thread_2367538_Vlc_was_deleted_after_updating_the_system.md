---
title: "Vlc was deleted after updating the system"
date: 2017-07-31
forum: General Help
---

### Post by offir on 2017-07-31
I have Ubuntu 16.04
A day or two ago there were several updates that came down
The computer has updated everything
I got a message OK

Now for some reason the vlc player was deleted
I tried to install it
But I get an error message



```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: libgles1-mesa (>= 7.8.1) but it is not going to be installed or
                libgles1
E: Unable to correct problems, you have held broken packages.
```

I tried the solution in this link but without success

[https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa]("https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa")


How can I fix it?

---

### Post by TheFu on 2017-07-31
I saw the same issue, so didn't patch my 16.04 laptop as normal until today.  There was a mess of dependency issues around wine and wine1.6. I removed WINE and allowed the updates through.  Then video playback started locking up the machine - with audio stuck at output too.  No different terminals and no remote ssh from other systems worked.  BRS was the only answer.

Was running 4.4.x kernel and decided installing the HWE stack was worth an attempt.  Have plenty of backups, so nothing was risked.

linux-headers-4.10.0-28-generic and lots of newer xorg packages were installed.  Old xorg packages were removed.
```

$ sudo aptitude install vlc
The following NEW packages will be installed:
  libgles1-mesa{ab} vlc vlc-nox{a} vlc-plugin-samba{a} 
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,397 kB of archives. After unpacking 16.1 MB will be used.
The following packages have unmet dependencies:
 libgles1-mesa : Depends: libglapi-mesa (= 12.0.6-0ubuntu0.16.04.1) but 17.0.7-0ubuntu0.16.04.1 is installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     libgles1-mesa [Not Installed]                      
2)     vlc [Not Installed]        
```

Aptitude is usually smarter about resolving package dependency issues.  It failed this time.  All the other dependency resolution efforts shown had libgl1-mesa* being downgraded along with 5 other packages.  Could it be a wayland dependency issue.

mpv still works perfectly. ;)

Just to be clear - this is a "me too" post. No answer. Sorry.

---

### Post by mc4man on 2017-07-31
You all need to get vlc from xenial-updates, it should only have a dep on libgles2-mesa whereas previous depended on both GLESv1 & GLESv2
[https://packages.ubuntu.com/xenial-updates/vlc](https://packages.ubuntu.com/xenial-updates/vlc)

Noting that the change occurred slightly before as in - 
> vlc (2.2.2-5ubuntu0.16.04.2) xenial; urgency=medium

  * Don't enable GLESv1 support. (LP: #1676845)

 -- Timo Aaltonen <tjaalton@debian.org>  Tue, 28 Mar 2017 14:23:57 +0300


Ex. here - 
> $ apt-cache policy libgles1-mesa libgles2-mesa vlc
libgles1-mesa:
  **Installed: (none)**
  Candidate: 17.0.0~xenial3
  Version table:
     17.0.0~xenial3 500
        500 [http://ppa.launchpad.net/mc3man/prop4me/ubuntu](http://ppa.launchpad.net/mc3man/prop4me/ubuntu) xenial/main amd64 Packages
     12.0.6-0ubuntu0.16.04.1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
     11.2.0-1ubuntu2 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages

libgles2-mesa:
  Installed: 17.0.7-0ubuntu0.16.04.1
  Candidate: 17.0.7-0ubuntu0.16.04.1
  Version table:
 *** 17.0.7-0ubuntu0.16.04.1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     17.0.0~xenial3 500
        500 [http://ppa.launchpad.net/mc3man/prop4me/ubuntu](http://ppa.launchpad.net/mc3man/prop4me/ubuntu) xenial/main amd64 Packages
     11.2.0-1ubuntu2 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages

vlc:
  Installed: 2.2.2-5ubuntu0.16.04.3
  Candidate: 2.2.2-5ubuntu0.16.04.3
  Version table:
 *** 2.2.2-5ubuntu0.16.04.3 500
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     2.2.2-5 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages


---

### Post by offir on 2017-08-01
I did not understand
How do i install vlc ?

---

### Post by TheFu on 2017-08-01
I have universe and multverse Xenial-updates enabled; must be the default.

But .... I also have videolan-ubuntu-master-daily-xenial.list enabled. Let me see if they have an 'update' ... there is a daily-stable PPA. Hummmm.  No joy.  

```

$ sudo aptitude  install libgles1-mesa libgles2-mesa vlc
libgles2-mesa is already installed at the requested version (17.0.7-0ubuntu0.16.04.1)
libgles2-mesa is already installed at the requested version (17.0.7-0ubuntu0.16.04.1)
The following NEW packages will be installed:
  libgles1-mesa{b} vlc vlc-nox{a} vlc-plugin-samba{ab} 
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,037 kB of archives. After unpacking 14.5 MB will be used.
The following packages have unmet dependencies:
 vlc-plugin-samba : Depends: libvlccore8 (= 2.2.2+git20170721+r59033+56~ubuntu16.04.1) but 3.0.0~~git20160813+r65787+62~ubuntu16.04.1 is installed.
 libgles1-mesa : Depends: libglapi-mesa (= 12.0.6-0ubuntu0.16.04.1) but 17.0.7-0ubuntu0.16.04.1 is installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     libgles1-mesa [Not Installed]                      
2)     vlc [Not Installed]                                
3)     vlc-plugin-samba [Not Installed]          

```
Accepting that solution ... 

```
 Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

```
does nothing.  BTW, I did update and upgrade just prior to doing this (within the last 10 min).

OTOH, the newer HWE 4.10 kernel appears to have fixed the video playback lockups I've been experiencing for a year with the broadwell iGPU.  Usually the system would lockup after 3 min of playback regardless of the player.  Made it through a 45 min show today.

---

### Post by vasa1 on 2017-08-01
vlc still installed and working here (Kubuntu 16.04):
```
06:28 PM ~ $ acpo vlc
vlc:
  Installed: 2.2.2-5ubuntu0.16.04.3
  Candidate: 2.2.2-5ubuntu0.16.04.3
  Version table:
 *** 2.2.2-5ubuntu0.16.04.3 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     2.2.2-5 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
06:28 PM ~ $ apt policy vlc
vlc:
  Installed: 2.2.2-5ubuntu0.16.04.3
  Candidate: 2.2.2-5ubuntu0.16.04.3
  Version table:
 *** 2.2.2-5ubuntu0.16.04.3 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     2.2.2-5 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
06:29 PM ~ $ uname -a
Linux aes-Inspiron-15-3567 4.10.0-28-generic #32~16.04.2-Ubuntu SMP Thu Jul 20 10:19:48 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
06:29 PM ~ $ 

06:31 PM ~ $ apt policy libgles2-mesa
libgles2-mesa:
  Installed: 17.0.7-0ubuntu0.16.04.1
  Candidate: 17.0.7-0ubuntu0.16.04.1
  Version table:
 *** 17.0.7-0ubuntu0.16.04.1 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status                                        
     11.2.0-1ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
06:31 PM ~ $ 
```

I also have mpv working well```

06:31 PM ~ $ apt policy mpv
mpv:
  Installed: 2:0.26.0~xenial
  Candidate: 2:0.26.0~xenial
  Version table:
 *** 2:0.26.0~xenial 500
        500 http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
     0.14.0-1build1 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
06:33 PM ~ $ 
```

---

### Post by mc4man on 2017-08-01
The videolan master ppa is  garbage & should be removed. If you look you'll see it's just doing failed builds daily for Months & Months now.
So for anyone using in their sources, -  remove the ppa, purge vlc-data, update sources & then install vlc.

---

### Post by TheFu on 2017-08-01
Golf clap!  Thanks mc4man!  Solved for me.
```

ii  vlc    2.2.2-5ubuntu0.16.04.3   amd64  multimedia player and streamer
```

I
a) purged all vlc-* and vlc - that removed about 8 packages.
b) removed the videolan PPAs from the sources.d/
c) updated
d) installed vlc

Hope this helped the OP too.

---

### Post by mc4man on 2017-08-01
> **offir said:**
> I did not understand
How do i install vlc ?
Please post results of,
```
apt-cache policy vlc libvlccore*
```

---

### Post by offir on 2017-08-02
> 
Please post results of,

```

apt-cache policy vlc libvlccore*
```




```
vlc:
  Installed: (none)
  Candidate: 2.2.2+git20170721+r59033+56~ubuntu16.04.1
  Version table:
     2.2.2+git20170721+r59033+56~ubuntu16.04.1 500
        500 http://ppa.launchpad.net/videolan/stable-daily/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
     2.2.2-5ubuntu0.16.04.3 500
        500 http://il.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
     2.2.2-5 500
        500 http://il.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
libvlccore-dev:
  Installed: (none)
  Candidate: 2.2.2+git20170721+r59033+56~ubuntu16.04.1
  Version table:
     2.2.2+git20170721+r59033+56~ubuntu16.04.1 500
        500 http://ppa.launchpad.net/videolan/stable-daily/ubuntu xenial/main amd64 Packages
     2.2.2-5ubuntu0.16.04.3 500
        500 http://il.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
     2.2.2-5 500
        500 http://il.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
libvlccore8:
  Installed: 2.2.2+git20170721+r59033+56~ubuntu16.04.1
  Candidate: 2.2.2+git20170721+r59033+56~ubuntu16.04.1
  Version table:
 *** 2.2.2+git20170721+r59033+56~ubuntu16.04.1 500
        500 http://ppa.launchpad.net/videolan/stable-daily/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
     2.2.2-5ubuntu0.16.04.3 500
        500 http://il.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
     2.2.2-5 500
        500 http://il.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages

```

---

### Post by vasa1 on 2017-08-02
> **mc4man said:**
> The videolan master ppa is  garbage & should be removed. If you look you'll see it's just doing failed builds daily for Months & Months now.
So for anyone using in their sources, -  remove the ppa, purge vlc-data, update sources & then install vlc.

@offir, did you do ^^^?

Please post```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
```so that people know which ppas you have.

---

### Post by mc4man on 2017-08-02
You are using the vlc stable ppa. While it gets successful builds they haven't altered it's build deps to remove GLESv1

So remove the ppa, purge vlc-data, re-install the Ubuntu package (removing vlc-data will remove all other vlc packages..
From cli for all
```
sudo add-apt-repository -r  ppa:videolan/stable-daily
```
```
sudo apt purge vlc-data
```
```
sudo apt update && sudo apt install vlc
```

---

### Post by offir on 2017-08-02
> @offir, did you do ^^^?

Please post

```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

so that people know which ppas you have. 

```
/etc/apt/sources.list:deb http://il.archive.ubuntu.com/ubuntu/ xenial main restricted
/etc/apt/sources.list:deb http://il.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
/etc/apt/sources.list:deb http://il.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://il.archive.ubuntu.com/ubuntu/ xenial-updates universe
/etc/apt/sources.list:deb http://il.archive.ubuntu.com/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb http://il.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
/etc/apt/sources.list:deb http://il.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu xenial partner
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security multiverse
/etc/apt/sources.list.d/dansmith-ubuntu-chirp-snapshots-xenial.list:deb http://ppa.launchpad.net/dansmith/chirp-snapshots/ubuntu xenial main
/etc/apt/sources.list.d/dansmith-ubuntu-chirp-snapshots-xenial.list.save:deb http://ppa.launchpad.net/dansmith/chirp-snapshots/ubuntu xenial main
/etc/apt/sources.list.d/getdeb.list:deb http://archive.getdeb.net/ubuntu xenial-getdeb apps
/etc/apt/sources.list.d/getdeb.list:deb http://archive.getdeb.net/ubuntu xenial-getdeb games
/etc/apt/sources.list.d/getdeb.list.save:deb http://archive.getdeb.net/ubuntu xenial-getdeb apps
/etc/apt/sources.list.d/getdeb.list.save:deb http://archive.getdeb.net/ubuntu xenial-getdeb games
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/skype-stable.list:deb [arch=amd64] https://repo.skype.com/deb stable main
/etc/apt/sources.list.d/skype-stable.list.save:deb [arch=amd64] https://repo.skype.com/deb stable main

```


Some of these ppa are not enabled because they are causing problems in the updates
Anyway thank you
It works now




> You are using the vlc stable ppa. While it gets successful builds they haven't altered it's build deps to remove GLESv1

So remove the ppa, purge vlc-data, re-install the Ubuntu package (removing vlc-data will remove all other vlc packages..
From cli for all


```
sudo add-apt-repository -r  ppa:videolan/stable-daily
```


```
sudo apt purge vlc-data
```

```

sudo apt update && sudo apt install vlc
```



Thanks
it worked

---

