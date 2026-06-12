---
title: "Skype errors during install"
date: 2013-09-28
forum: General Help
---

### Post by chrtylee on 2013-09-28
W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages)  404  Not Found [IP: 24.143.206.170 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.


i tried doing a terminal install, software center install and ubuntu-tweak install none will work.

---

### Post by papibe on 2013-09-28
Hi chrtylee.

Somehow your software sources have a reference to a wrong repository.

Let's fix your software sources, and then install skype.

Could you open a terminal, run this command and post back its results?
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Regards.

---

### Post by chrtylee on 2013-09-28
i already got it by downloading the .deb right from skype site, but will do this anyway to fix problem for future

```
 /etc/apt/sources.list

     1    # deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/
     2    
     3    # deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
     4    # deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted
     5    
     6    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     7    # newer versions of the distribution.
     8    deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
     9    deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
    10    
    11    ## Major bug fix updates produced after the final release of the
    12    ## distribution.
    13    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    14    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    15    
    16    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17    ## team. Also, please note that software in universe WILL NOT receive any
    18    ## review or updates from the Ubuntu security team.
    19    deb http://us.archive.ubuntu.com/ubuntu/ precise universe
    20    deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
    21    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    22    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    23    
    24    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25    ## team, and may not be under a free licence. Please satisfy yourself as to 
    26    ## your rights to use the software. Also, please note that software in 
    27    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    28    ## security team.
    29    deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    30    deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    31    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    32    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    33    
    34    ## N.B. software from this repository may not have been tested as
    35    ## extensively as that contained in the main release, although it includes
    36    ## newer versions of some applications which may provide useful features.
    37    ## Also, please note that software in backports WILL NOT receive any review
    38    ## or updates from the Ubuntu security team.
    39    deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    40    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    41    
    42    deb http://security.ubuntu.com/ubuntu precise-security main restricted
    43    deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    44    deb http://security.ubuntu.com/ubuntu precise-security universe
    45    deb-src http://security.ubuntu.com/ubuntu precise-security universe
    46    deb http://security.ubuntu.com/ubuntu precise-security multiverse
    47    deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    48    
    49    ## Uncomment the following two lines to add software from Canonical's
    50    ## 'partner' repository.
    51    ## This software is not part of Ubuntu, but is offered by Canonical and the
    52    ## respective vendors as a service to Ubuntu users.
    53    # deb http://archive.canonical.com/ubuntu precise partner
    54    # deb-src http://archive.canonical.com/ubuntu precise partner
    55    
    56    ## This software is not part of Ubuntu, but is offered by third-party
    57    ## developers who want to ship their latest software.
    58    deb http://extras.ubuntu.com/ubuntu precise main
    59    deb-src http://extras.ubuntu.com/ubuntu precise main
    60    deb http://archive.canonical.com/ precise partner
    61    deb-src http://archive.canonical.com/ precise partner

/etc/apt/sources.list.d/skype.list

     1    # deb http://download.skype.com/linux/repos/debian/ stable non-free #Repository for Skype (stable)
     2    deb http://download.skype.com/linux/repos/debian/ stable non-free #Repository for Skype (stable)



```

```
 /etc/apt/sources.list.d/playonlinux.list

     1    deb http://deb.playonlinux.com/ precise main 
```

---

### Post by papibe on 2013-09-28
Thanks.

There's a couple of things you need to fix.

The skype/debian repository you added won't work in Ubuntu. Delete it:
```
sudo rm -rf /etc/apt/sources.list.d/skype.list
```
Then it seems that you tried to add the partner repository (where Skype resides), but you made a syntax error.

To fix it, open the sources file:
```
gksudo gedit /etc/apt/sources.list
```
Then remove the last 2 lines: line 60 and 61.

After that, uncomment line 53.

The end of the file should look like this:
```

    ...
    49	## Uncomment the following two lines to add software from Canonical's
    50	## 'partner' repository.
    51	## This software is not part of Ubuntu, but is offered by Canonical and the
    52	## respective vendors as a service to Ubuntu users.
    53	deb http://archive.canonical.com/ubuntu precise partner
    54	# deb-src http://archive.canonical.com/ubuntu precise partner
    55	
    56	## This software is not part of Ubuntu, but is offered by third-party
    57	## developers who want to ship their latest software.
    58	deb http://extras.ubuntu.com/ubuntu precise main
    59	deb-src http://extras.ubuntu.com/ubuntu precise main

```
Save the file, and close gedit.

Then update your sources:
```
sudo apt-get update
```
(You should have no errors now).

and finally, install Skype:
```
sudo apt-get install skype
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by chrtylee on 2013-09-29
well as i said i fixed by installing from skype website, is the skype from that terminal install any different or better? if not then ill just mark this as resolved

---

