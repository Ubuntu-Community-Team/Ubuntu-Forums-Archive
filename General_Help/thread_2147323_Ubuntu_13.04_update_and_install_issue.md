---
title: "Ubuntu 13.04 update and install issue"
date: 2013-05-21
forum: General Help
---

### Post by hobgoblinn on 2013-05-21
Hi, I've checked several forums and sites for trying to fix this issue.  This issue has been happening for the last five days. I'm a bit of a  newbie to Linux but I think I've managed to narrow down where the issue  is. 

  I've recently been getting an error like this ```
E: GPG error: http://arcgive.canonical.com raring Release: The following signatures were invalid: NODATA 1 NODATA 2
``` every time with "*sudo apt-get update*". Also been getting a  red warning triangle warning me update information is outdated and may  be caused by network issues or outdated repository then says to click "*show updates*" then a few seconds later a message pops up saying the machine is up to date. After some intense  google searching a few people have had a similar issue but it seemed to  be with 13.03. From what I gather, I am missing GPG keys that is causing the issue  (tried resetting them to default in the settings but no luck). There was  a link to what appeared to be the PGP key for raring Release but I  can't make heads or tails of what to do with it: [http://archive.canonical.com/dists/raring/Release.gpg](http://archive.canonical.com/dists/raring/Release.gpg)
    
I am not using a proxy which has been known to cause an issue, I've tried changing mirrors and selecting the best one from other and I've tried the "*sudo apt-get clean*" "*sudo apt-get update*" but still no luck with the issue. Here is the output from "*sudo apt-get update*": 

```
Get:1 http://ppa.launchpad.net raring Release.gpg [316 B]
Hit http://archive.canonical.com oneiric Release.gpg                           
Get:2 http://arcgive.canonical.com raring Release.gpg                          
Get:3 http://ppa.launchpad.net raring Release [9,739 B]                        
Hit http://archive.canonical.com oneiric Release                               
Get:4 http://archive.ubuntu.com raring Release.gpg [933 B]                     
Get:5 http://archive.ubuntu.com raring-updates Release.gpg [933 B]             
Get:6 http://archive.canonical.com oneiric/partner Sources [2,656 B]           
Get:7 http://ppa.launchpad.net raring/main Sources [11.9 kB]                   
Get:8 http://packages.medibuntu.org maverick Release.gpg [198 B]               
Get:9 http://arcgive.canonical.com raring Release                              
Ign http://arcgive.canonical.com raring Release                                
E: GPG error: http://arcgive.canonical.com raring Release: The following signatures were invalid: NODATA 1 NODATA 2
```

I am really hoping someone here may know what to do. 

Thank you for your help and if there is anything other info you need to resolve this issue, let me know.

---

### Post by papibe on 2013-05-21
Hi hobgoblinn.

Could you post the output of this command?
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Regards.

---

### Post by hobgoblinn on 2013-05-21
Thank you for the speedy responce, here is the output: 

```
/etc/apt/sources.list.d/webupd8team-java-precise.list

     1    # deb http://ppa.launchpad.net/webupd8team/java/ubuntu quantal main # disabled on upgrade to quantal
     2    # deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu quantal main # disabled on upgrade to quantal

/etc/apt/sources.list.d/yannubuntu-boot-repair-precise.list

     1    # deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu quantal main # disabled on upgrade to quantal
     2    # deb-src http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu quantal main # disabled on upgrade to quantal

/etc/apt/sources.list.d/stretch-bitcoin-precise.list

     1    # deb http://ppa.launchpad.net/stretch/bitcoin/ubuntu quantal main # disabled on upgrade to quantal
     2    # deb-src http://ppa.launchpad.net/stretch/bitcoin/ubuntu quantal main # disabled on upgrade to quantal

/etc/apt/sources.list.d/medibuntu.list

     1    deb http://packages.medibuntu.org/ maverick free non-free

/etc/apt/sources.list.d/nilarimogard-webupd8-raring.list

     1    deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu raring main
     2    deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu raring main

/etc/apt/sources.list.d/bitcoin-bitcoin-precise.list

     1    # deb http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu quantal main # disabled on upgrade to quantal
     2    # deb-src http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu quantal main # disabled on upgrade to quantal

/etc/apt/sources.list

     1    # deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://archive.ubuntu.com/ubuntu raring main restricted multiverse universe
     6    
     7    ## Major bug fix updates produced after the final release of the
     8    ## distribution.
     9    deb http://archive.ubuntu.com/ubuntu raring-updates main restricted multiverse universe
    10    
    11    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    12    ## team. Also, please note that software in universe WILL NOT receive any
    13    ## review or updates from the Ubuntu security team.
    14    
    15    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    16    ## team, and may not be under a free licence. Please satisfy yourself as to 
    17    ## your rights to use the software. Also, please note that software in 
    18    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    19    ## security team.
    20    
    21    ## N.B. software from this repository may not have been tested as
    22    ## extensively as that contained in the main release, although it includes
    23    ## newer versions of some applications which may provide useful features.
    24    ## Also, please note that software in backports WILL NOT receive any review
    25    ## or updates from the Ubuntu security team.
    26    deb http://archive.ubuntu.com/ubuntu raring-backports main restricted multiverse universe
    27    
    28    deb http://archive.ubuntu.com/ubuntu raring-security main restricted multiverse universe
    29    
    30    ## Uncomment the following two lines to add software from Canonical's
    31    ## 'partner' repository.
    32    ## This software is not part of Ubuntu, but is offered by Canonical and the
    33    ## respective vendors as a service to Ubuntu users.
    34    deb http://archive.canonical.com/ubuntu oneiric partner
    35    deb-src http://archive.canonical.com/ubuntu oneiric partner
    36    
    37    ## This software is not part of Ubuntu, but is offered by third-party
    38    ## developers who want to ship their latest software.
    39    deb http://extras.ubuntu.com/ubuntu raring main
    40    deb-src http://extras.ubuntu.com/ubuntu raring main
    41    deb http://arcgive.canonical.com/ raring partner
    42    deb-src http://arcgive.canonical.com/ raring partner
    43    deb http://archive.ubuntu.com/ubuntu raring-proposed multiverse restricted universe main


```

---

### Post by papibe on 2013-05-21
Thanks.

It seems to be a typo on the repository pointing to the source code of  archive.ubuntu.com/ubuntu.

This
```
deb-src http://**arc[COLOR="#FF0000"]g[/COLOR]ive**.canonical.com/ raring partner
```
should be:
```
deb-src http://**arc[COLOR="#FF0000"]h[/COLOR]ive**.canonical.com/ raring partner
```
To change that run an editor as root:
```
gksudo gedit /etc/apt/sources.list
```
and carefully edit the line as it should be. After that update your sources.

Let us know how it goes.
Regards.

---

### Post by hobgoblinn on 2013-05-21
Awesome! Can't thank you enough, the issue is now fixed and able to update and install as normal. Out of interest, what would cause it to change the links like that? 

This can now be marked as solved and hopefully others with the same issue can now resolve it

---

### Post by papibe on 2013-05-21
Glad it is fixed now :)
> **hobgoblinn said:**
> Out of interest, what would cause it to change the links like that?
I checked my 13.04 machine and it is not a widespread error. Did you ever edited that file? 
> **hobgoblinn said:**
> This can now be marked as solved and hopefully others with the same issue can now resolve it
You can do it yourself. [Here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how to do it.

Regards.

---

