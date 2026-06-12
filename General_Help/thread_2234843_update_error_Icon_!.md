---
title: "update error Icon /!\"
date: 2014-07-17
forum: General Help
---

### Post by Bob_Ross on 2014-07-17
Ubuntu 14.04 64 LTS

I'm getting the red /_!_\ at the top telling me my update information is outdated or unable to connect
and to run update manually.

When I run it manually through the drop down or even run from terminal sudo apt-get update it goes along fine and I get these errors at the bottom.

W: Failed to fetch [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

When I run sudo apt-get purge -s gwibber I get

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'gwibber' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

When I run locate gwibber

/etc/apt/sources.list.d/gwibber-daily-ppa-trusty.list
/etc/apt/sources.list.d/gwibber-daily-ppa-trusty.list.save
/etc/apt/trusted.gpg.d/gwibber-daily-ppa.gpg
/etc/apt/trusted.gpg.d/gwibber-daily-ppa.gpg~
/usr/share/software-center/softwarecenter/gwibber_helper.py
/usr/share/software-center/softwarecenter/gwibber_helper.pyc
/usr/share/unity/icons/lens-nav-gwibber.svg

I also tried

sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean

and ran sudo apt-get update again but still get the same errors.

Even checked software center and gwibber is not in there either.

Why is update trying to update something I don't have installed?

Thanks
Bob

---

### Post by Bashing-om on 2014-07-17
Bob_Ross; Hi ! Welcome to the forum.

The 3rd party "gwibber" has no support for 14.04
see from your web browser address bar:
[http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/)
there is no listing for trusty.
So, what is required is to remove the source for that PPA.
This fetch is located in either "/etc/apt/sources.list" OR in the directory "/etc/apt/sources.list.d".
To look:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
Once the fetch is disabled/removed then if so desired you may remove the application from the system.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Bob_Ross on 2014-07-17
Thanks for your reply.

Here is what I go when I ran your commands. Do I just delete the gwibber files?

```

sudo cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted
     2    deb http://archive.ubuntu.com/ubuntu trusty main restricted
     3    deb http://security.ubuntu.com/ubuntu/ trusty-security main restricted
     4    deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted
     5    
     6    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     7    # newer versions of the distribution.
     8    deb-src http://archive.ubuntu.com/ubuntu trusty main restricted
     9    
    10    ## Major bug fix updates produced after the final release of the
    11    ## distribution.
    12    deb-src http://archive.ubuntu.com/ubuntu trusty-updates main restricted
    13    
    14    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    15    ## team. Also, please note that software in universe WILL NOT receive any
    16    ## review or updates from the Ubuntu security team.
    17    deb http://archive.ubuntu.com/ubuntu trusty universe
    18    deb-src http://archive.ubuntu.com/ubuntu trusty universe
    19    deb http://archive.ubuntu.com/ubuntu trusty-updates universe
    20    deb-src http://archive.ubuntu.com/ubuntu trusty-updates universe
    21    
    22    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    23    ## team, and may not be under a free licence. Please satisfy yourself as to 
    24    ## your rights to use the software. Also, please note that software in 
    25    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    26    ## security team.
    27    deb http://archive.ubuntu.com/ubuntu trusty multiverse
    28    deb-src http://archive.ubuntu.com/ubuntu trusty multiverse
    29    deb http://archive.ubuntu.com/ubuntu trusty-updates multiverse
    30    deb-src http://archive.ubuntu.com/ubuntu trusty-updates multiverse
    31    
    32    ## N.B. software from this repository may not have been tested as
    33    ## extensively as that contained in the main release, although it includes
    34    ## newer versions of some applications which may provide useful features.
    35    ## Also, please note that software in backports WILL NOT receive any review
    36    ## or updates from the Ubuntu security team.
    37    deb http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse
    38    deb-src http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse
    39    
    40    deb http://archive.ubuntu.com/ubuntu trusty-security main restricted
    41    deb-src http://archive.ubuntu.com/ubuntu trusty-security main restricted
    42    deb http://archive.ubuntu.com/ubuntu trusty-security universe
    43    deb-src http://archive.ubuntu.com/ubuntu trusty-security universe
    44    deb http://archive.ubuntu.com/ubuntu trusty-security multiverse
    45    deb-src http://archive.ubuntu.com/ubuntu trusty-security multiverse
    46    
    47    ## Uncomment the following two lines to add software from Canonical's
    48    ## 'partner' repository.
    49    ## This software is not part of Ubuntu, but is offered by Canonical and the
    50    ## respective vendors as a service to Ubuntu users.
    51    # deb http://archive.canonical.com/ubuntu trusty partner
    52    # deb-src http://archive.canonical.com/ubuntu trusty partner
    53    
    54    ## This software is not part of Ubuntu, but is offered by third-party
    55    ## developers who want to ship their latest software.
    56    deb http://extras.ubuntu.com/ubuntu trusty main
    57    deb-src http://extras.ubuntu.com/ubuntu trusty main


```

and

```

sudo tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/chris-lea-node_js-trusty.list <==
deb http://ppa.launchpad.net/chris-lea/node.js/ubuntu trusty main
# deb-src http://ppa.launchpad.net/chris-lea/node.js/ubuntu trusty main

==> /etc/apt/sources.list.d/chris-lea-node_js-trusty.list.save <==
deb http://ppa.launchpad.net/chris-lea/node.js/ubuntu trusty main
# deb-src http://ppa.launchpad.net/chris-lea/node.js/ubuntu trusty main

==> /etc/apt/sources.list.d/gns3-ppa-trusty.list <==
deb http://ppa.launchpad.net/gns3/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gns3/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/gns3-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/gns3/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gns3/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/gwibber-daily-ppa-trusty.list <==
deb http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/gwibber-daily-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/langdalepl-gvfs-mtp-trusty.list <==
deb http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu trusty main
# deb-src http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu trusty main

==> /etc/apt/sources.list.d/langdalepl-gvfs-mtp-trusty.list.save <==
deb http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu trusty main
# deb-src http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu trusty main

==> /etc/apt/sources.list.d/nvbn-rm-ppa-trusty.list <==
deb http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/nvbn-rm-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu trusty main


```

Bob

---

### Post by Bob_Ross on 2014-07-17
I did mention and showed, gwibber is not installed on my system but somethign is telling update it is.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'gwibber' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

Then these files are on my system

locate gwibber

/etc/apt/sources.list.d/gwibber-daily-ppa-trusty.list
/etc/apt/sources.list.d/gwibber-daily-ppa-trusty.list.save
/etc/apt/trusted.gpg.d/gwibber-daily-ppa.gpg
/etc/apt/trusted.gpg.d/gwibber-daily-ppa.gpg~
/usr/share/software-center/softwarecenter/gwibber_helper.py
/usr/share/software-center/softwarecenter/gwibber_helper.pyc
/usr/share/unity/icons/lens-nav-gwibber.svg

---

### Post by Bashing-om on 2014-07-17
Bob_Ross;

It is like unto this:
With this fetch in the directory "/etc/apt/sources.list.d" 
```

/etc/apt/sources.list.d/gwibber-daily-ppa-trusty.list

```
active, then each time you update the system, then there is also an attempt to update 'gwibber'.
Also need to deal with the backup too.
> 
/etc/apt/sources.list.d/gwibber-daily-ppa-trusty.list.save

as that application is in the software repository, you might try "ppa-purge" To revert the package to standard;
Then remove those fetch lines so the package manager no longer tries to update the application
and finally remove it from the system with 'apt-get remove .

[INDENT][INDENT]just my thoughts
[/INDENT][/INDENT]'

---

### Post by Bob_Ross on 2014-07-17
I'm having a hard time understanding how your trying to tell me to get this out of my system.

Can you please give me some command lines that need to be run to do this?

I've never used gwibber, 14.04 install was not an upgrade it was a clean install.
I never upgrade versions, I always install clean and only LTS versions. No in between
upgrades.

sudo ppa-purge doesn't work.

How do I get this out of my system if it's not installed

When I run sudo apt-get purge -s gwibber I get

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'gwibber' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

Do I just delete the following files?

locate gwibber

/etc/apt/sources.list.d/gwibber-daily-ppa-trusty.list
/etc/apt/sources.list.d/gwibber-daily-ppa-trusty.list.save
/etc/apt/trusted.gpg.d/gwibber-daily-ppa.gpg
/etc/apt/trusted.gpg.d/gwibber-daily-ppa.gpg~
/usr/share/software-center/softwarecenter/gwibber_helper.py
/usr/share/software-center/softwarecenter/gwibber_helper.pyc
/usr/share/unity/icons/lens-nav-gwibber.sv

---

### Post by Bob_Ross on 2014-07-17
I just moved the 4 files causing the 404 out of the directory and everything seems to be fine.

Thanks

---

### Post by oldos2er on 2014-07-17
Can you please post all the terminal output from the ppa-purge command? We need to see why it's not working.

---

### Post by Bob_Ross on 2014-07-17
I tried it a couple different ways, what should the proper way to run the purge be?

I'm getting from all the ways I tried.

E: Invalid operation ppa-purge

---

### Post by Bob_Ross on 2014-07-17
I also tried

sudo apt-get purge -s ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'ppa-purge' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.

---

### Post by Bashing-om on 2014-07-17
Bob_Ross; Oh Boy,

Maybe good.
As that fetch did exist in the 3rd party directory, you must have in some shape - fashion - form have chosen to install it.
The proper method to remove it is to first do the "ppa-purge" routine to revert it to what is in the repository.

May I suggest at this time to see what the status of the package manager is ?
what returns from terminal commands:
```

sudo apt-get -f install
sudo dpkg -C

```
It may well be that all is in good shape, but as I do not run a standard install
```

sysop@1404mini:~$ apt-cache policy gwibber
gwibber:
  Installed: (none)
  Candidate: 3.7.0bzr13.04.05-0ubuntu1
  Version table:
     3.7.0bzr13.04.05-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
sysop@1404mini:~$

```
I can not verify at this time, but, I am concerned that "gwibber" is a necessary component in a standard install.

At a later time I will boot up a standard 14.04 and have a looksee .

[INDENT]anything worth doing is worth
[INDENT][INDENT][INDENT]doing right
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bob_Ross on 2014-07-17
```

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.

```

The followinf gave nothing.

```

sudo dpkg -C

```

---

### Post by Bashing-om on 2014-07-17
Bob_Ross; Sheesshh,

I am playing catch-up, did not notice all the responses prior.
OK, currently, as you have manually removed files, then "ppa-purge" no longer applies - we may have a tough row to hoe;
And we have:
> 
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.

Let's see what happens:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

[INDENT][INDENT]fingers crossed
[/INDENT][/INDENT]

---

### Post by Bob_Ross on 2014-07-17
I ran update after moving the files it did fine. Ran again. Did fine.

```

sudo apt-get update
Fetched 1,661 kB in 26s (62.6 kB/s)
Reading package lists... Done

```

A few errors at the bottom.

```

sudo apt-get upgrade
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base libmysqlclient18:i386 libnautilus-extension1a
  libunity-core-6.0-9 mysql-common nautilus nautilus-data unity unity-services
  unity-settings-daemon
13 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,017 kB of archives.
After this operation, 2,016 kB disk space will be freed.
Get:1 http://security.ubuntu.com/ubuntu/ trusty-security/main mysql-common all 5.5.38-0ubuntu0.14.04.1 [14.1 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty-updates/main language-pack-en all 1:14.04+20140707 [1,826 B]
Get:3 http://security.ubuntu.com/ubuntu/ trusty-security/main libmysqlclient18 i386 5.5.38-0ubuntu0.14.04.1 [592 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ trusty-updates/main language-pack-en-base all 1:14.04+20140707 [457 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty-updates/main language-pack-gnome-en all 1:14.04+20140707 [1,848 B]
Get:6 http://archive.ubuntu.com/ubuntu/ trusty-updates/main language-pack-gnome-en-base all 1:14.04+20140707 [948 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libnautilus-extension1a amd64 1:3.10.1-0ubuntu9.2 [52.3 kB]
Get:8 http://archive.ubuntu.com/ubuntu/ trusty-updates/main nautilus-data all 1:3.10.1-0ubuntu9.2 [50.9 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ trusty-updates/main unity-settings-daemon amd64 14.04.0+14.04.20140606-0ubuntu1 [489 kB]
Get:10 http://archive.ubuntu.com/ubuntu/ trusty-updates/main unity amd64 7.2.1+14.04.20140513-0ubuntu2 [1,452 kB]
Get:11 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libunity-core-6.0-9 amd64 7.2.1+14.04.20140513-0ubuntu2 [447 kB]
Get:12 http://archive.ubuntu.com/ubuntu/ trusty-updates/main unity-services amd64 7.2.1+14.04.20140513-0ubuntu2 [29.6 kB]
Get:13 http://archive.ubuntu.com/ubuntu/ trusty-updates/main nautilus amd64 1:3.10.1-0ubuntu9.2 [481 kB]
Fetched 5,017 kB in 5s (870 kB/s)  
(Reading database ... 319754 files and directories currently installed.)
Preparing to unpack .../language-pack-en_1%3a14.04+20140707_all.deb ...
Unpacking language-pack-en (1:14.04+20140707) over (1:14.04+20140522) ...
Preparing to unpack .../language-pack-en-base_1%3a14.04+20140707_all.deb ...
Unpacking language-pack-en-base (1:14.04+20140707) over (1:14.04+20140410) ...
Preparing to unpack .../language-pack-gnome-en_1%3a14.04+20140707_all.deb ...
Unpacking language-pack-gnome-en (1:14.04+20140707) over (1:14.04+20140522) ...
Preparing to unpack .../language-pack-gnome-en-base_1%3a14.04+20140707_all.deb ...
Unpacking language-pack-gnome-en-base (1:14.04+20140707) over (1:14.04+20140410) ...
Preparing to unpack .../mysql-common_5.5.38-0ubuntu0.14.04.1_all.deb ...
Unpacking mysql-common (5.5.38-0ubuntu0.14.04.1) over (5.5.37-0ubuntu0.14.04.1) ...
Preparing to unpack .../libmysqlclient18_5.5.38-0ubuntu0.14.04.1_i386.deb ...
Unpacking libmysqlclient18:i386 (5.5.38-0ubuntu0.14.04.1) over (5.5.37-0ubuntu0.14.04.1) ...
Preparing to unpack .../libnautilus-extension1a_1%3a3.10.1-0ubuntu9.2_amd64.deb ...
Unpacking libnautilus-extension1a (1:3.10.1-0ubuntu9.2) over (1:3.10.1-0ubuntu9.1) ...
Preparing to unpack .../nautilus-data_1%3a3.10.1-0ubuntu9.2_all.deb ...
Unpacking nautilus-data (1:3.10.1-0ubuntu9.2) over (1:3.10.1-0ubuntu9.1) ...
Preparing to unpack .../unity-settings-daemon_14.04.0+14.04.20140606-0ubuntu1_amd64.deb ...
Unpacking unity-settings-daemon (14.04.0+14.04.20140606-0ubuntu1) over (14.04.0+14.04.20140414-0ubuntu1) ...
Preparing to unpack .../unity_7.2.1+14.04.20140513-0ubuntu2_amd64.deb ...
Unpacking unity (7.2.1+14.04.20140513-0ubuntu2) over (7.2.0+14.04.20140423-0ubuntu1.2) ...
Preparing to unpack .../libunity-core-6.0-9_7.2.1+14.04.20140513-0ubuntu2_amd64.deb ...
Unpacking libunity-core-6.0-9 (7.2.1+14.04.20140513-0ubuntu2) over (7.2.0+14.04.20140423-0ubuntu1.2) ...
Preparing to unpack .../unity-services_7.2.1+14.04.20140513-0ubuntu2_amd64.deb ...
Unpacking unity-services (7.2.1+14.04.20140513-0ubuntu2) over (7.2.0+14.04.20140423-0ubuntu1.2) ...
Preparing to unpack .../nautilus_1%3a3.10.1-0ubuntu9.2_amd64.deb ...
Unpacking nautilus (1:3.10.1-0ubuntu9.2) over (1:3.10.1-0ubuntu9.1) ...
Processing triggers for software-center (13.10-0ubuntu4.1) ...
INFO:softwarecenter.db.update:no translation information in database needed
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for libglib2.0-0:i386 (2.40.0-2) ...
Processing triggers for libglib2.0-0:amd64 (2.40.0-2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up mysql-common (5.5.38-0ubuntu0.14.04.1) ...
Setting up libmysqlclient18:i386 (5.5.38-0ubuntu0.14.04.1) ...
Setting up libnautilus-extension1a (1:3.10.1-0ubuntu9.2) ...
Setting up nautilus-data (1:3.10.1-0ubuntu9.2) ...
Setting up unity-settings-daemon (14.04.0+14.04.20140606-0ubuntu1) ...
Setting up unity-services (7.2.1+14.04.20140513-0ubuntu2) ...
Setting up libunity-core-6.0-9 (7.2.1+14.04.20140513-0ubuntu2) ...
Setting up unity (7.2.1+14.04.20140513-0ubuntu2) ...
Setting up nautilus (1:3.10.1-0ubuntu9.2) ...
Setting up language-pack-en (1:14.04+20140707) ...
Setting up language-pack-en-base (1:14.04+20140707) ...
Generating locales...
  en_AG.UTF-8... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZM.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
Setting up language-pack-gnome-en (1:14.04+20140707) ...
Setting up language-pack-gnome-en-base (1:14.04+20140707) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...

```

Clean

```

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Bashing-om on 2014-07-17
Bob_Ross; Hey !

I agree, looks like you are in good shape.

If there is nothing else on this matter:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

'til we meet again
[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT]

---

### Post by Bob_Ross on 2014-07-17
Funny how moving those 4 files out of the list.

I'm wondering where they came from in the first place.

I was trying to find solved. Were is it located?

---

### Post by Bob_Ross on 2014-07-17
Found it.

---

### Post by Bashing-om on 2014-07-17
Bob_Ross; Hey,

No way to tell how they originated from this perspective.
But all is well that ends well.

To mark as solved:  top of thread -> thread tools 

[INDENT][INDENT]good things can happen
[/INDENT][/INDENT]

---

