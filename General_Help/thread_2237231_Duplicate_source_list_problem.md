---
title: "Duplicate source list problem"
date: 2014-07-31
forum: General Help
---

### Post by Reding on 2014-07-31
Hi all,

I've managed to delete a lot of duplicate sources i had before, but 2 lines are still fighting against it... See below.

```
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-backports/multiverse amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-backports/multiverse i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-backports_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-security/restricted amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-security/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages)
```

I even tried with Yppa manager, but nothing seems to be able to solve the problem

Thanks in advance

Red

---

### Post by Bashing-om on 2014-07-31
Reding; Hi !

Two places those fetches exist; the  "/etc/apt/sources.list" file and the 3rd party directory "/etc/apt/sources.list.d".
Show us what you have and we will see what we can find:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
Then is but a simple matter of an edit (SOP -> make a backup prior to editing any file for any reason, Murphy's law also applies to your computer).

[INDENT][INDENT]to see
[INDENT][INDENT][INDENT]what is to be seen
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Reding on 2014-07-31
Here we go mate.

```
1    # deb cdrom:[Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/ trusty main multiverse restricted universe
     2    # deb cdrom:[Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/ trusty main multiverse restricted universe
     3    # deb cdrom:[Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/ trusty main multiverse restricted universe
     4    
     5    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     6    # newer versions of the distribution.
     7    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted
     8    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main restricted
     9    
    10    ## Major bug fix updates produced after the final release of the
    11    ## distribution.
    12    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted
    13    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted
    14    
    15    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    16    ## team. Also, please note that software in universe WILL NOT receive any
    17    ## review or updates from the Ubuntu security team.
    18    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
    19    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty universe
    20    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates universe
    21    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates universe
    22    
    23    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    24    ## team, and may not be under a free licence. Please satisfy yourself as to 
    25    ## your rights to use the software. Also, please note that software in 
    26    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    27    ## security team.
    28    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty multiverse
    29    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty multiverse
    30    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates multiverse
    31    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates multiverse
    32    
    33    ## N.B. software from this repository may not have been tested as
    34    ## extensively as that contained in the main release, although it includes
    35    ## newer versions of some applications which may provide useful features.
    36    ## Also, please note that software in backports WILL NOT receive any review
    37    ## or updates from the Ubuntu security team.
    38    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse
    39    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse
    40    
    41    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted
    42    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security main restricted
    43    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe
    44    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security universe
    45    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security multiverse
    46    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security multiverse
    47    
    48    ## Uncomment the following two lines to add software from Canonical's
    49    ## 'partner' repository.
    50    ## This software is not part of Ubuntu, but is offered by Canonical and the
    51    ## respective vendors as a service to Ubuntu users.
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    56    
    57    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
    58    # newer versions of the distribution.
    59    
    60    ## Major bug fix updates produced after the final release of the
    61    ## distribution.
    62    
    63    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    64    ## team. Also, please note that software in universe WILL NOT receive any
    65    ## review or updates from the Ubuntu security team.
    66    
    67    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    68    ## team, and may not be under a free licence. Please satisfy yourself as to 
    69    ## your rights to use the software. Also, please note that software in 
    70    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    71    ## security team.
    72    
    73    ## N.B. software from this repository may not have been tested as
    74    ## extensively as that contained in the main release, although it includes
    75    ## newer versions of some applications which may provide useful features.
    76    ## Also, please note that software in backports WILL NOT receive any review
    77    ## or updates from the Ubuntu security team.
    78    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports multiverse
    79    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports multiverse
    80    
    81    
    82    ## Uncomment the following two lines to add software from Canonical's
    83    ## 'partner' repository.
    84    ## This software is not part of Ubuntu, but is offered by Canonical and the
    85    ## respective vendors as a service to Ubuntu users.
    86    
    87    ## This software is not part of Ubuntu, but is offered by third-party
    88    ## developers who want to ship their latest software.
    89    
    90    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
    91    # newer versions of the distribution.
    92    
    93    ## Major bug fix updates produced after the final release of the
    94    ## distribution.
    95    
    96    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    97    ## team. Also, please note that software in universe WILL NOT receive any
    98    ## review or updates from the Ubuntu security team.
    99    
   100    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
   101    ## team, and may not be under a free licence. Please satisfy yourself as to 
   102    ## your rights to use the software. Also, please note that software in 
   103    ## multiverse WILL NOT receive any review or updates from the Ubuntu
   104    ## security team.
   105    
   106    ## N.B. software from this repository may not have been tested as
   107    ## extensively as that contained in the main release, although it includes
   108    ## newer versions of some applications which may provide useful features.
   109    ## Also, please note that software in backports WILL NOT receive any review
   110    ## or updates from the Ubuntu security team.
   111    
   112    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security restricted
   113    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-security restricted
   114    
   115    ## Uncomment the following two lines to add software from Canonical's
   116    ## 'partner' repository.
   117    ## This software is not part of Ubuntu, but is offered by Canonical and the
   118    ## respective vendors as a service to Ubuntu users.
   119    
   120    ## This software is not part of Ubuntu, but is offered by third-party
   121    ## developers who want to ship their latest software.
   122    
   123    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
   124    # newer versions of the distribution.
   125    
   126    ## Major bug fix updates produced after the final release of the
   127    ## distribution.
   128    
   129    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
   130    ## team. Also, please note that software in universe WILL NOT receive any
   131    ## review or updates from the Ubuntu security team.
   132    
   133    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
   134    ## team, and may not be under a free licence. Please satisfy yourself as to 
   135    ## your rights to use the software. Also, please note that software in 
   136    ## multiverse WILL NOT receive any review or updates from the Ubuntu
   137    ## security team.
   138    
   139    ## N.B. software from this repository may not have been tested as
   140    ## extensively as that contained in the main release, although it includes
   141    ## newer versions of some applications which may provide useful features.
   142    ## Also, please note that software in backports WILL NOT receive any review
   143    ## or updates from the Ubuntu security team.
   144    
   145    
   146    ## Uncomment the following two lines to add software from Canonical's
   147    ## 'partner' repository.
   148    ## This software is not part of Ubuntu, but is offered by Canonical and the
   149    ## respective vendors as a service to Ubuntu users.
   150    
   151    ## This software is not part of Ubuntu, but is offered by third-party
   152    ## developers who want to ship their latest software.
```
```

red@ZaReason:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/canonical_partner.list <==
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

==> /etc/apt/sources.list.d/canonical_partner.list.save <==
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

==> /etc/apt/sources.list.d/chris-lea-node_js-trusty.list <==
deb [http://ppa.launchpad.net/chris-lea/node.js/ubuntu](http://ppa.launchpad.net/chris-lea/node.js/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/chris-lea/node.js/ubuntu](http://ppa.launchpad.net/chris-lea/node.js/ubuntu) trusty main

==> /etc/apt/sources.list.d/chris-lea-node_js-trusty.list.save <==
deb [http://ppa.launchpad.net/chris-lea/node.js/ubuntu](http://ppa.launchpad.net/chris-lea/node.js/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/chris-lea/node.js/ubuntu](http://ppa.launchpad.net/chris-lea/node.js/ubuntu) trusty main

==> /etc/apt/sources.list.d/docky-core-stable-trusty.list.save <==

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.

==> /etc/apt/sources.list.d/google.list <==
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

==> /etc/apt/sources.list.d/google.list.save <==
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

==> /etc/apt/sources.list.d/happy-neko-ps3mediaserver-trusty.list.save <==

==> /etc/apt/sources.list.d/intellinuxgraphics.list <==
deb [https://download.01.org/gfx/ubuntu/14.04/main](https://download.01.org/gfx/ubuntu/14.04/main) trusty main #Intel Graphics drivers

==> /etc/apt/sources.list.d/intellinuxgraphics.list.save <==
deb [https://download.01.org/gfx/ubuntu/14.04/main](https://download.01.org/gfx/ubuntu/14.04/main) trusty main #Intel Graphics drivers

==> /etc/apt/sources.list.d/jfi-ppa-trusty.list <==
deb [http://ppa.launchpad.net/jfi/ppa/ubuntu](http://ppa.launchpad.net/jfi/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/jfi/ppa/ubuntu](http://ppa.launchpad.net/jfi/ppa/ubuntu) trusty main

==> /etc/apt/sources.list.d/jfi-ppa-trusty.list.save <==
deb [http://ppa.launchpad.net/jfi/ppa/ubuntu](http://ppa.launchpad.net/jfi/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/jfi/ppa/ubuntu](http://ppa.launchpad.net/jfi/ppa/ubuntu) trusty main

==> /etc/apt/sources.list.d/lestcape-cinnamon-trusty.list.save <==

==> /etc/apt/sources.list.d/linrunner-tlp-trusty.list.save <==

==> /etc/apt/sources.list.d/noobslab-apps-trusty.list <==

==> /etc/apt/sources.list.d/noobslab-apps-trusty.list.save <==

==> /etc/apt/sources.list.d/noobslab-icons-trusty.list.save <==

==> /etc/apt/sources.list.d/ozcanesen-terra-terminal-trusty.list.save <==

==> /etc/apt/sources.list.d/pulb-mailnag-trusty.list.save <==

==> /etc/apt/sources.list.d/ravefinity-project-ppa-trusty.list <==
deb [http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu](http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu) trusty main

==> /etc/apt/sources.list.d/ravefinity-project-ppa-trusty.list.save <==
deb [http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu](http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu) trusty main

==> /etc/apt/sources.list.d/satyajit-happy-themes-trusty.list.save <==

==> /etc/apt/sources.list.d/shimmerproject-ppa-trusty.list.save <==

==> /etc/apt/sources.list.d/tiheum-equinox-trusty.list <==
deb [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) trusty main

==> /etc/apt/sources.list.d/tiheum-equinox-trusty.list.save <==
deb [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) trusty main

==> /etc/apt/sources.list.d/webupd8team-java-trusty.list <==
deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main

==> /etc/apt/sources.list.d/webupd8team-java-trusty.list.save <==
deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) trusty main

==> /etc/apt/sources.list.d/webupd8team-y-ppa-manager-trusty.list <==
deb [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu](http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu) trusty main
```

---

### Post by Bashing-om on 2014-07-31
Reding; Yep,

Got it :
> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe [color=red]multiverse[/color]
    39    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports main restricted universe multiverse
##as opposed to:
78    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports [color=red]multiverse[/color]
    79    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-backports multiverse

I do suggest ya remove lines 78 and 79, then re-run the update/upgrade routine and see what the status is then.

[INDENT][INDENT]one thing at a time kinda guy
[/INDENT][/INDENT]

---

### Post by Reding on 2014-08-01
I can't find it in the software center under "Software sources" ...

How can I remove it manually from the terminal ? 

Red :)

---

### Post by plucky on 2014-08-01
> **Reding said:**
> I can't find it in the software center under "Software sources" ...

How can I remove it manually from the terminal ? 

Red :)

```
gksu gedit /etc/apt/sources.list
```

and put a # in front of ```
78 deb http://archive.ubuntu.com/ubuntu trusty-backports multiverse
79 deb-src http://archive.ubuntu.com/ubuntu trusty-backports multiverse 
```

so it looks like ```

78 # deb http://archive.ubuntu.com/ubuntu trusty-backports multiverse
79 # deb-src http://archive.ubuntu.com/ubuntu trusty-backports multiverse
```

The line numbers might not be visible.

Good Luck

---

### Post by Reding on 2014-08-01
To change in gedit is enough right ?

Thanks ;)

---

### Post by Bashing-om on 2014-08-01
Reding; Hi !

Yep, that will do the job.
Make a backup of the current file, just in case of any thing happening:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-orig
gksu gedit /etc/apt/sources.list

```
Make the edits as plucky advises. save the file and exit back to terminal.
In terminal once more now do the update/upgrade:
```

sudo apt-get update
sudo apt-get upgrade

```
Now advise us of the results .

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by Reding on 2014-08-01
It solved the problem !

Thanks a lot mate

---

### Post by Bashing-om on 2014-08-01
Reding; Good deal !

Pleased ya up and smoothly running,

Please mark this thread solved; 
aides others seeking the solution, 
helps keep the forum clean and 
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]and just
[INDENT][INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

