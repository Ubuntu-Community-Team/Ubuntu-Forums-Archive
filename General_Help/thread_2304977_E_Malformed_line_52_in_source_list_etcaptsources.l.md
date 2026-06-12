---
title: "E: Malformed line 52 in source list /etc/apt/sources.list (dist parse) E: The list of"
date: 2015-12-01
forum: General Help
---

### Post by Mahmut_Can_Senyurt on 2015-12-01
When I try to open the update manager I am getting the following error message; E: Malformed line 52 in source list /etc/apt/sources.list (dist parse) E: The list of sources could not be read.

My problem started when I was trying to install Skype. I am using Ubuntu 14.04 and I would really appreciate any help on how to deal with this problem since I can not solve it.

I am an absolute beginner of Ubuntu. However, I checked the forum for a similar problem and saw that two commands need to be executed;

Here is what I get when I execute ```
cat -n /etc/apt/sources.list
```

     1    
     2    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     3    # newer versions of the distribution.
     4    deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty main restricted
     5    deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty universe restricted multiverse main #Added by software-properties
     6    
     7    ## Major bug fix updates produced after the final release of the
     8    ## distribution.
     9    deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    10    deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates universe restricted multiverse main #Added by software-properties
    11    
    12    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    13    ## team. Also, please note that software in universe WILL NOT receive any
    14    ## review or updates from the Ubuntu security team.
    15    deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty universe
    16    deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates universe
    17    
    18    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    19    ## team, and may not be under a free licence. Please satisfy yourself as to
    20    ## your rights to use the software. Also, please note that software in
    21    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    22    ## security team.
    23    deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty multiverse
    24    deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    25    
    26    ## N.B. software from this repository may not have been tested as
    27    ## extensively as that contained in the main release, although it includes
    28    ## newer versions of some applications which may provide useful features.
    29    ## Also, please note that software in backports WILL NOT receive any review
    30    ## or updates from the Ubuntu security team.
    31    deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    32    deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse #Added by software-properties
    33    
    34    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    35    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe restricted multiverse main #Added by software-properties
    36    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    37    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    38    
    39    ## This software is not part of Ubuntu, but is offered by Canonical and the
    40    ## respective vendors as a service to Ubuntu users.
    41    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    42    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    43    
    44    ## Uncomment the following two lines to add software from Ubuntu's
    45    ## 'extras' repository.
    46    ## This software is not part of Ubuntu, but is offered by third-party
    47    ## developers who want to ship their latest software.
    48    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    49    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    50    
    51    
    52    deb [http://archive.canonical.com/](http://archive.canonical.com/) partner
    53    # deb-src [http://archive.canonical.com/](http://archive.canonical.com/) partner
    54    deb [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
    55    deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
    56    # deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
    57    deb [http://www.tolaris.com/apt/](http://www.tolaris.com/apt/) trusty main
    58    deb-src [http://www.tolaris.com/apt/](http://www.tolaris.com/apt/) trusty main
    59    deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-proposed restricted multiverse main universe
    60    deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-proposed restricted multiverse main universe #Added by software-properties

And When I execute ```
sudo apt-get -f install
``` I get the following output

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apt-clone archdetect-deb autogen binutils-mingw-w64-i686
  binutils-mingw-w64-x86-64 dmraid firefox-locale-en firefox-locale-fr
  g++-mingw-w64 g++-mingw-w64-i686 g++-mingw-w64-x86-64 gcc-mingw-w64
  gcc-mingw-w64-base gcc-mingw-w64-i686 gcc-mingw-w64-x86-64
  gfortran-mingw-w64 gfortran-mingw-w64-i686 gfortran-mingw-w64-x86-64
  gir1.2-json-1.0 gir1.2-timezonemap-1.0 gir1.2-xkl-1.0 gnat-mingw-w64
  gnat-mingw-w64-base gnat-mingw-w64-i686 gnat-mingw-w64-x86-64 kpartx
  kpartx-boot libdevmapper-event1.02.1 libdmraid1.0.0.rc16 libopts25
  libopts25-dev lvm2 mingw-w64 mingw-w64-common mingw-w64-i686-dev
  mingw-w64-x86-64-dev python3-icu python3-pam quilt rdate watershed
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 662 not upgraded.

Thank you so much in advance for any help!

Can

---

### Post by Bashing-om on 2015-12-01
Mahmut_Can_Senyurt; Hello; Yeah,

Line 52 is malformed, there is no field specified for the release .
Mine:
```

deb http://archive.canonical.com/ubuntu trusty partner

```
Where my release is trusty.

Once the edit is made ( you did make a back up of the file 1st, right ?) .. and the new file is saved:
```

sudo apt update 
sudo apt upgrade
sudo apt full-upgrade

```

Do those " and 662 not upgraded.' now get installed ?

[INDENT][INDENT]computers
[INDENT][INDENT][INDENT]literally, only do as told
 [/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2015-12-01
Edit the file using the nano text editor.
```
sudo nano /etc/apt/sources.list
```
delete lines 52 and 53.
CTRL+x to save and exit.

Thanks to mc4man for extra nano instruction below!

Then try again. Use '**sudo apt update && sudo apt upgrade**' to test if you have correctly edited the file.
If not, please post the entire output here.

Do NOT use 'sudo apt-get install -f' unless you understand what you are instructing the system to do. It won't solve your problem, which is not related to missing dependencies. Using random powerful commands is an easy way to break your system horribly. These magic incantaions *work*.

You seem to have 662 packages not upgraded. That's a bigger problem. You should upgrade them.

---

### Post by mc4man on 2015-12-01
> **ian-weisser said:**
> Edit the file using the nano text editor.
```
sudo nano /etc/apt/sources.list
```
delete lines 52 and 53.
CTRL+X to save and exit.


Seeing as though the Op is " an absolute beginner of Ubuntu" a more extensive instruc. on nano

Use the arrow keys to navigate cursor, backspace to remove characters
After finishing edit >
ctrl+o  
press enter key
ctrl+x

ctrl+o > writes out your changes
enter > completes the writeout
ctrl+x > exits nano

Nano lists actions at bottom of terminal, ^ means ctrl key

If uncomfortable with nano then use gedit as root as  such 
```
sudo -H gedit /etc/apt/sources.list
```

---

### Post by Mahmut_Can_Senyurt on 2015-12-05
Hello again!

First of all, thank you very much for your quick and extremely helpful views on the matter. I believe my problem is solved thanks to your help.

 I first deleted the two problematic lines (52-53) and then I executed the three commands suggested by Bashing-om. Now, when I executed ```
sudo apt full-upgrade
``` I had the following messages;

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  apt-clone archdetect-deb autogen binutils-mingw-w64-i686
  binutils-mingw-w64-x86-64 dmraid firefox-locale-en firefox-locale-fr
  g++-mingw-w64 g++-mingw-w64-i686 g++-mingw-w64-x86-64 gcc-mingw-w64
  gcc-mingw-w64-base gcc-mingw-w64-i686 gcc-mingw-w64-x86-64
  gfortran-mingw-w64 gfortran-mingw-w64-i686 gfortran-mingw-w64-x86-64
  gir1.2-json-1.0 gir1.2-timezonemap-1.0 gir1.2-xkl-1.0 gnat-mingw-w64
  gnat-mingw-w64-base gnat-mingw-w64-i686 gnat-mingw-w64-x86-64 kpartx
  kpartx-boot libdevmapper-event1.02.1 libdmraid1.0.0.rc16 libopts25
  libopts25-dev lvm2 mingw-w64 mingw-w64-common mingw-w64-i686-dev
  mingw-w64-x86-64-dev python3-icu python3-pam quilt rdate watershed
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Do you think I did the correct thing? And does this mean that I upgraded 662 packages?

Once again, thank you so much for the answers!

---

### Post by Bashing-om on 2015-12-05
Mahmut_Can_Senyurt; Yepper .

You did right - somewhat . I do not advocate doing without the partner repo myself . Never can tell if/when one might want software released from "partners" .

As to present:
```

The following packages were automatically installed and are no longer required:

```
Is what the package manager 'thinks' . Generally if the package management system is totally consistent, it is right.
I prefer a clean system, and I would adhere to the advise.
```

sudo apt-get autoremove

```

Per this line:
> 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

you are presently up-2-date, so yeah those 662 packages have been upgraded.

[INDENT][INDENT]your system. your call
[INDENT][INDENT][INDENT]we can not tell you how to administer your system
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

