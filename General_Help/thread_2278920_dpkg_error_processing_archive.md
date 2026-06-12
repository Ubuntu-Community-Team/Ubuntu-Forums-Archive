---
title: "dpkg: error processing archive"
date: 2015-05-19
forum: General Help
---

### Post by ctgcwiqc on 2015-05-19
I have tried...
apt-get update && apt-get upgrade
apt-get dist-upgrade
apt-get install -f
apt-get clean
apt-get autoremove
aptitude install redeclipse-data

All to no avail.  see output from terminal below.  Any ideas appreciated.

```
****@***********:/home/*****# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  redeclipse-data
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/781 MB of archives.
After this operation, 340 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 806515 files and directories currently installed.)
Preparing to unpack .../redeclipse-data_1.5.1-1~getdeb2_all.deb ...
Unpacking redeclipse-data (1.5.1-1~getdeb2) over (1.5.1-1~getdeb1) ...
dpkg: error processing archive /var/cache/apt/archives/redeclipse-data_1.5.1-1~getdeb2_all.deb (--unpack):
 trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse 1.5.1-1~getdeb1
Errors were encountered while processing:
 /var/cache/apt/archives/redeclipse-data_1.5.1-1~getdeb2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
root@*****:/home/*****# apt-get upgrade redeclipse-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  redeclipse-data
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 781 MB of archives.
After this operation, 340 kB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 http://archive.getdeb.net/ubuntu/ trusty-getdeb/games redeclipse-data all 1.5.1-1~getdeb2 [781 MB]
Fetched 781 MB in 18min 44s (695 kB/s)                                         
(Reading database ... 806252 files and directories currently installed.)
Preparing to unpack .../redeclipse-data_1.5.1-1~getdeb2_all.deb ...
Unpacking redeclipse-data (1.5.1-1~getdeb2) over (1.5.1-1~getdeb1) ...
dpkg: error processing archive /var/cache/apt/archives/redeclipse-data_1.5.1-1~getdeb2_all.deb (--unpack):
 trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse 1.5.1-1~getdeb1
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by ctgcwiqc on 2015-05-19
Well now after navigating I see that this is not the section to post this into.  Mod please move to the appropriate location.  Thanks.

---

### Post by papibe on 2015-05-19
Thread moved to **General Help**.

---

### Post by Bashing-om on 2015-05-19
ctgcwiqc; Hummm ...

'redeclipse' also installed from PPA such that there is a conflict ?
what returns:
```

apt-cache policy redeclipse

```

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by ctgcwiqc on 2015-05-20
```
*****@***********:~$ apt-cache policy redeclipse
redeclipse:
  Installed: 1.5.1-1~getdeb1
  Candidate: 1.5.1-1~getdeb1
  Version table:
 *** 1.5.1-1~getdeb1 0
        500 http://archive.getdeb.net/ubuntu/ trusty-getdeb/games amd64 Packages
        100 /var/lib/dpkg/status
     1.4-5 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/multiverse amd64 Packages
```

---

### Post by Bashing-om on 2015-05-20
ctgcwiqc; Yepper;

What we have here is a conflict of interest.
Is there a particular reason you installed from PPA and want to keep " archive.getdeb.net/ubuntu/ " ?

One or the other will have to be removed.


[INDENT][INDENT]there can be only one
[/INDENT][/INDENT]

---

### Post by sandyd on 2015-05-20
> **Bashing-om said:**
> ctgcwiqc; Yepper;

What we have here is a conflict of interest.
Is there a particular reason you installed from PPA and want to keep " archive.getdeb.net/ubuntu/ " ?

One or the other will have to be removed.


[INDENT][INDENT]there can be only one
[/INDENT][/INDENT]
Both versions are from getdeb:
```

redeclipse-data_1.5.1-1~getdeb2
redeclipse 1.5.1-1~getdeb1
```
so there shouldn't be a conflict

---

### Post by ctgcwiqc on 2015-05-20
I have had that PPA installed for months to get the latest update to Red Eclipse (V1.5)  The Ubuntu repositories was still at (V1.4).  This game has updated before with no problem.  I have this exact setup on 4 laptops, mine is the only one with this problem that I am aware of.  Thanks for the assistance.

---

### Post by Bashing-om on 2015-05-21
ctgcwiqc; Well ..

As I continue to think about this situation:
> 
dpkg: error processing archive /var/cache/apt/archives/redeclipse-data_1.5.1-1~getdeb2_all.deb (--unpack):
 trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse 1.5.1-1~getdeb1

bk

dpkg: error processing archive /var/cache/apt/archives/redeclipse-data_1.5.1-1~getdeb2_all.deb (--unpack):
 trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse 1.5.1-1~getdeb1

bk

1.5.1-1~getdeb1 0
        500 [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) trusty-getdeb/games amd64 Packages


As it is your expressed desire to keep the PPA version; Let's try a less invasive method to upgrade the package:
```

dpkg --remove --force-remove-reinstreq redeclipse
sudo apt-get update
apt-get install redeclipse

```
With the hope that " /var/cache/apt/archives/redeclipse-data_1.5.1-1~getdeb2" is removed from the data base;
'update' rebuilds the data base ;
and lastly that "install redeclipse" will install along with the new version of "redeclipse-data" .

[INDENT][INDENT]looks reasonable to me
[/INDENT][/INDENT]

---

### Post by ian-weisser on 2015-05-21
--force-remove-reinstreq merely deletes the package record from the dpkg database. Files not otherwise removed may be left behind to foul a later install of the upgraded package.
So look carefully at any new error messages; might simply need to delete old cruft manually.

---

### Post by ctgcwiqc on 2015-05-22
Did not work.   See output from terminal after attempting install:
```
The following packages will be upgraded:
  redeclipse-data
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0 B/781 MB of archives.
After this operation, 340 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 806254 files and directories currently installed.)
Preparing to unpack .../redeclipse-data_1.5.1-1~getdeb2_all.deb ...
Unpacking redeclipse-data (1.5.1-1~getdeb2) over (1.5.1-1~getdeb1) ...
dpkg: error processing archive /var/cache/apt/archives/redeclipse-data_1.5.1-1~getdeb2_all.deb (--unpack):
 trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse 1.5.1-1~getdeb1
Errors were encountered while processing:
 /var/cache/apt/archives/redeclipse-data_1.5.1-1~getdeb2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2015-05-23
ctgcwiqc; Hey;

Sorta stuck here as to what to do; thinking ;
Presently you have:
> 
Unpacking redeclipse-data (1.5.1-1~getdeb2)

Which must be from a PPA as what is available even in the latest ubuntu reposisitory:
> 
You have searched for packages that names contain redeclipse-data in suite(s) vivid, all sections, and all architectures. Found 1 matching packages.

Exact hits

Package redeclipse-data

vivid (games): data for the Red Eclipse FPS game [multiverse] 
1.4-3: all

where the latest version is 1.4-3 .

Will refocus my attention and see what I can come up with.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-05-23
ctgcwiqc; Still stuck;

As I can not access the server from my install:
In my browser the URL:
[http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu)
results:
> 
Not Found

The requested URL /ubuntu was not found on this server.

Apache/2.2.22 (Ubuntu) Server at archive.getdeb.net Port 80

What results when you enter this URL in your browser ? 

Maybe because:
> 
AptURL
The APT protocol, or apturl, is a very simple way to install a software package from a web browser.

the application is not installed on my system.

Insure that it is installed on yours:
```

dpkg -l apturl

```

Let's see then where we go if you can access the server.

[INDENT][INDENT]there is that path that seems right, but
[INDENT][INDENT][INDENT]leads to errors
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ctgcwiqc on 2015-05-23
I'm not sure if you are telling me to install apturl, i entered the command you provided in termial and this is the output.  Thanks for being willing to help with this.  I am lost on what to do to fix.  I am no genius, but am pretty good with goole seaches and I found nothing to help.

```
dpkg -l apturl
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                           Version              Architecture         Description
+++-==============================-====================-====================-=================================================================
ii  apturl                         0.5.2ubuntu4         amd64                install packages using the apt protocol - GTK+ frontend


```

---

### Post by Bashing-om on 2015-05-23
ctgcwiqc; Hey[

Yep 'apturl' is fully installed, so that is not a source of the issue.
I am still in a quandry, as I still have no access to the server.
Can you access from that URL above ?
As I am able to access the web site from google ( hummm) .. I am confused as to what to think.

[INDENT][INDENT]look'n for a way forward
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-05-23
ctgcwiqc; Hey; Hey !

I do I do have another thought.
Let's verify the source fetch.
As:
[http://archive.getdeb.net/getdeb/ubuntu/pool/](http://archive.getdeb.net/getdeb/ubuntu/pool/)
does resolve; let's see what is set in the sources.list(s) .
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

Maybe I have been bass-ackard, or maybe there is corruption in the control file(s) ?

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by ctgcwiqc on 2015-05-23
Not too long ago I did try to clear up some PPA that were not being used I believe.  Not too many.  I removed Grive (linux google drive sync utility) and some other items to clear up some things I no longer used.  You are probably on to something.  See terminal output below.  Thanks again.
```
cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
     6    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    11    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
    17    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
    18    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    19    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
    27    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
    28    deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    29    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    37    deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
    38    
    39    deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    40    deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
    41    deb http://security.ubuntu.com/ubuntu trusty-security universe
    42    deb-src http://security.ubuntu.com/ubuntu trusty-security universe
    43    deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    44    deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    deb http://archive.canonical.com/ubuntu trusty partner
    51    deb-src http://archive.canonical.com/ubuntu trusty partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu trusty main
    56    deb-src http://extras.ubuntu.com/ubuntu trusty main
    57    deb http://archive.getdeb.net/ubuntu trusty-getdeb games apps
    58    # deb-src http://archive.getdeb.net/ubuntu trusty-getdeb games
    59    # deb-src http://archive.getdeb.net/ubuntu trusty-getdeb apps


```
```
tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/freyja-dev-unity-tweak-tool-daily-trusty.list <==
deb http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu trusty main
# deb-src http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu trusty main

==> /etc/apt/sources.list.d/freyja-dev-unity-tweak-tool-daily-trusty.list.save <==
deb http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu trusty main
# deb-src http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu trusty main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.

==> /etc/apt/sources.list.d/google-talkplugin.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main

==> /etc/apt/sources.list.d/google-talkplugin.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main

==> /etc/apt/sources.list.d/gurqn-systray-trusty-trusty.list <==
deb http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main

==> /etc/apt/sources.list.d/gurqn-systray-trusty-trusty.list.save <==
deb http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gurqn/systray-trusty/ubuntu trusty main

==> /etc/apt/sources.list.d/libdvdcss2.list <==
deb http://download.videolan.org/pub/debian/stable/ /

==> /etc/apt/sources.list.d/libdvdcss2.list.save <==
deb http://download.videolan.org/pub/debian/stable/ /

==> /etc/apt/sources.list.d/libreoffice-ppa-trusty.list <==
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/libreoffice-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/linrunner-tlp-trusty.list <==
deb http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main
# deb-src http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main

==> /etc/apt/sources.list.d/linrunner-tlp-trusty.list.save <==
deb http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main
# deb-src http://ppa.launchpad.net/linrunner/tlp/ubuntu trusty main

==> /etc/apt/sources.list.d/peterlevi-ppa-trusty.list <==
deb http://ppa.launchpad.net/peterlevi/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/peterlevi/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/peterlevi-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/peterlevi/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/peterlevi/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/pmjdebruijn-darktable-release-trusty.list <==
deb http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu trusty main
# deb-src http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu trusty main
# deb-src http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu trusty main

==> /etc/apt/sources.list.d/pmjdebruijn-darktable-release-trusty.list.save <==
deb http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu trusty main
# deb-src http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu trusty main
# deb-src http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu trusty main

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_motorbike_ubuntu.list <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/motorbike/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_motorbike_ubuntu.list.save <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/motorbike/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_varicad-viewer_ubuntu.list <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/varicad-viewer/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_varicad-viewer_ubuntu.list.save <==
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/varicad-viewer/ubuntu trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/steam.list <==
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam

==> /etc/apt/sources.list.d/steam.list.save <==
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam

==> /etc/apt/sources.list.d/stebbins-handbrake-releases-trusty.list <==

==> /etc/apt/sources.list.d/stebbins-handbrake-releases-trusty.list.save <==

==> /etc/apt/sources.list.d/stebbins-handbrake-snapshots-trusty.list <==
deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu trusty main
# deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu trusty main

==> /etc/apt/sources.list.d/stebbins-handbrake-snapshots-trusty.list.save <==
deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu trusty main
# deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu trusty main

==> /etc/apt/sources.list.d/team-xbmc-ppa-trusty.list <==
deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/team-xbmc-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/thefanclub-grive-tools-trusty.list <==

==> /etc/apt/sources.list.d/thefanclub-grive-tools-trusty.list.save <==

==> /etc/apt/sources.list.d/thefanclub-ubuntu-after-install-trusty.list <==
deb http://ppa.launchpad.net/thefanclub/ubuntu-after-install/ubuntu trusty main
# deb-src http://ppa.launchpad.net/thefanclub/ubuntu-after-install/ubuntu trusty main

==> /etc/apt/sources.list.d/thefanclub-ubuntu-after-install-trusty.list.save <==
deb http://ppa.launchpad.net/thefanclub/ubuntu-after-install/ubuntu trusty main
# deb-src http://ppa.launchpad.net/thefanclub/ubuntu-after-install/ubuntu trusty main

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list <==
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-java-trusty.list <==
deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-java-trusty.list.save <==
deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main


```

---

### Post by Bashing-om on 2015-05-23
ctgcwiqc; Shucks;

Stuck again.
1) The server is up and running per:
[http://archive.getdeb.net/status/](http://archive.getdeb.net/status/)

2) Your source line is valid and correct per:
[http://www.getdeb.net/updates/Ubuntu/15.04#how_to_install](http://www.getdeb.net/updates/Ubuntu/15.04#how_to_install)
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) trusty-getdeb games apps

3) I find no downtime/problems reported for the web site

4) The URL does not resolve for me ( [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) )
------------------------------
Please paste :
[http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu)
into your browser and see if it resolves for you

Put back in our back pocket that:
[http://archive.getdeb.net/getdeb/ubuntu/pool/](http://archive.getdeb.net/getdeb/ubuntu/pool/)
DOES resolve.
Depending; we may play with that.

[INDENT][INDENT]I regret this happens
[INDENT][INDENT][INDENT]but here is where I learn the most
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ctgcwiqc on 2015-05-23
> Please paste :
[http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu)
into your browser and see if it resolves for you

This is what I get:
**Not Found**

 The requested URL /ubuntu was not found on this server.
 [HR][/HR] Apache/2.2.22 (Ubuntu) Server at archive.getdeb.net Port 80


> Put back in our back pocket that:
[http://archive.getdeb.net/getdeb/ubuntu/pool/](http://archive.getdeb.net/getdeb/ubuntu/pool/)
DOES resolve.
Depending; we may play with that.

This does resolve for me.  I can access this site.

---

### Post by ctgcwiqc on 2015-05-23
Also checked this.

```
:~$ aptitude why-not redeclipse-data 
Unable to find a reason to remove redeclipse-data.
:~$ aptitude why redeclipse-data 
i   redeclipse Depends redeclipse-data (>= 1.5.1)
:~$ aptitude why redeclipse
Unable to find a reason to install redeclipse.
:~$ aptitude why-not redeclipse
Unable to find a reason to remove redeclipse.


```

---

### Post by Bashing-om on 2015-05-23
ctgcwiqc; Sheesshh, OK

Your also not able to access rules out a package problem.

I continue to try and find out why we are not able to connect to the server.
I am beginning to seriously consider the server is at fault and is not reported to this time.
OR perhaps the URL is changed and I can not find an advisory too that effect.

One thing for sure, until we can access the database for getdeb.net we can not fix the installed package.


[INDENT][INDENT]sometimes
[/INDENT][/INDENT]

---

### Post by ctgcwiqc on 2015-05-23
```
   sudo dpkg --remove --force-remove-reinstreq redeclipse
 (Reading database ... 806253 files and directories currently installed.)
 Removing redeclipse (1.5.1-1~getdeb1) ...
 Processing triggers for mime-support (3.54ubuntu1.1) ...
 Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
 Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
 Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
 Rebuilding /usr/share/applications/bamf-2.index...
 Processing triggers for doc-base (0.10.5) ...
 Processing 1 removed doc-base file...
 Registering documents with scrollkeeper...
 Processing triggers for hicolor-icon-theme (0.13-1) ...
 Processing triggers for man-db (2.6.7.1-1ubuntu1) …
 
 

```

```
   apt-get upgrade
 Reading package lists... Done                                                   
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 Calculating upgrade... Done
[U][B] The following package was automatically installed and is no longer required:
   redeclipse-data[/B][/U]
 Use 'apt-get autoremove' to remove it.
 [U][B]The following packages will be upgraded:
   redeclipse-data[/B][/U]
 1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 Need to get 781 MB of archives.
 After this operation, 340 kB disk space will be freed.
 Do you want to continue? [Y/n] n
 Abort.
 root@cgultrabook:/home/clint# apt-get autoremove
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 The following packages will be REMOVED:
   redeclipse-data
 0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
 After this operation, 893 MB disk space will be freed.
 Do you want to continue? [Y/n] y
 (Reading database ... 806161 files and directories currently installed.)
 Removing redeclipse-data (1.5.1-1~getdeb1) …
```

Notice that redeclipse-data is no longer needed, as well as there is a second redeclipse-data package that is able to be updated?  Seems I had two of the same packages installed?
```
apt-cache policy redeclipse-data
redeclipse-data:
  Installed: (none)
  Candidate: 1.5.1-1~getdeb2
  Version table:
     1.5.1-1~getdeb2 0
        500 http://archive.getdeb.net/ubuntu/ trusty-getdeb/games amd64 Packages
     1.4-2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/multiverse amd64 Packages
```
It looks like there is nothing installed?  What is the problem here.  redeclipse is uninstalled.

```
   apt-cache policy redeclipse redeclipse:
   Installed: (none)
   Candidate: 1.5.1-1~getdeb1
   Version table:
      1.5.1-1~getdeb1 0
         500 http://archive.getdeb.net/ubuntu/ trusty-getdeb/games amd64 Packages
         100 /var/lib/dpkg/status
      1.4-5 0
         500 http://us.archive.ubuntu.com/ubuntu/ trusty/multiverse amd64 Packages


```

---

### Post by ctgcwiqc on 2015-05-24
This happened after removing redeclipse and redeclipse-data.

 ```
sudo apt-get -o Acquire::http::Dl-Limit=50 install redeclipse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  redeclipse-data
The following NEW packages will be installed:
  redeclipse redeclipse-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 781 MB/783 MB of archives.
After this operation, 899 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.getdeb.net/ubuntu/ trusty-getdeb/games redeclipse-data all 1.5.1-1~getdeb2 [781 MB]
Fetched 618 MB in 4h 9min 1s (41.4 kB/s)                                       
Selecting previously unselected package redeclipse-data.
(Reading database ... 801573 files and directories currently installed.)
Preparing to unpack .../redeclipse-data_1.5.1-1~getdeb2_all.deb ...
Unpacking redeclipse-data (1.5.1-1~getdeb2) ...
Selecting previously unselected package redeclipse.
Preparing to unpack .../redeclipse_1.5.1-1~getdeb1_amd64.deb ...
Unpacking redeclipse (1.5.1-1~getdeb1) ...
dpkg: error processing archive /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse-data 1.5.1-1~getdeb2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for doc-base (0.10.5) ...
Errors were encountered while processing:
 /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```


Error report console popped up but i could not copy and paste the output so i took a screenshot.  See screenshots.

[ATTACH=CONFIG]262176[/ATTACH][ATTACH=CONFIG]262177[/ATTACH][ATTACH=CONFIG]262178[/ATTACH]

---

### Post by Bashing-om on 2015-05-24
ctgcwiqc; Sheeeshh ..

I continue to struggle with this, seems now my troubleshooting procedure is invalid, even though we get a null response from the URL, sure looks like the server responds from the source file's request:
> 
 Get:1 [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) trusty-getdeb/games redeclipse-data all 1.5.1-1~[color=red]getdeb2[/color] [781 MB]


And it appears there are maybe 3 versions of redeclipse on the system :
> 
Preparing to unpack .../redeclipse-data_1.5.1-1~[color=red]getdeb2[/color]_all.deb ...
Preparing to unpack .../redeclipse_1.5.1-1~getdeb1_amd64.deb ...
Unpacking redeclipse (1.5.1-1~getdeb1) ...
dpkg: error processing archive /var/cache/apt/archives/redeclipse_1.5.1-1~[color=red]getdeb1_amd64.deb[/color] (--unpack):
 trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse-data 1.5.1-1~getdeb2

Perhaps even something installed from ubuntu's software respository.

Let's look and see what there is on the system:
```

ls -al /var/cache/apt/archives/redeclipse*
dpkg -l "redeclipse*"

```

I have in mind to remove the obsolete -getdeb1 package, and see if dpkg will install the -getdeb2 packages .
Working in other than ubuntu server is proving to be tough going -in my ineptness.

[INDENT][INDENT]But;
[INDENT][INDENT][INDENT]where there is a will there is a way  when the server is up that is
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ctgcwiqc on 2015-05-24
```
ls -al /var/cache/apt/archives/redeclipse*
```
```
-rw-r--r-- 1 root root   1850304 Apr  4 12:50 /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb
-rw-r--r-- 1 root root 780854524 Apr 25 13:51 /var/cache/apt/archives/redeclipse-data_1.5.1-1~getdeb2_all.deb
```
```
dpkg -l "redeclipse*"
```
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                           Version              Architecture         Description
+++-==============================-====================-====================-=================================================================
ic  redeclipse                     1.5.1-1~getdeb1      amd64                multiplayer FPS game based on Cube2
ii  redeclipse-data                1.5.1-1~getdeb2      all                  data for the Red Eclipse FPS game
ii  redeclipse-server              1.5.1-1~getdeb1      amd64                server for the Red Eclipse FPS game
```

---

### Post by Bashing-om on 2015-05-24
ctgcwiqc; Well, good and bad:

Good we see no ubuntu repository references for redeclipse.

Bad that the redeclipse-data file is not the same version as redeclipse .
Bad that :
> 
Preparing to unpack .../redeclipse-data_1.5.1-1~getdeb2_all.deb ...

is not present in the /var/cache/apt/archives/ ; I can not explain why it is not.

Maybe we can remove that old version that is marked 'iC' and then install the getdeb2 version properly ?

How about we try:
```

sudo apt-get remove redeclipse=1.5.1-1~getdeb1

```

If that completes with no error, try and install:
```

sudo apt-get update
sudo apt-get install redeclipse

```

[INDENT][INDENT]could be as simple and easy as that
[/INDENT][/INDENT]

---

### Post by ctgcwiqc on 2015-05-24
```
sudo apt-get remove redeclipse=1.5.1-1~getdeb1
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'redeclipse' is not installed, so not removed
The following package was automatically installed and is no longer required:
  redeclipse-data
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I ran apt-get udpate then the following
```
apt-get install redeclipse
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  redeclipse
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,850 kB of archives.
After this operation, 6,054 kB of additional disk space will be used.
(Reading database ... 806141 files and directories currently installed.)
Preparing to unpack .../redeclipse_1.5.1-1~getdeb1_amd64.deb ...
Unpacking redeclipse (1.5.1-1~getdeb1) ...
dpkg: error processing archive /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse-data 1.5.1-1~getdeb2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for doc-base (0.10.5) ...
Errors were encountered while processing:
 /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2015-05-24
ctgcwiqc; Shesshh ...

Why oh why "Package 'redeclipse' is not installed, so not removed" when "ic  redeclipse                     1.5.1-1~getdeb1ic  redeclipse                     1.5.1-1~getdeb1 " says it is installed ??? And we know that the ,deb is on the system "-rw-r--r-- 1 root root   1850304 Apr  4 12:50 /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb" .
Why oh why does the system want to download the redeclipse_1.5.1-1~getdeb1_amd64.deb .
Is it because that is what is present in /var/cache/apt/archives/ ?

I am going to getdeb's web site and verify that the file I think we want is there .

Be back soonest ,

[INDENT][INDENT]I be in that process  of learning
[/INDENT][/INDENT]

---

### Post by ctgcwiqc on 2015-05-24
* sure do thank you for all your help.  I have only had one mishap with this PPA on one of the 5 laptops i use it on.  It was because I had set it up for the wrong release, and had unmet dependencies.  My mistake, but that was fixed.  I have no clue on this issue.  I know that I removed several PPAs that were no longet used by me, but dont know how or why that may have led to this if it had anything to do with it at all.*

---

### Post by Bashing-om on 2015-05-24
ctgcwiqc; Welp;

This has not put a smile on my face - yet - But, it sure has kept me entertained .

OK; The file we want is present on the server:
[http://archive.getdeb.net/getdeb/ubuntu/pool/games/r/redeclipse/](http://archive.getdeb.net/getdeb/ubuntu/pool/games/r/redeclipse/)
This file is there !
redeclipse_1.5.1-1~getdeb2_amd64.deb
(copied from the server as verification)

So the question now is why will not the package manager get it ?

Try: - with a purge flag
```

sudo apt-get remove --purge redeclipse=1.5.1-1~getdeb1
sudo rm /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb

```

NOW what happens:
```

sudo apt-get update
sudo apt-get install redeclipse

```

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times I do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-05-24
ctgcwiqc; Hey;

Nother question - me not seeing the forest for the tree.
Why install "ii  redeclipse-server              1.5.1-1~getdeb1" ?

Is this not a conflict with the normal redeclipse installed ? Is this perhaps what is holding us to the getdeb1 version ???

[INDENT][INDENT]here, I just do not know
[/INDENT][/INDENT]

---

### Post by ctgcwiqc on 2015-05-24
```
sudo apt-get remove --purge redeclipse=1.5.1-1~getdeb1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  redeclipse-data
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  redeclipse*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 806140 files and directories currently installed.)
Removing redeclipse (1.5.1-1~getdeb1) ...
Purging configuration files for redeclipse (1.5.1-1~getdeb1) ...
```
```
sudo rm /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb
```
```
apt-get clean
```
```
apt-get autoremove
```
```
apt-get update
```
```
apt-get install redeclipse
```

The package is downloading now.  My connection is super slow right now so it will take a while to install.

redeclipse-server is installed to create LAN and internet games.  I can backup configuration settings and remove package to test if that is a problem but I dont think that is the problem.  I don't believe there are any dependencies between the two as you should be able to install redeclipse-server to a server that does not have redeclipse installed and its config still allows the server to host games.  I think that is correct but I'm not certain.

---

### Post by Bashing-om on 2015-05-24
ctgcwiqc;

Look'n promising, so far.

as to redeclipse/server, If problems continue we can look at the dependencies of each and then make a determination on updating the -server package also .

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe else
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ctgcwiqc on 2015-05-25
We still have a problem.
```
sudo apt-get -o Acquire::http::Dl-Limit=15 install redeclipse
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  redeclipse-data
The following NEW packages will be installed:
  redeclipse redeclipse-data
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 781 MB/783 MB of archives.
After this operation, 899 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.getdeb.net/ubuntu/ trusty-getdeb/games redeclipse-data all 1.5.1-1~getdeb2 [781 MB]
Get:2 http://archive.getdeb.net/ubuntu/ trusty-getdeb/games redeclipse-data all 1.5.1-1~getdeb2 [781 MB]
Fetched 577 kB in 8h 38min 29s (18 B/s)                                        
Selecting previously unselected package redeclipse-data.
(Reading database ... 801573 files and directories currently installed.)
Preparing to unpack .../redeclipse-data_1.5.1-1~getdeb2_all.deb ...
Unpacking redeclipse-data (1.5.1-1~getdeb2) ...
Selecting previously unselected package redeclipse.
Preparing to unpack .../redeclipse_1.5.1-1~getdeb1_amd64.deb ...
Unpacking redeclipse (1.5.1-1~getdeb1) ...
dpkg: error processing archive /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse-data 1.5.1-1~getdeb2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for doc-base (0.10.5) ...
Errors were encountered while processing:
 /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by Bashing-om on 2015-05-25
ctgcwiqc; Yuk !

Where in the world is :
> 
dpkg: error processing archive /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb (--unpack):

that getdeb1 package being pulled for ??? We did remove all traces of it from the system.

Let's suppose it is from the "ii redeclipse-server 1.5.1-1~getdeb1" package.

What then is it's dependencies ?
```

apt-cache depends redeclipse-server
apt-cache depends redeclipse
apt-cache depends redeclipse-data

```
And just for a reverse look up:
```

apt-cache rdepends redeclipse-server

```

And let's us also take a look at the control file(s) for the related packaging. A bit tedious  to do so in this manner, but doable.
It contains all the data dpkg requires to update and uninstall packages. 
Maybe we can get all the info we need doing a number like :
```

grep -B3 -A10 redeclipse /var/lib/dpkg/status

```

Else, well, we open the file in a text editor and go searching for the related stanzas and read what the package manager expects for each.

[INDENT][INDENT]this has got my goat and
[INDENT][INDENT][INDENT]I so want to know the why
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ctgcwiqc on 2015-05-25
```
apt-cache depends redeclipse-server
redeclipse-server
  Depends: libc6
  Depends: libenet2a
  Depends: libstdc++6
  Depends: zlib1g
  Conflicts: redeclipse-server:i386
```


I *am wondering why there is any mention of UTOPIC in the output below.  I think this may be relevant. *

```
apt-cache depends redeclipse
redeclipse
  Depends: redeclipse-data
  Depends: libc6
  Depends: libenet2a
 |Depends: libgl1-mesa-glx
    libgl1-mesa-glx-lts-**utopic**
  Depends: <libgl1>
    libgl1-mesa-glx
    libgl1-mesa-glx-lts-**utopic**
  Depends: libsdl-image1.2
  Depends: libsdl-mixer1.2
  Depends: libsdl1.2debian
  Depends: libstdc++6
  Depends: libx11-6
  Depends: zlib1g
  Conflicts: redeclipse:i386
```
```
apt-cache depends redeclipse-data
redeclipse-data
  Enhances: redeclipse-server
```
```
apt-cache rdepends redeclipse-server
redeclipse-server
Reverse Depends:
  redeclipse-server:i386
  redeclipse-server-dbg
  redeclipse-data
  redeclipse-server:i386
  redeclipse-server-dbg
  redeclipse-data
```
```
grep -B3 -A10 redeclipse /var/lib/dpkg/status
 and basic manipulation of all Vorbis I audio streams.
Original-Maintainer: Debian Xiph.org Maintainers <pkg-xiph-maint@lists.alioth.debian.org>

Package: redeclipse-server
Status: install ok installed
Priority: optional
Section: games
Installed-Size: 1474
Maintainer: GetDeb Package Ninjas <package.ninjas@getdeb.net>
Architecture: amd64
Source: redeclipse
Version: 1.5.1-1~getdeb1
Depends: libc6 (>= 2.15), libenet2a (>= 1.3.10+ds), libstdc++6 (>= 4.1.1), zlib1g (>= 1:1.1.4)
Description: server for the Red Eclipse FPS game
 This package contains the dedicated server for the Red Eclipse FPS game, it
 also includes some example scripts for configuring the server. It contains no
 init integration.
Homepage: http://www.redeclipse.net

Package: gettext-base
Status: install ok installed
Priority: standard
Section: utils
Installed-Size: 344
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: gettext
Version: 0.18.3.1-1ubuntu3
--
  - Dial on demand.
Original-Maintainer: John Hasler <jhasler@debian.org>

Package: redeclipse
Status: install ok not-installed
Priority: optional
Section: games
Architecture: amd64

Package: landscape-client-ui-install
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 92
--
Homepage: http://www.info-zip.org/UnZip.html
Original-Maintainer: Santiago Vila <sanvila@debian.org>

Package: redeclipse-data
Status: install ok installed
Priority: optional
Section: games
Installed-Size: 871809
Maintainer: GetDeb Package Ninjas <package.ninjas@getdeb.net>
Architecture: all
Version: 1.5.1-1~getdeb2
Enhances: redeclipse-server
Description: data for the Red Eclipse FPS game
 This package contains the data content, e.g. maps, models, textures, sounds,
 etc. for the Red Eclipse FPS game.
Homepage: http://www.redeclipse.net

Package: ubuntu-mono
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 4133
Maintainer: Ubuntu Artwork Team <ubuntu-art@lists.ubuntu.com>
Architecture: all
Source: ubuntu-themes
Version: 14.04+14.04.20140410-0ubuntu1


```

---

### Post by ctgcwiqc on 2015-05-25
So getdeb2 is not for my release 14.04....Why is it trying to install that version?

Packages are available for the following releases:
Ubuntu 15.04: 1.5.1-1~getdeb3~vivid
Ubuntu 14.04: 1.5.1-1~getdeb1
Ubuntu 12.04: 1.4-1~getdeb1
Ubuntu 14.10: 1.5.1-1~getdeb2~utopic
Ubuntu 12.10: 1.4-1~getdeb1

source: [http://www.playdeb.net/game/Red%20Eclipse](http://www.playdeb.net/game/Red%20Eclipse)

---

### Post by Bashing-om on 2015-05-25
ctgcwiqc; Sheeshh ; I still do not get it ->

And I am still stuck:
> 
apt-cache depends redeclipse ->> Depends: redeclipse-data
bk
Package: redeclipse-data ->> Version: 1.5.1-1~getdeb2


Now we know that "redeclipse-data Version: 1.5.1-1~getdeb2" is fully installed, and as it is a dependency of "redeclipse";
We want to install the corresponding version of redeclipse to that of the installed -data -getdeb2. And it will not install !
Each time we purge the getdeb1 version of 'redeclipse' and try and re-install, the old incompatible version getdeb.1 is fetched.

I do not perceive a conflict with  "redeclipse-server 1.5.1-1~getdeb1 " being installed.

>  
Preparing to unpack .../redeclipse-data_1.5.1-1~getdeb2_all.deb ...
Unpacking redeclipse-data (1.5.1-1~getdeb2) ...
Selecting previously unselected package redeclipse.
[color=red]Preparing to unpack .../redeclipse_1.5.1-1~getdeb1_amd64.deb ...[/color]
Unpacking redeclipse (1.5.1-1~getdeb1) ...
dpkg: error processing archive /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse-data 1.5.1-1~getdeb2


We have inconclusive data in '/var/cache/apt/archives/redeclipse' to point us in a direction forward.

As I am stuck, and sick of dithering about, I am going to go ask for help.

-----------------------------------
Your last post showing the getdeb1 is the proper version:
Pops to mind this in in relation to opt in for HardWare Enablement stack; and there is no way back short of a system (RE-)install.
HWE: -> show
```

uname -r
ls -al /usr/bin/hwe-support-status
hwe-support-status --verbose
hwe-support-status --show-all-unsupported

```

Yeah, HWE may well explain what is going on here !

[INDENT][INDENT]judgement reserved; pending ^
[/INDENT][/INDENT]

---

### Post by ctgcwiqc on 2015-05-25
What I'm saying is package manager should NOT be installing getdeb2.  That is for Utopic Ubuntu 14.10.  I should only receive getdeb1.  I am about to post the output from the previously requested commands.

---

### Post by ctgcwiqc on 2015-05-25
```
uname -r
3.13.0-53-generic
```
```
ls -al /usr/bin/hwe-support-status
ls: cannot access /usr/bin/hwe-support-status: No such file or directory
```
```
hwe-support-status --verbose
hwe-support-status: command not found
```
```
hwe-support-status --show-all-unsupported
hwe-support-status: command not found
```

---

### Post by Bashing-om on 2015-05-25
ctgcwiqc; Agreed,


I do not see HWE as a factor - whewwhh ! -
We should have getdeb1 .
So why is the version for redeclipse-data installed at getdeb2 ?

Maybe we can purge redeclipse-data, and see if the 1 version of redeclipse  installs ?
But that too begs the question as to why "redeclipse-data Version: 1.5.1-1~getdeb2 " got installed ??

[INDENT][INDENT]maybe then ?
[/INDENT][/INDENT]

---

### Post by ctgcwiqc on 2015-05-25
I got bored and:
removed redeclipse, redeclipse-server & redeclipse-data
removed getdeb repositories from sources
rebooted
verified redeclipse & redeclipse-data version 1.4.5 available in software center without getdeb repo added
added getdeb repo back to sources list
checked versions and the available redeclipse is 1.5.1.1~getdeb1 however the redeclipse-data is 1.5.1.1~getdeb2 for some reason.  I'm lost.  This is not a super pressing matter for me as it is just a video game that I seldom play.  It is just pretty frustrating.

---

### Post by Bashing-om on 2015-05-25
ctgcwiqc; yukkie Poo ;


Back to chasing my tail, and banging my head against the stone wall of redeclipse:
see:
[http://www.ubuntuupdates.org/package/getdeb_games/trusty/games/getdeb/redeclipse-data](http://www.ubuntuupdates.org/package/getdeb_games/trusty/games/getdeb/redeclipse-data)
Yikes ! That do say that for redeclipse-data, the correct version is getdeb2 ! HUH ?? Now that makes no common sense to me as we are also advised that the correct version for redeclipse is getdeb1 ... but but but .


this is old info from older package, but we can extrapolate to the current:
[http://mirrors.sunsite.dk/getdeb/ubuntu/dists/precise-getdeb-testing/games/binary-amd64/Packages](http://mirrors.sunsite.dk/getdeb/ubuntu/dists/precise-getdeb-testing/games/binary-amd64/Packages)
> 
Package: redeclipse
Version: 1.4-1~getdeb1
Architecture: amd64
Maintainer: GetDeb Package Ninjas <package.ninjas@getdeb.net>
Installed-Size: 4561
Depends: redeclipse-data (>= 1.4), libc6 (>= blah blah blah

The version of redeclipse matches that of the redeclipse-data version !! 
-------------------

That to me means we are back to finding a way to verify what the correct version is and what the dependencies are !
I am going to continue beating my Head.
We could take the easier approach, and just ask - be nicer if we do our homework 1st . There does exist a help desk and as well a forum !

If nothing else good
[INDENT][INDENT]I do learn from this experience (what just yet remains to be seen)
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-05-25
ctgcwiqc; Welp;

I am convinced:
My suppositions must not be valid: per
[http://www.ubuntuupdates.org/package/getdeb_games/trusty/games/getdeb/redeclipse](http://www.ubuntuupdates.org/package/getdeb_games/trusty/games/getdeb/redeclipse)
> 
Name:	redeclipse
Latest version:	1.5.1-1~getdeb1
Release:	trusty (14.04)
Level:	getdeb
Repository:	games


And per:
[http://www.ubuntuupdates.org/package/getdeb_games/trusty/games/getdeb/redeclipse-data](http://www.ubuntuupdates.org/package/getdeb_games/trusty/games/getdeb/redeclipse-data)
> 
Name:	redeclipse-data
Latest version:	1.5.1-1~getdeb2
Release:	trusty (14.04)
Level:	getdeb
Repository:	games


So now that you have (RE-)installed all 'redeclipses'; what now is the new status ?
Did it install, does the game run ?

[INDENT][INDENT]ain't no quit
[/INDENT][/INDENT]

---

### Post by ctgcwiqc on 2015-05-25
It failed to install with the same error.  I checked another laptop that has the same setup as this one.  Both redeclipse and redeclipse-data are 1.5.1.1~getdeb1?  There are no updates available.  I will try to reinstall and post the output.

---

### Post by Bashing-om on 2015-05-25
ctgcwiqc; Presently;

I know of no better way forward.

I hate though that you loose all the game data, and this means starting all over again .
```

apt-get remove --purge redeclipse redeclipse-data redeclipse-server

```


Slowly in stages:
```

sudo apt-get update
sudo apt-get install redeclipse

``` Now as 'redeclipse-data' is a dependency of 'redeclipe' (and also the -server) 
Did installing redeclipse also install that dependent package 'redeclipse-data' ?
CHECK !
```

dpkg -l redeclipse-data

```

Depending that output we may next install 'redeclipse-data' and IF that goes well ->
```

sudo apt-get install redeclipse-server

```

Maybe the 3rd time will be the charm

---

### Post by ctgcwiqc on 2015-05-27
I believe a yucky poo is in order here?

```
apt-get remove --purge redeclipse redeclipse-data redeclipse-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'redeclipse' is not installed, so not removed
Package 'redeclipse-data' is not installed, so not removed
Package 'redeclipse-server' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

```
apt-get install redeclipse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libenet2a redeclipse-data
The following NEW packages will be installed:
  libenet2a redeclipse redeclipse-data
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 781 MB/783 MB of archives.
After this operation, 899 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.getdeb.net/ubuntu/ trusty-getdeb/games redeclipse-data all 1.5.1-1~getdeb2 [781 MB]
Fetched 754 MB in 14min 2s (895 kB/s)                                          
Selecting previously unselected package libenet2a:amd64.
(Reading database ... 801558 files and directories currently installed.)
Preparing to unpack .../libenet2a_1.3.11+ds-1_amd64.deb ...
Unpacking libenet2a:amd64 (1.3.11+ds-1) ...
Selecting previously unselected package redeclipse-data.
Preparing to unpack .../redeclipse-data_1.5.1-1~getdeb2_all.deb ...
Unpacking redeclipse-data (1.5.1-1~getdeb2) ...
Preparing to unpack .../redeclipse_1.5.1-1~getdeb1_amd64.deb ...
Unpacking redeclipse (1.5.1-1~getdeb1) ...
dpkg: error processing archive /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse-data 1.5.1-1~getdeb2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for doc-base (0.10.5) ...
Errors were encountered while processing:
 /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
```
dpkg -l redeclipse
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                           Version              Architecture         Description
+++-==============================-====================-====================-=================================================================
in  redeclipse                     <none>               amd64                (no description available)


```
```
dpkg -l redeclipse-data
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                           Version              Architecture         Description
+++-==============================-====================-====================-=================================================================
iU  redeclipse-data                1.5.1-1~getdeb2      all                  data for the Red Eclipse FPS game


```
```
dpkg -l redeclipse-server
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                           Version              Architecture         Description
+++-==============================-====================-====================-=================================================================
un  redeclipse-server              <none>               <none>               (no description available)


```

---

### Post by Bashing-om on 2015-05-27
ctgcwiqc; Yeah, yukkie Poo is right.

I am beginning to think what we have here is a fault in the install scripts. And if confirmed we need to have a talk with the PPA maintenance people.
We purged everything related. On this 1st attempt to reinstall 'redeclipse' we get an error:
> 
apt-get install redeclipse ->> The following extra packages will be installed: libenet2a [color=red]redeclipse-data[/color] ->> The following NEW packages will be installed:  libenet2a redeclipse [color=red]redeclipse-data[/color] ->> Unpacking redeclipse (1.5.1-1~getdeb1) ...->> dpkg: error processing archive /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb (--unpack): ->> trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse-data 1.5.1-1~getdeb2 // dpkg-deb: error: subprocess paste was killed by signal [color=red](Broken pipe)[/color]


I have in mind to bring in our guru of package management to assist in isolating that bad script. Then we go talk to the people of the PPA archive.getdeb.net  with our findings.

[INDENT][INDENT]but before I make a further fool of myself, I would like confirmation that 
[INDENT][INDENT][INDENT]I am not being foolish
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ctgcwiqc on 2015-05-27
Thanks.  Patiently waiting.  I'm still curious why this has only affected 1 out of 5 laptops that I have set up the exact same way.

---

### Post by ian-weisser on 2015-05-27
```

dpkg: error processing archive /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse-data 1.5.1-1~getdeb2

```

I think this is the cruft in my Post #10 warning.
The conflicting package was deleted from the database, *but some files were left in place*.  --force-remove-reinstreq does that.

Delete the conflicting file (/usr/share/games/redeclipse/config/fonts/play.cfg) manually, or use dpkg's --force-conflicts flag to overwrite the conflicting cruft.

---

### Post by ctgcwiqc on 2015-05-28
I couldn't figure out how to get the --force-conflicts flag to work.  I will purge force whatever I need to do.  The problem continues to to be I think it is trying to install the wrong package.  I think it should be redeclipse-data~getdeb1 but it is trying to install redeclipse-data~getdeb1.

---

### Post by matt_symes on 2015-05-28
Hi

> **ian-weisser said:**
> ```

dpkg: error processing archive /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse-data 1.5.1-1~getdeb2

```

I think this is the cruft in my Post #10 warning.
The conflicting package was deleted from the database, *but some files were left in place*.  --force-remove-reinstreq does that.

Delete the conflicting file (/usr/share/games/redeclipse/config/fonts/play.cfg) manually, or use dpkg's --force-conflicts flag to overwrite the conflicting cruft.

^^^ This. (or --force-overwrite may also work)

I have not read all this thread as life's too short but the fix for post #1 was a one line dpkg command.

Kind regards

---

### Post by ak399g on 2015-05-28
> **ctgcwiqc said:**
> [post #47; fresh install + errors]

New player of redeclipse, can confirm this error occurs on Xubuntu 14.04 (3.13.0-53-generic amd64)

> **ian-weisser said:**
> [post #50; delete/ignore conflicts]

Not entirely sure how that's done. I did try

```

$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb
(Reading database ... 648671 files and directories currently installed.)
Preparing to unpack .../redeclipse_1.5.1-1~getdeb1_amd64.deb ...
Unpacking redeclipse (1.5.1-1~getdeb1) ...
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse-data 1.5.1-1~getdeb2
Setting up redeclipse (1.5.1-1~getdeb1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for doc-base (0.10.5) ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...

```

and then install redeclipse, but all the fonts became screwed up.

[http://i.imgur.com/KMOy7jH.png](http://i.imgur.com/KMOy7jH.png)

EDIT: ```
apt-get -o Dpkg::Options::="--force-overwrite" install
``` had the same effect

The error is clearly there for a reason. My only guess is the package maintainers moved fonts from redeclipse to redeclipse-data and didn't check for conflicts. Until it's fixed in the repo, we'll have to find a way to do it manually.

---

### Post by ctgcwiqc on 2015-05-28
> the fix for post #1 was a one line dpkg command.

I've tried several one line dpkg commands.  None have worked yet.  I have manually deleted the conflicting file.  I attempted the --force-conflicts flag but I guess you didn't read much, just posted an irrelevant condescending comment.  Not everyone is a software engineer, computer programmer, hacker, scripter, apt guru.  Some people just like to use computers.  I shouldn't have to know how to rebuild an engine to drive a car.  

If you read this you will see that the package will not install, and even if it does install, per the getdeb site it is the wrong package for my release 14.04.  the correct package should be redeclipse-data~getdeb1 but apt-get install redeclipse returns with redeclipse-data~getdeb2 which is for a different release.  If you have something productive to add please reply.

---

### Post by matt_symes on 2015-05-28
Hi

No problem. 

I was going to read through all the thread tonight when i have more time but now, somehow, I can't seem to find the time.

Kind regards

---

### Post by ak399g on 2015-05-28
[http://www.ubuntuupdates.org/pm/redeclipse](http://www.ubuntuupdates.org/pm/redeclipse)
[http://www.ubuntuupdates.org/pm/redeclipse-data](http://www.ubuntuupdates.org/pm/redeclipse-data)
The package maintainers assign redeclipse getdeb1 and redeclipse-data getdeb2  to 14.04. Perhaps download/install the .deb for redeclipse-data getdeb1 (utopic) and install it without adding the full repo? I just don't think you'll be able to use the repos through apt until they fix it on their end.

---

### Post by ian-weisser on 2015-05-28
> **ctgcwiqc said:**
>   Not everyone is a software engineer, computer programmer, hacker, scripter, apt guru.  Some people just like to use computers.  I shouldn't have to know how to rebuild an engine to drive a car.  

We all understand your frustration. Been there, too. It stinks.
Please understand that *we didn't cause the problem.* Bashing-om's patience and ak399g's research have revealed that problem is not with Ubuntu, nor apt, nor dpkg.

You installed non-Ubuntu software from a non-Ubuntu repository that figuratively broke your car engine.
If you want to drive the car, you can either learn to rebuild the engine...or live without the non-Ubuntu software

Let us know if you wish to keep or dump the software, and we will try to guide you.
Keeping might get a bit technical. Might not. I suspect ak399g's approach might be practical. Done a few that way myself.

---

### Post by Bashing-om on 2015-05-28
Et all; Difficult response;

I do appreciate all the effort from all who are assisting in finding resolution. Coming to my aid in my time of need.
As it is my failure to properly read apt's responses that has led to this state of confusion.

It is our goal to (RE-)install an application; preferably  through the software management system.
I do suggest we backup and reqroup and SEE what the fault is prior to placing blame on the PPA maintainers.

How about we purge all instances of 'redeclipse' then see if the file that the the package manager is having a fit about still is on the system ?
If " /usr/share/games/redeclipse/config/fonts/play.cfg" exists then manually remove it:
```

sudo rm /usr/share/games/redeclipse/config/fonts/play.cfg

```
should suffice in this instance.
If there is then a problem getting 'redeclipse' to install .. well we go looking at /var/lib/apt/lists/redeclipse structure and see what is to be installed, and go round and round as to what actually gets removed in the purge operation that hinders a re-install.

Finding the fault (if any) will benefit all who want to install redeclipse.

[INDENT][INDENT]that is my story and I am sticking to it
[/INDENT][/INDENT]

---

### Post by ak399g on 2015-05-28
Can be installed properly with:
[http://www.ubuntuupdates.org/package/getdeb_games/trusty/games/getdeb/redeclipse](http://www.ubuntuupdates.org/package/getdeb_games/trusty/games/getdeb/redeclipse) (Download "redeclipse" -> 64-bit deb package)
[http://www.ubuntuupdates.org/package/getdeb_games/utopic/games/getdeb/redeclipse-data](http://www.ubuntuupdates.org/package/getdeb_games/utopic/games/getdeb/redeclipse-data) (Download "redeclipse-data" -> All arch deb package)

Despite being billed as utopic, the redeclipse-data package is compatible with Xubuntu 14.04 (trusty). I don't know why they upgraded trusty's redeclipse-data package from getdeb1 to getdeb2 and left utopic (14.10) alone.

No errors, fonts work properly.

[http://i.imgur.com/V0cgmvA.png](http://i.imgur.com/V0cgmvA.png)

---

### Post by ctgcwiqc on 2015-05-28
> [**[COLOR=#C61919][B]matt_symes**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1067998")
you mentiones one command would fix my woes, but failed to mention which one perform this feat.

> [**[COLOR=#000000]ak399g[/COLOR]**]("http://ubuntuforums.org/member.php?u=1985490")
If redeclipse-data~getdeb2 is the correct package, I wonder why I have 4 other laptops running redeclipse-data~getdeb1 and are not prompting me for any updates (getdeb2)

> [**[COLOR=#DD4814][B]ian-weisser**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1841707")
I'm not frustrated, I posted that I was waiting patiently for assistance.  I just felt that I was being talked down to, with no constructive solution to the issue I was faced with.  It's been a long day, not due to PC issues either.  My intentions were to keep the getdeb repo installed to have access to the latest rev of the game.  I dont play it much, unless my kids want me to play with them which is rare.  I have fixed several "broken engines" but I was lost with this issue.  There were no hits for this problem when googling.  I self host LAMP server and run ownCloud and Ampache with SSL.  I love Linux and Ubuntu.  I cant believe how scared I was of CLI when I first migrated to Linux in 2014.  Now I run Ubuntu 14.04 server without GUI.

> [**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1111508")
This guy has been freaking awesome, plus the way he talks makes me laugh.  Thanks for working with me patiently and taking the time to read and respond accordingly.  I sure do appreciate it.

---

### Post by ctgcwiqc on 2015-05-28
```
apt-get install redeclipse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  redeclipse
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,850 kB of archives.
After this operation, 6,054 kB of additional disk space will be used.
(Reading database ... 806152 files and directories currently installed.)
Preparing to unpack .../redeclipse_1.5.1-1~getdeb1_amd64.deb ...
Unpacking redeclipse (1.5.1-1~getdeb1) ...
dpkg: error processing archive /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse-data 1.5.1-1~getdeb2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for doc-base (0.10.5) ...
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
```
rm /usr/share/games/redeclipse/config/fonts/play.cfg 
```
```
apt-get install redeclipseReading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  redeclipse
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,850 kB of archives.
After this operation, 6,054 kB of additional disk space will be used.
(Reading database ... 806152 files and directories currently installed.)
Preparing to unpack .../redeclipse_1.5.1-1~getdeb1_amd64.deb ...
Unpacking redeclipse (1.5.1-1~getdeb1) ...
dpkg: error processing archive /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse-data 1.5.1-1~getdeb2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for doc-base (0.10.5) ...
Errors were encountered while processing:
 /var/cache/apt/archives/redeclipse_1.5.1-1~getdeb1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2015-05-29
ctgcwiqc; Yikes !

Totally UN-expected result !
you removed the file we think is conflicting:
> 
 rm /usr/share/games/redeclipse/config/fonts/play.cfg

And in the install process Once more showing a conflict with the file ! HUH ???
> 
trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse-data 1.5.1-1~getdeb2

Maybe ? it was not removed as I do not see that you exercised the elevated "sudo' execution authorization to remove the file ?

Else; all I know to do now is try and look and see what the package manager is told to do.
Let's find and look at the control files. Supposing that the install process has generated these files .

Let's see what we can find 1st.
```

ls -al /var/lib/dpkg/info/redeclipse.list
ls -al /var/lib/dpkg/info/redeclipse.postinst
ls -al /var/lib/dpkg/info/redeclipse.postrm

```

Depending on what we find we also will want to look at "redeclipse-data" .

Upfront, there is more about the package management system I do not know than that I do know. I do rely on Ian as my mentor and guide in many situations; This one could well be one of "them" .

This is of course if you have the time and the want to to pursue finding this fault in the package manager's attempt to install. From ak399g's input, we know we can 'get' the .deb and install .. But, I agree we should not have to resort to this method .

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ctgcwiqc on 2015-05-29
> Maybe ? it was not removed as I do not see that you exercised the elevated "sudo' execution authorization to remove the file ?
All commands were ran as root.  So the file was removed.  I verified via "ls" there was no file remaining after removal.

```
ls -al /var/lib/dpkg/info/redeclipse.list
ls: cannot access /var/lib/dpkg/info/redeclipse.list: No such file or directory
```
```
ls -al /var/lib/dpkg/info/redeclipse.postinst
ls: cannot access /var/lib/dpkg/info/redeclipse.postinst: No such file or directory
```
```
ls -al /var/lib/dpkg/info/redeclipse.postrm
ls: cannot access /var/lib/dpkg/info/redeclipse.postrm: No such file or directory

``````
ls -al /var/lib/dpkg/info/redeclipse-data.list-rw-r--r-- 1 root root 274436 May 28 10:50 /var/lib/dpkg/info/redeclipse-data.list


``````
ls -al /var/lib/dpkg/info/redeclipse-data.postinst 
ls: cannot access /var/lib/dpkg/info/redeclipse-data.postinst: No such file or directory


``````
ls -al /var/lib/dpkg/info/redeclipse-data.postrm
ls: cannot access /var/lib/dpkg/info/redeclipse-data.postrm: No such file or directory


```

I am not in a hurry.  I will work with you guys to find a fix as to benefit all who want to install this in the future.   Thanks for your time and patience.

---

### Post by Bashing-om on 2015-05-29
ctgcwiqc; Welp;

So much for an easier approach to "see".
Apparently :
> 
Preparing to unpack .../redeclipse_1.5.1-1~getdeb1_amd64.deb ...
Unpacking redeclipse (1.5.1-1~getdeb1) ...
dpkg: error processing archive /var/cache/apt/archives/redeclipse_1.5.1-1~[color=red]getdeb1[/color]_amd64.deb (--unpack):
 trying to overwrite '/usr/share/games/redeclipse/config/fonts/play.cfg', which is also in package redeclipse-data 1.5.1-1~[color=red]getdeb2[/color]
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)

We are not getting far enough in the install process ,due to the possible packaging error, to generate the control files.
I remain mystified why and how "  /usr/share/games/redeclipse/config/fonts/play.cfg " is duplicated.

@ian-weisser ; Is there a way to unpack the .debs on the system with out installing to gain access to the control files ? OR must we go back to the web site and "consult the source " ??

Because
[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2015-05-29
The 'overwrite' file conflict shouldn't happen if the file is really not on the system yet, and if dpkg has really forgotten about the old package.

I would first check that file /usr/share/games/redeclipse/config/fonts/play.cfg really doesn't exist on the system.

I would next check that /var/lib/dpkg/info/redeclipse.* files don't exist. If they do, then --force-remove-reinstreq didn't work and should be done again.

---

### Post by ctgcwiqc on 2015-06-05
/play.cfg is verified to be non-existent on my system.
there were no instances of redeclipse.* in /var/lib/dpkg/info

---

### Post by ctgcwiqc on 2015-06-05
I figured I would use software center to try the install again.  Same error I have been receiving.


[ATTACH=CONFIG]262451[/ATTACH][ATTACH=CONFIG]262452[/ATTACH][ATTACH=CONFIG]262453[/ATTACH][ATTACH=CONFIG]262454[/ATTACH]

---

### Post by bapoumba on 2015-06-05
Post #17 :
```
==> /etc/apt/sources.list.d/steam.list <==
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam

==> /etc/apt/sources.list.d/steam.list.save <==
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
```

Please remove these ppas.

In addition, most of your ppas are duplicated.

---

### Post by Bashing-om on 2015-06-07
ctgcwiqc; Yuk;

You are not forgotten nor abandoned. 
After considerable effort and thinking, I still do not know a way forward. - If I have nothing to say, best to say nothing is the creed here on the forum. 

I am just stonewalled on account of my ignorance .

[INDENT][INDENT][INDENT]I hate when that happens
[/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2015-06-07
Agreed.
One must assume dpkg can be trusted...else the entire system cannot be trusted and should be reinstalled.
If dpkg is providing errors that are provably untrue (file exists), then either dpkg cannot be trusted...or we don't have all the relevant facts (container or chroot? VM confusion? Multiple filesystems?).

I've used dpkg for many years, and never seen a problem like the one described in this thread. My searches have not turned up anybody encountering this before.

---

### Post by ctgcwiqc on 2015-06-14
> **bapoumba said:**
> Post #17 :
```
==> /etc/apt/sources.list.d/steam.list <==
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam

==> /etc/apt/sources.list.d/steam.list.save <==
deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam
```

Please remove these ppas.

In addition, most of your ppas are duplicated.

I have no problem removing the steam PPA.  Point me to the information  on the duplicated ppas, because i dont see them.  I see that I can  install "PPA Manager" to help clean-up duplicates.  Point me in the right  path to see these duplicates.

---

### Post by bapoumba on 2015-06-15
Please see the above quote, you have two entries (one with .save and one without) for most ppas. As it points to the same repo, it is not that important, but one entry is enough.
```
ls -la /etc/apt/sources.list.d
```

---

### Post by ctgcwiqc on 2015-06-15
So i see those *.save files are created automatically when performing dist-upgrade I think.  I removed all with ```
sudo rm *.save
```.  Those are gone now as well as the steam ppa.  I don't know how that helps but I have been meaning to remove some ppas for a while now anyways.

---

### Post by bapoumba on 2015-06-16
Have you tried the update/upgrade again ?

---

### Post by ctgcwiqc on 2015-06-16
```
sudo apt-get update && sudo apt-get upgrade
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
Ign http://download.videolan.org  InRelease                                    
Ign http://us.archive.ubuntu.com trusty InRelease                              
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://download.videolan.org  Release.gpg                                  
Hit http://download.videolan.org  Release                                      
Hit http://download.videolan.org  Packages                                     
Hit http://archive.getdeb.net trusty-getdeb InRelease                          
Hit http://archive.canonical.com trusty Release                                
Hit http://archive.getdeb.net trusty-getdeb/apps amd64 Packages                
Hit http://archive.getdeb.net trusty-getdeb/games amd64 Packages               
Hit http://archive.getdeb.net trusty-getdeb/apps i386 Packages                 
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://archive.getdeb.net trusty-getdeb/games i386 Packages                
Get:2 http://security.ubuntu.com trusty-security Release [63.5 kB]             
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Hit http://extras.ubuntu.com trusty Release                                    
Get:3 http://archive.canonical.com trusty/partner Translation-en [4,588 B]     
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty/main Sources                               
Ign http://download.videolan.org  Translation-en_US                            
Ign http://download.videolan.org  Translation-en                               
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Get:4 http://security.ubuntu.com trusty-security/main Sources [85.8 kB]        
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Ign https://private-ppa.launchpad.net trusty InRelease                         
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:5 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]          
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                  
Ign https://private-ppa.launchpad.net trusty InRelease                         
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty Release                                
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en_US             
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:6 http://us.archive.ubuntu.com trusty-updates Release [63.5 kB]            
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en                
Get:7 http://security.ubuntu.com trusty-security/restricted Sources [2,061 B]  
Ign https://private-ppa.launchpad.net trusty InRelease                         
Ign http://archive.getdeb.net trusty-getdeb/games Translation-en_US            
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://archive.getdeb.net trusty-getdeb/games Translation-en               
Get:8 http://security.ubuntu.com trusty-security/universe Sources [25.7 kB]    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Get:9 http://ppa.launchpad.net trusty Release.gpg [316 B]                      
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Get:10 http://security.ubuntu.com trusty-security/multiverse Sources [2,333 B] 
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:11 http://security.ubuntu.com trusty-security/main amd64 Packages [299 kB] 
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://ppa.launchpad.net trusty Release                                    
Get:12 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Get:13 http://ppa.launchpad.net trusty Release [15.1 kB]                       
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Get:14 http://security.ubuntu.com trusty-security/universe amd64 Packages [108 kB]
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Get:15 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,686 B]
Hit http://ppa.launchpad.net trusty Release                                    
Get:16 http://security.ubuntu.com trusty-security/main i386 Packages [285 kB]  
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Hit http://ppa.launchpad.net trusty Release                                    
Get:17 http://us.archive.ubuntu.com trusty-updates/main Sources [207 kB]       
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Get:18 http://security.ubuntu.com trusty-security/restricted i386 Packages [8,846 B]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign https://private-ppa.launchpad.net trusty Release.gpg                       
Get:19 http://security.ubuntu.com trusty-security/universe i386 Packages [108 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:20 http://us.archive.ubuntu.com trusty-updates/restricted Sources [3,433 B]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:21 http://us.archive.ubuntu.com trusty-updates/universe Sources [120 kB]   
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit https://private-ppa.launchpad.net trusty Release.gpg                       
Get:22 http://ppa.launchpad.net trusty/main amd64 Packages [29.3 kB]           
Get:23 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,841 B]
Get:24 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,143 B]
Get:25 http://security.ubuntu.com trusty-security/main Translation-en [156 kB] 
Hit https://private-ppa.launchpad.net trusty Release.gpg                       
Get:26 http://ppa.launchpad.net trusty/main i386 Packages [29.3 kB]            
Get:27 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [541 kB]
Get:28 http://ppa.launchpad.net trusty/main Translation-en [11.4 kB]           
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:29 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [11.8 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:30 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [286 kB]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit https://private-ppa.launchpad.net trusty Release                           
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:31 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB]
Get:32 http://security.ubuntu.com trusty-security/universe Translation-en [61.1 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit https://private-ppa.launchpad.net trusty Release                           
Hit https://private-ppa.launchpad.net trusty Release                           
Ign https://private-ppa.launchpad.net trusty/main amd64 Packages/DiffIndex     
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign https://private-ppa.launchpad.net trusty/main i386 Packages/DiffIndex      
Get:33 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [528 kB] 
Hit http://ppa.launchpad.net trusty/main Translation-en   
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Get:34 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [11.8 kB]
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Get:35 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [287 kB]
Get:36 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US            
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US            
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US            
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Get:37 http://us.archive.ubuntu.com trusty-updates/main Translation-en [261 kB]
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Fetched 3,664 kB in 10min 19s (5,917 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic linux-tools-common
  linux-tools-generic linux-tools-virtual-lts-utopic
The following packages will be upgraded:
  apparmor aptdaemon aptdaemon-data dh-apparmor fonts-opensymbol initscripts
  libapparmor-perl libapparmor1 libreoffice
  libreoffice-avmedia-backend-gstreamer libreoffice-base libreoffice-base-core
  libreoffice-base-drivers libreoffice-calc libreoffice-common
  libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk
  libreoffice-help-en-us libreoffice-impress libreoffice-java-common
  libreoffice-math libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-report-builder-bin
  libreoffice-sdbc-firebird libreoffice-sdbc-hsqldb libreoffice-style-human
  libreoffice-writer linux-libc-dev python-aptdaemon
  python-aptdaemon.gtk3widgets python3-aptdaemon python3-aptdaemon.gtk3widgets
  python3-aptdaemon.pkcompat python3-uno sysv-rc sysvinit-utils uno-libs3 ure
  wpasupplicant
43 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 91.2 MB of archives.
After this operation, 38.9 kB of additional disk space will be used.
Do you want to continue? [Y/n] 


```

I ran update/upgrade and recieved this response.  I was also notified via Ubuntu Update GUI that partial upgrade was available.  I've read this is best NOT to perform a partial upgrade, as it is most likely an error and would be sorted out evntually.  This has been popping up for a few days now.  I will update the packages taht aren't dependant on the partial upgrade and attempt to reinstall redeclipse.  I am having bad internet problems right now with my wireless ISP so for the last few months trying to install anything large is taking forever.

---

### Post by bapoumba on 2015-06-16
Have you accepted (Y) the previous upgrade ? Did it run without errors ? Could you please post the complete output after you enter Y ?

---

### Post by ctgcwiqc on 2015-06-16
> **bapoumba said:**
> Have you accepted (Y) the previous upgrade ? Did it run without errors ? Could you please post the complete output after you enter Y ?

```
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main sysvinit-utils amd64 2.88dsf-41ubuntu6.2 [53.1 kB]
Get:2 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-base-drivers amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [583 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main sysv-rc all 2.88dsf-41ubuntu6.2 [36.4 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main initscripts amd64 2.88dsf-41ubuntu6.2 [27.7 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libapparmor1 amd64 2.8.95~2430-0ubuntu5.2 [25.5 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libapparmor-perl amd64 2.8.95~2430-0ubuntu5.2 [26.9 kB]
Get:7 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-base amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [1,540 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main apparmor amd64 2.8.95~2430-0ubuntu5.2 [319 kB]
Get:9 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-calc amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [6,400 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-libc-dev amd64 3.13.0-55.92 [777 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main wpasupplicant amd64 2.1-0ubuntu1.3 [749 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main aptdaemon-data all 1.1.1-1ubuntu5.2 [162 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-aptdaemon.gtk3widgets all 1.1.1-1ubuntu5.2 [13.8 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-aptdaemon.pkcompat all 1.1.1-1ubuntu5.2 [32.4 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main aptdaemon all 1.1.1-1ubuntu5.2 [13.5 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-aptdaemon all 1.1.1-1ubuntu5.2 [67.3 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main dh-apparmor all 2.8.95~2430-0ubuntu5.2 [12.3 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python-aptdaemon.gtk3widgets all 1.1.1-1ubuntu5.2 [13.7 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python-aptdaemon all 1.1.1-1ubuntu5.2 [66.7 kB]
Err http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-calc amd64 1:4.4.4~rc2-0ubuntu1~trusty1
  Connection failed
Get:20 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-gnome amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [148 kB]
Get:21 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-gtk amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [280 kB]
Get:22 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-impress amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [1,177 kB]
Get:23 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-writer amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [7,666 kB]
Get:24 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-common all 1:4.4.4~rc2-0ubuntu1~trusty1 [22.0 MB]
Get:25 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-pdfimport amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [281 kB]
Get:26 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-ogltrans amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [154 kB]
Get:27 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main ure amd64 4.4.4~rc2-0ubuntu1~trusty1 [1,825 kB]
Get:28 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main uno-libs3 amd64 4.4.4~rc2-0ubuntu1~trusty1 [784 kB]
Get:29 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-base-core amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [791 kB]
Get:30 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [83.7 kB]
Get:31 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-math amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [420 kB]
Get:32 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main python3-uno amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [179 kB]
Get:33 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-draw amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [3,435 kB]
Get:34 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-core amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [33.2 MB]
Get:35 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main fonts-opensymbol all 2:102.6+LibO4.4.4~rc2-0ubuntu1~trusty1 [160 kB]
Get:36 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-report-builder-bin amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [833 kB]
Get:37 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-avmedia-backend-gstreamer amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [94.1 kB]
Get:38 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-java-common all 1:4.4.4~rc2-0ubuntu1~trusty1 [2,079 kB]
Get:39 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-style-human all 1:4.4.4~rc2-0ubuntu1~trusty1 [1,535 kB]
Get:40 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-help-en-us all 1:4.4.4~rc2-0ubuntu1~trusty1 [2,772 kB]
Get:41 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-sdbc-firebird amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [77.9 kB]
Get:42 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-sdbc-hsqldb amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [183 kB]
Get:43 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-presentation-minimizer all 1:4.4.4~rc2-0ubuntu1~trusty1 [77.9 kB]
Fetched 84.8 MB in 46min 50s (30.2 kB/s)                                       
E: Failed to fetch http://ppa.launchpad.net/libreoffice/ppa/ubuntu/pool/main/libr/libreoffice/libreoffice-calc_4.4.4~rc2-0ubuntu1~trusty1_amd64.deb  Connection failed

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


```

Internet is screwed up.  I'm gonna run update/upgrade again and see if it completes this time.  I will also post screenshots from Ubuntu Software Upadater.

---

### Post by ctgcwiqc on 2015-06-16
> **bapoumba said:**
> Have you accepted (Y) the previous upgrade ? Did it run without errors ? Could you please post the complete output after you enter Y ?  ```
sudo apt-get update && sudo apt-get upgrade [sudo] password for :  no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory Ign http://archive.canonical.com trusty InRelease                               Ign http://ppa.launchpad.net trusty InRelease                                   Ign http://download.videolan.org  InRelease                                     Ign http://extras.ubuntu.com trusty InRelease                                   Ign http://security.ubuntu.com trusty-security InRelease                        Ign http://us.archive.ubuntu.com trusty InRelease                               Hit http://download.videolan.org  Release.gpg                                   Hit http://download.videolan.org  Release                                       Hit http://security.ubuntu.com trusty-security Release.gpg                      Ign http://us.archive.ubuntu.com trusty-updates InRelease                       Hit http://extras.ubuntu.com trusty Release.gpg                                 Hit http://archive.getdeb.net trusty-getdeb InRelease                           Hit http://archive.canonical.com trusty Release.gpg                             Ign http://ppa.launchpad.net trusty InRelease                                   Hit http://download.videolan.org  Packages                                      Hit http://security.ubuntu.com trusty-security Release                          Ign https://private-ppa.launchpad.net trusty InRelease                          Hit http://extras.ubuntu.com trusty Release                                     Hit http://archive.canonical.com trusty Release                                 Ign http://ppa.launchpad.net trusty InRelease                                   Hit http://security.ubuntu.com trusty-security/main Sources                     Hit http://archive.getdeb.net trusty-getdeb/apps amd64 Packages                 Hit http://extras.ubuntu.com trusty/main Sources                                Hit http://archive.canonical.com trusty/partner Sources                         Ign http://ppa.launchpad.net trusty InRelease                                   Hit http://security.ubuntu.com trusty-security/restricted Sources               Ign https://private-ppa.launchpad.net trusty InRelease                          Hit http://archive.getdeb.net trusty-getdeb/games amd64 Packages                Hit http://archive.canonical.com trusty/partner amd64 Packages                  Hit http://extras.ubuntu.com trusty/main amd64 Packages                         Ign http://ppa.launchpad.net trusty InRelease                                   Hit http://security.ubuntu.com trusty-security/universe Sources                 Ign https://private-ppa.launchpad.net trusty InRelease                          Hit http://archive.getdeb.net trusty-getdeb/apps i386 Packages                  Hit http://extras.ubuntu.com trusty/main i386 Packages                          Hit http://archive.canonical.com trusty/partner i386 Packages                   Ign http://ppa.launchpad.net trusty InRelease                                   Hit http://security.ubuntu.com trusty-security/multiverse Sources               Hit https://private-ppa.launchpad.net trusty Release.gpg                        Hit http://archive.canonical.com trusty/partner Translation-en                  Ign http://ppa.launchpad.net trusty InRelease                                   Hit http://archive.getdeb.net trusty-getdeb/games i386 Packages                 Hit http://security.ubuntu.com trusty-security/main amd64 Packages              Hit https://private-ppa.launchpad.net trusty Release.gpg                        Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages        Ign http://ppa.launchpad.net trusty InRelease                                   Hit https://private-ppa.launchpad.net trusty Release.gpg                        Hit http://security.ubuntu.com trusty-security/universe amd64 Packages          Ign http://ppa.launchpad.net trusty InRelease                                   Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages        Hit https://private-ppa.launchpad.net trusty Release                            Ign http://ppa.launchpad.net trusty InRelease                                   Hit http://security.ubuntu.com trusty-security/main i386 Packages               Ign http://ppa.launchpad.net trusty InRelease                                   Hit http://security.ubuntu.com trusty-security/restricted i386 Packages         Hit https://private-ppa.launchpad.net trusty Release                            Hit http://security.ubuntu.com trusty-security/universe i386 Packages           Hit http://ppa.launchpad.net trusty Release.gpg                                 Hit https://private-ppa.launchpad.net trusty Release                            Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages         Ign http://download.videolan.org  Translation-en_US                             Hit https://private-ppa.launchpad.net trusty/main amd64 Packages                Hit http://security.ubuntu.com trusty-security/main Translation-en              Ign http://download.videolan.org  Translation-en                                Hit http://ppa.launchpad.net trusty Release.gpg                                 Hit http://security.ubuntu.com trusty-security/multiverse Translation-en        Ign http://extras.ubuntu.com trusty/main Translation-en_US                      Hit http://ppa.launchpad.net trusty Release.gpg                                 Hit https://private-ppa.launchpad.net trusty/main i386 Packages                 Hit http://ppa.launchpad.net trusty Release.gpg                                 Ign http://extras.ubuntu.com trusty/main Translation-en                         Hit http://security.ubuntu.com trusty-security/restricted Translation-en        Hit http://ppa.launchpad.net trusty Release.gpg                                 Hit http://ppa.launchpad.net trusty Release.gpg                                 Hit http://ppa.launchpad.net trusty Release.gpg                                 Hit http://security.ubuntu.com trusty-security/universe Translation-en          Hit http://ppa.launchpad.net trusty Release.gpg                                 Hit http://ppa.launchpad.net trusty Release.gpg                                 Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en_US              Hit http://ppa.launchpad.net trusty Release.gpg                                 Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en                 Ign http://archive.getdeb.net trusty-getdeb/games Translation-en_US             Ign http://archive.getdeb.net trusty-getdeb/games Translation-en                Hit http://ppa.launchpad.net trusty Release.gpg                             Hit http://ppa.launchpad.net trusty Release      Hit https://private-ppa.launchpad.net trusty/main amd64 Packages        Hit http://ppa.launchpad.net trusty Release                       Hit https://private-ppa.launchpad.net trusty/main i386 Packages                 Hit http://ppa.launchpad.net trusty Release                                     Hit http://ppa.launchpad.net trusty Release                                     Hit http://ppa.launchpad.net trusty Release                                     Hit http://ppa.launchpad.net trusty Release                                     Hit https://private-ppa.launchpad.net trusty/main amd64 Packages        Hit http://ppa.launchpad.net trusty Release                                     Ign http://us.archive.ubuntu.com trusty-backports InRelease                     Hit http://ppa.launchpad.net trusty Release                                     Hit http://us.archive.ubuntu.com trusty Release.gpg                             Hit http://ppa.launchpad.net trusty Release                                     Hit https://private-ppa.launchpad.net trusty/main i386 Packages                 Get:1 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]           Hit http://ppa.launchpad.net trusty Release                                     Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                   Hit http://ppa.launchpad.net trusty Release                                     Hit http://us.archive.ubuntu.com trusty Release                                 Hit http://ppa.launchpad.net trusty/main amd64 Packages                         Get:2 http://us.archive.ubuntu.com trusty-updates Release [63.5 kB]             Hit http://ppa.launchpad.net trusty/main i386 Packages                          Hit http://ppa.launchpad.net trusty/main Translation-en                         Hit http://ppa.launchpad.net trusty/main amd64 Packages                         Hit http://us.archive.ubuntu.com trusty-backports Release                       Hit http://ppa.launchpad.net trusty/main i386 Packages                          Hit http://us.archive.ubuntu.com trusty/main Sources                            Hit http://ppa.launchpad.net trusty/main Translation-en                         Hit http://us.archive.ubuntu.com trusty/restricted Sources                      Hit http://ppa.launchpad.net trusty/main amd64 Packages                         Hit http://us.archive.ubuntu.com trusty/universe Sources                        Hit http://ppa.launchpad.net trusty/main i386 Packages                          Hit http://us.archive.ubuntu.com trusty/multiverse Sources                      Hit http://ppa.launchpad.net trusty/main Translation-en                         Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                     Hit http://ppa.launchpad.net trusty/main amd64 Packages                         Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages               Hit http://ppa.launchpad.net trusty/main i386 Packages                          Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                 Hit http://ppa.launchpad.net trusty/main Translation-en                         Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages               Hit http://ppa.launchpad.net trusty/main amd64 Packages                         Hit http://us.archive.ubuntu.com trusty/main i386 Packages                      Hit http://ppa.launchpad.net trusty/main i386 Packages                          Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages                Hit http://ppa.launchpad.net trusty/main Translation-en                         Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                  Hit http://ppa.launchpad.net trusty/main amd64 Packages                         Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages                Hit http://ppa.launchpad.net trusty/main i386 Packages                          Hit http://ppa.launchpad.net trusty/main Translation-en                         Hit http://us.archive.ubuntu.com trusty/main Translation-en                     Hit http://ppa.launchpad.net trusty/main amd64 Packages                         Hit http://ppa.launchpad.net trusty/main i386 Packages                          Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en               Hit http://ppa.launchpad.net trusty/main Translation-en                         Hit http://ppa.launchpad.net trusty/main amd64 Packages                         Hit http://us.archive.ubuntu.com trusty/restricted Translation-en               Hit http://ppa.launchpad.net trusty/main i386 Packages                          Hit http://ppa.launchpad.net trusty/main Translation-en                         Hit http://us.archive.ubuntu.com trusty/universe Translation-en                 Hit http://ppa.launchpad.net trusty/main amd64 Packages                         Get:3 http://us.archive.ubuntu.com trusty-updates/main Sources [207 kB]         Hit http://ppa.launchpad.net trusty/main i386 Packages                          Ign https://private-ppa.launchpad.net trusty/main Translation-en_US             Ign https://private-ppa.launchpad.net trusty/main Translation-en                Hit http://ppa.launchpad.net trusty/main Translation-en                         Hit http://ppa.launchpad.net trusty/main amd64 Packages                         Ign https://private-ppa.launchpad.net trusty/main Translation-en_US             Hit http://ppa.launchpad.net trusty/main i386 Packages                          Ign https://private-ppa.launchpad.net trusty/main Translation-en                Hit http://ppa.launchpad.net trusty/main Translation-en                         Ign https://private-ppa.launchpad.net trusty/main Translation-en_US             Hit http://ppa.launchpad.net trusty/main amd64 Packages                         Ign https://private-ppa.launchpad.net trusty/main Translation-en                Hit http://ppa.launchpad.net trusty/main i386 Packages                          Hit http://ppa.launchpad.net trusty/main Translation-en                         Get:4 http://us.archive.ubuntu.com trusty-updates/universe Sources [120 kB]     Get:5 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [541 kB]  Get:6 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [11.8 kB] Get:7 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [286 kB] Get:8 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB] Get:9 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [528 kB]   Get:10 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [11.8 kB] Get:11 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [287 kB] Get:12 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB] Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en             Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en       Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en       Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en         Hit http://us.archive.ubuntu.com trusty-backports/main Sources                  Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources            Hit http://us.archive.ubuntu.com trusty-backports/universe Sources              Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources            Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages           Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages     Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages       Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages     Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages            Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages      Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages        Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages      Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en           Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en     Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en     Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en       Get:13 http://us.archive.ubuntu.com trusty-updates/restricted Sources [3,158 B] Get:14 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,108 B] Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                  Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US Fetched 2,090 kB in 6min 18s (5,522 B/s) Reading package lists... Done Reading package lists... Done Building dependency tree        Reading state information... Done Calculating upgrade... Done The following packages have been kept back:   linux-generic linux-headers-generic linux-image-generic linux-tools-common   linux-tools-generic linux-tools-virtual-lts-utopic The following packages will be upgraded:   apparmor aptdaemon aptdaemon-data dh-apparmor fonts-opensymbol initscripts   libapparmor-perl libapparmor1 libreoffice   libreoffice-avmedia-backend-gstreamer libreoffice-base libreoffice-base-core   libreoffice-base-drivers libreoffice-calc libreoffice-common   libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk   libreoffice-help-en-us libreoffice-impress libreoffice-java-common   libreoffice-math libreoffice-ogltrans libreoffice-pdfimport   libreoffice-presentation-minimizer libreoffice-report-builder-bin   libreoffice-sdbc-firebird libreoffice-sdbc-hsqldb libreoffice-style-human   libreoffice-writer linux-libc-dev python-aptdaemon   python-aptdaemon.gtk3widgets python3-aptdaemon python3-aptdaemon.gtk3widgets   python3-aptdaemon.pkcompat python3-uno sysv-rc sysvinit-utils uno-libs3 ure   wpasupplicant 43 upgraded, 0 newly installed, 0 to remove and 6 not upgraded. Need to get 6,400 kB/91.2 MB of archives. After this operation, 38.9 kB of additional disk space will be used. Do you want to continue? [Y/n] y Get:1 http://ppa.launchpad.net/libreoffice/ppa/ubuntu/ trusty/main libreoffice-calc amd64 1:4.4.4~rc2-0ubuntu1~trusty1 [6,400 kB] Fetched 1,220 kB in 1min 33s (13.1 kB/s)                                        Extracting templates from packages: 100% Preconfiguring packages ... (Reading database ... 801990 files and directories currently installed.) Preparing to unpack .../libreoffice-base-drivers_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking libreoffice-base-drivers (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-base_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking libreoffice-base (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-calc_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking libreoffice-calc (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-gnome_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking libreoffice-gnome (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-gtk_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking libreoffice-gtk (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-impress_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking libreoffice-impress (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-writer_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking libreoffice-writer (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-common_1%3a4.4.4~rc2-0ubuntu1~trusty1_all.deb ... Unpacking libreoffice-common (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-pdfimport_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking libreoffice-pdfimport (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-ogltrans_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking libreoffice-ogltrans (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../ure_4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking ure (4.4.4~rc2-0ubuntu1~trusty1) over (4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../uno-libs3_4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking uno-libs3 (4.4.4~rc2-0ubuntu1~trusty1) over (4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-base-core_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking libreoffice-base-core (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking libreoffice (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-math_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking libreoffice-math (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../python3-uno_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking python3-uno (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-draw_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking libreoffice-draw (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-core_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking libreoffice-core (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../fonts-opensymbol_2%3a102.6+LibO4.4.4~rc2-0ubuntu1~trusty1_all.deb ... Unpacking fonts-opensymbol (2:102.6+LibO4.4.4~rc2-0ubuntu1~trusty1) over (2:102.6+LibO4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-report-builder-bin_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking libreoffice-report-builder-bin (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-avmedia-backend-gstreamer_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking libreoffice-avmedia-backend-gstreamer (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-java-common_1%3a4.4.4~rc2-0ubuntu1~trusty1_all.deb ... Unpacking libreoffice-java-common (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-style-human_1%3a4.4.4~rc2-0ubuntu1~trusty1_all.deb ... Unpacking libreoffice-style-human (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../sysvinit-utils_2.88dsf-41ubuntu6.2_amd64.deb ... Unpacking sysvinit-utils (2.88dsf-41ubuntu6.2) over (2.88dsf-41ubuntu6.1) ... Preparing to unpack .../sysv-rc_2.88dsf-41ubuntu6.2_all.deb ... Unpacking sysv-rc (2.88dsf-41ubuntu6.2) over (2.88dsf-41ubuntu6.1) ... Processing triggers for mime-support (3.54ubuntu1.1) ... Processing triggers for gnome-menus (3.10.1-0ubuntu2) ... Processing triggers for desktop-file-utils (0.22-1ubuntu1) ... Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ... Rebuilding /usr/share/applications/bamf-2.index... Processing triggers for man-db (2.6.7.1-1ubuntu1) ... Processing triggers for gnome-icon-theme (3.10.0-0ubuntu2) ... Processing triggers for hicolor-icon-theme (0.13-1) ... Processing triggers for shared-mime-info (1.2-0ubuntu3) ... Unknown media type in type 'all/all' Unknown media type in type 'all/allfiles' Unknown media type in type 'uri/mms' Unknown media type in type 'uri/mmst' Unknown media type in type 'uri/mmsu' Unknown media type in type 'uri/pnm' Unknown media type in type 'uri/rtspt' Unknown media type in type 'uri/rtspu' Processing triggers for fontconfig (2.11.0-0ubuntu4.1) ... Processing triggers for ureadahead (0.100.0-16) ... ureadahead will be reprofiled on next reboot Setting up sysvinit-utils (2.88dsf-41ubuntu6.2) ... Setting up sysv-rc (2.88dsf-41ubuntu6.2) ... (Reading database ... 801990 files and directories currently installed.) Preparing to unpack .../initscripts_2.88dsf-41ubuntu6.2_amd64.deb ... Unpacking initscripts (2.88dsf-41ubuntu6.2) over (2.88dsf-41ubuntu6.1) ... Preparing to unpack .../libapparmor1_2.8.95~2430-0ubuntu5.2_amd64.deb ... Unpacking libapparmor1:amd64 (2.8.95~2430-0ubuntu5.2) over (2.8.95~2430-0ubuntu5.1) ... Preparing to unpack .../libapparmor-perl_2.8.95~2430-0ubuntu5.2_amd64.deb ... Unpacking libapparmor-perl (2.8.95~2430-0ubuntu5.2) over (2.8.95~2430-0ubuntu5.1) ... Preparing to unpack .../apparmor_2.8.95~2430-0ubuntu5.2_amd64.deb ... Unpacking apparmor (2.8.95~2430-0ubuntu5.2) over (2.8.95~2430-0ubuntu5.1) ... Preparing to unpack .../libreoffice-help-en-us_1%3a4.4.4~rc2-0ubuntu1~trusty1_all.deb ... Unpacking libreoffice-help-en-us (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-sdbc-firebird_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking libreoffice-sdbc-firebird (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../libreoffice-sdbc-hsqldb_1%3a4.4.4~rc2-0ubuntu1~trusty1_amd64.deb ... Unpacking libreoffice-sdbc-hsqldb (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../linux-libc-dev_3.13.0-55.92_amd64.deb ... Unpacking linux-libc-dev:amd64 (3.13.0-55.92) over (3.13.0-54.91) ... Preparing to unpack .../wpasupplicant_2.1-0ubuntu1.3_amd64.deb ... Unpacking wpasupplicant (2.1-0ubuntu1.3) over (2.1-0ubuntu1.2) ... Preparing to unpack .../aptdaemon-data_1.1.1-1ubuntu5.2_all.deb ... Unpacking aptdaemon-data (1.1.1-1ubuntu5.2) over (1.1.1-1ubuntu5.1) ... Preparing to unpack .../python3-aptdaemon.gtk3widgets_1.1.1-1ubuntu5.2_all.deb ... Unpacking python3-aptdaemon.gtk3widgets (1.1.1-1ubuntu5.2) over (1.1.1-1ubuntu5.1) ... Preparing to unpack .../python3-aptdaemon.pkcompat_1.1.1-1ubuntu5.2_all.deb ... Unpacking python3-aptdaemon.pkcompat (1.1.1-1ubuntu5.2) over (1.1.1-1ubuntu5.1) ... Preparing to unpack .../aptdaemon_1.1.1-1ubuntu5.2_all.deb ... Unpacking aptdaemon (1.1.1-1ubuntu5.2) over (1.1.1-1ubuntu5.1) ... Preparing to unpack .../python3-aptdaemon_1.1.1-1ubuntu5.2_all.deb ... Unpacking python3-aptdaemon (1.1.1-1ubuntu5.2) over (1.1.1-1ubuntu5.1) ... Preparing to unpack .../dh-apparmor_2.8.95~2430-0ubuntu5.2_all.deb ... Unpacking dh-apparmor (2.8.95~2430-0ubuntu5.2) over (2.8.95~2430-0ubuntu5.1) ... Preparing to unpack .../libreoffice-presentation-minimizer_1%3a4.4.4~rc2-0ubuntu1~trusty1_all.deb ... Unpacking libreoffice-presentation-minimizer (1:4.4.4~rc2-0ubuntu1~trusty1) over (1:4.4.3~rc2-0ubuntu1~trusty1) ... Preparing to unpack .../python-aptdaemon.gtk3widgets_1.1.1-1ubuntu5.2_all.deb ... Unpacking python-aptdaemon.gtk3widgets (1.1.1-1ubuntu5.2) over (1.1.1-1ubuntu5.1) ... Preparing to unpack .../python-aptdaemon_1.1.1-1ubuntu5.2_all.deb ... Unpacking python-aptdaemon (1.1.1-1ubuntu5.2) over (1.1.1-1ubuntu5.1) ... Processing triggers for man-db (2.6.7.1-1ubuntu1) ... Processing triggers for ureadahead (0.100.0-16) ... Processing triggers for hicolor-icon-theme (0.13-1) ... Setting up fonts-opensymbol (2:102.6+LibO4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-style-human (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up uno-libs3 (4.4.4~rc2-0ubuntu1~trusty1) ... Setting up ure (4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-common (1:4.4.4~rc2-0ubuntu1~trusty1) ... Installing new version of config file /etc/bash_completion.d/libreoffice.sh ... Setting up libreoffice-core (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-base-drivers (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-base-core (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-base (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-calc (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-gtk (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-gnome (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-draw (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-impress (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-writer (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-pdfimport (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-ogltrans (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-math (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-report-builder-bin (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-avmedia-backend-gstreamer (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-java-common (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up python3-uno (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up initscripts (2.88dsf-41ubuntu6.2) ... Setting up libapparmor1:amd64 (2.8.95~2430-0ubuntu5.2) ... Setting up libapparmor-perl (2.8.95~2430-0ubuntu5.2) ... Setting up apparmor (2.8.95~2430-0ubuntu5.2) ... Installing new version of config file /etc/apparmor.d/abstractions/X ... Installing new version of config file /etc/apparmor.d/abstractions/ubuntu-helpers ... Installing new version of config file /etc/apparmor.d/abstractions/php5 ...  * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd                                                                          [ OK ]  * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd                                                                          [ OK ] Setting up libreoffice-help-en-us (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-sdbc-firebird (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up libreoffice-sdbc-hsqldb (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up linux-libc-dev:amd64 (3.13.0-55.92) ... Setting up wpasupplicant (2.1-0ubuntu1.3) ... Setting up aptdaemon-data (1.1.1-1ubuntu5.2) ... Setting up python3-aptdaemon (1.1.1-1ubuntu5.2) ... Setting up python3-aptdaemon.gtk3widgets (1.1.1-1ubuntu5.2) ... Setting up python3-aptdaemon.pkcompat (1.1.1-1ubuntu5.2) ... Setting up aptdaemon (1.1.1-1ubuntu5.2) ... Setting up dh-apparmor (2.8.95~2430-0ubuntu5.2) ... Setting up libreoffice-presentation-minimizer (1:4.4.4~rc2-0ubuntu1~trusty1) ... Setting up python-aptdaemon (1.1.1-1ubuntu5.2) ... Setting up python-aptdaemon.gtk3widgets (1.1.1-1ubuntu5.2) ... Processing triggers for libc-bin (2.19-0ubuntu6.6) ...  
``` Looks like that part was successful.  Was going to re-run to make sure everything was updated minus the "partial upgrade" packages but received this error.  Going to reboot now.  ```
# apt-get update E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable) E: Unable to lock directory /var/lib/apt/lists/ root@cgultrabook:/home/clint#      
```

---

### Post by ctgcwiqc on 2015-06-16
I attempted to post the successful update, but apparently it failed to post. Attached is output of the "partial upgrade" I am given the option to perform.

```
sudo apt-get update
[sudo] password for : 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://us.archive.ubuntu.com trusty InRelease                              
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://download.videolan.org  InRelease                                    
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:2 http://security.ubuntu.com trusty-security Release [63.5 kB]             
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://download.videolan.org  Release.gpg                                  
Hit http://archive.canonical.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty Release                                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.getdeb.net trusty-getdeb InRelease                          
Hit http://download.videolan.org  Release                                      
Get:3 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]          
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://extras.ubuntu.com trusty/main Sources                               
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://download.videolan.org  Packages                                     
Get:4 http://security.ubuntu.com trusty-security/main Sources [85.8 kB]        
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://archive.getdeb.net trusty-getdeb/apps amd64 Packages                
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign https://private-ppa.launchpad.net trusty InRelease                         
Get:5 http://us.archive.ubuntu.com trusty-updates Release [63.5 kB]            
Hit http://archive.getdeb.net trusty-getdeb/games amd64 Packages               
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign https://private-ppa.launchpad.net trusty InRelease                         
Get:6 http://security.ubuntu.com trusty-security/restricted Sources [2,061 B]  
Hit http://archive.getdeb.net trusty-getdeb/apps i386 Packages                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:7 http://security.ubuntu.com trusty-security/universe Sources [25.7 kB]    
Ign https://private-ppa.launchpad.net trusty InRelease                         
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Hit http://archive.getdeb.net trusty-getdeb/games i386 Packages                
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:8 http://security.ubuntu.com trusty-security/multiverse Sources [2,333 B]  
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Ign http://archive.canonical.com trusty/partner Translation-en                 
Get:9 http://security.ubuntu.com trusty-security/main amd64 Packages [299 kB]  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit https://private-ppa.launchpad.net trusty Release                           
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Get:10 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://download.videolan.org  Translation-en_US                            
Hit https://private-ppa.launchpad.net trusty Release                           
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Get:11 http://security.ubuntu.com trusty-security/universe amd64 Packages [108 kB]
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Ign http://download.videolan.org  Translation-en                               
Hit https://private-ppa.launchpad.net trusty Release                           
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Get:12 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,686 B]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Get:13 http://security.ubuntu.com trusty-security/main i386 Packages [285 kB]  
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:14 http://security.ubuntu.com trusty-security/restricted i386 Packages [8,846 B]
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Get:15 http://security.ubuntu.com trusty-security/universe i386 Packages [108 kB]
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Get:16 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,841 B]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Get:17 http://us.archive.ubuntu.com trusty-updates/main Sources [207 kB]       
Hit http://ppa.launchpad.net trusty Release                                    
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://ppa.launchpad.net trusty Release                                    
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en_US             
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en                
Get:18 http://us.archive.ubuntu.com trusty-updates/restricted Sources [3,433 B]
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://archive.getdeb.net trusty-getdeb/games Translation-en_US            
Get:19 http://us.archive.ubuntu.com trusty-updates/universe Sources [120 kB]   
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://archive.getdeb.net trusty-getdeb/games Translation-en               
Hit http://ppa.launchpad.net trusty Release                                    
Get:20 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,143 B]
Hit http://ppa.launchpad.net trusty Release                                    
Get:21 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [541 kB]
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:22 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [11.8 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:23 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [286 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:24 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [12.0 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:25 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [528 kB] 
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:26 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [11.8 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US            
Get:27 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [287 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US            
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Get:28 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US            
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Fetched 3,097 kB in 47s (65.5 kB/s)
Reading package lists... Done
clint@cgultrabook:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-lts-utopic-tools-3.16.0-39 linux-tools-3.16.0-39-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-lts-utopic-tools-3.16.0-33 linux-lts-utopic-tools-3.16.0-38
  linux-lts-utopic-tools-common linux-tools-3.16.0-33-generic
  linux-tools-3.16.0-38-generic
The following NEW packages will be installed:
  linux-headers-3.13.0-55 linux-headers-3.13.0-55-generic
  linux-image-3.13.0-55-generic linux-image-extra-3.13.0-55-generic
  linux-lts-utopic-tools-3.16.0-41 linux-tools-3.13.0-55
  linux-tools-3.13.0-55-generic linux-tools-3.16.0-41-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic linux-tools-common
  linux-tools-generic linux-tools-virtual-lts-utopic
6 upgraded, 8 newly installed, 5 to remove and 0 not upgraded.
Need to get 47.4 MB/62.6 MB of archives.
After this operation, 271 MB of additional disk space will be used.
Do you want to continue? [Y/n] ^Cclint@cgultrabook:~$ ^C          
clint@cgultrabook:~$ clear

clint@cgultrabook:~$ sudo apt-get update && sudo apt-get upgrade
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://download.videolan.org  InRelease                                    
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://us.archive.ubuntu.com trusty InRelease                              
Ign http://archive.canonical.com trusty InRelease                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://download.videolan.org  Release.gpg                                  
Ign http://security.ubuntu.com trusty-security InRelease                       
Hit http://archive.canonical.com trusty Release.gpg                            
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://download.videolan.org  Release                                      
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Hit http://archive.canonical.com trusty Release                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.getdeb.net trusty-getdeb InRelease                          
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://download.videolan.org  Packages                                     
Hit http://security.ubuntu.com trusty-security Release                         
Hit http://archive.canonical.com trusty/partner Sources                        
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty-updates Release.gpg                    
Ign https://private-ppa.launchpad.net trusty InRelease                         
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://archive.getdeb.net trusty-getdeb/apps amd64 Packages                
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign https://private-ppa.launchpad.net trusty InRelease                         
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://archive.getdeb.net trusty-getdeb/games amd64 Packages               
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/universe Sources                
Ign https://private-ppa.launchpad.net trusty InRelease                         
Hit http://us.archive.ubuntu.com trusty-updates Release                        
Hit http://archive.getdeb.net trusty-getdeb/apps i386 Packages                 
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit https://private-ppa.launchpad.net trusty Release.gpg                       
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://archive.getdeb.net trusty-getdeb/games i386 Packages                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit https://private-ppa.launchpad.net trusty Release.gpg                       
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Ign http://archive.canonical.com trusty/partner Translation-en                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit https://private-ppa.launchpad.net trusty Release.gpg                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit https://private-ppa.launchpad.net trusty Release                           
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit https://private-ppa.launchpad.net trusty Release                           
Ign http://download.videolan.org  Translation-en_US                            
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit https://private-ppa.launchpad.net trusty Release                           
Ign http://download.videolan.org  Translation-en                               
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://ppa.launchpad.net trusty Release                                    
Hit https://private-ppa.launchpad.net trusty/main amd64 Packages               
Hit http://ppa.launchpad.net trusty Release                                    
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en_US             
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty-updates/main Sources                   
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en                
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources             
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://archive.getdeb.net trusty-getdeb/games Translation-en_US            
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources               
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://archive.getdeb.net trusty-getdeb/games Translation-en               
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources             
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages            
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages        
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages      
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages         
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US            
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US            
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US            
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Ign https://private-ppa.launchpad.net trusty/main Translation-en               
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Reading package lists... Done                                                  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic linux-tools-common
  linux-tools-generic linux-tools-virtual-lts-utopic
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
clint@cgultrabook:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-lts-utopic-tools-3.16.0-39 linux-tools-3.16.0-39-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-lts-utopic-tools-3.16.0-33 linux-lts-utopic-tools-3.16.0-38
  linux-lts-utopic-tools-common linux-tools-3.16.0-33-generic
  linux-tools-3.16.0-38-generic
The following NEW packages will be installed:
  linux-headers-3.13.0-55 linux-headers-3.13.0-55-generic
  linux-image-3.13.0-55-generic linux-image-extra-3.13.0-55-generic
  linux-lts-utopic-tools-3.16.0-41 linux-tools-3.13.0-55
  linux-tools-3.13.0-55-generic linux-tools-3.16.0-41-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic linux-tools-common
  linux-tools-generic linux-tools-virtual-lts-utopic
6 upgraded, 8 newly installed, 5 to remove and 0 not upgraded.
Need to get 47.4 MB/62.6 MB of archives.
After this operation, 271 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.


```

What I have read in the past says to steer clear of these "partial upgrades".  What should I do about this?  I will attempt reinstallation of red eclipse now.

---

### Post by ian-weisser on 2015-06-16
The offer to do a 'partial upgrade' means that you have a problem.
You have non-Ubuntu software, or have mixed different versions of the software, or have replaced Ubutntu software with non-Ubuntu versions. You have hopelessly confounded the package manager to the point that it cannot provide you a reliable upgrade path anymore. Your system may work, but it is fundamentally broken.

Your package manager is a vital element of your Ubuntu system. It's how  you get security updates. It's how you upgrade. Don't install software  that breaks it.

I advise against the partial upgrade, unless you are adept at manually diagnosing version conflicts.
I advise against installing yet more non-Ubuntu software.

I think you should uninstall all non-Ubuntu software and restore your package manager to a useful, working condition (or else reinstall to accomplish the same).
Once you have a working package manager, you can reinstall your non-Ubuntu software. Keep track of it. Check your package manager by updating after each non-Ubuntu install.

---

### Post by ctgcwiqc on 2015-06-17
I appreciate your help.  I dont understand what you mean by "non-ubuntu" software.  Are you refering to applications that run under wine, or PPAs that are not official preconfigured PPAs.  Its not like I have hundreds of PPAs added.  
I will begin removing them if that's what you are talking about.  I alreday keep a list of changes made to laptops, as well as servers.  

What still has not been answered is why I have 6 laptops with the exact same setup and this is the only one with the problems.  Why are PPAs so evil?  Why are they frowned upon so negatively.  I dont know anyone who only uses the default repositories, there are too many essential programs which are not current enough or not available.  

Is there a way to determine which PPA/software is the bad actor without removing all or reinstalling OS altogether?  I have to think the first thing to remove would obviously be the getdeb repo which maintains the software Red Eclipse which originally brought me here as well as remove any software/repos that I don't use frequently.

---

### Post by ian-weisser on 2015-06-17
> **ctgcwiqc said:**
> I appreciate your help.  I dont understand what you mean by "non-ubuntu" software.  Are you refering to applications that run under wine, or PPAs that are not official preconfigured PPAs.
Could be any of those. Or something else.



> **ctgcwiqc said:**
> What still has not been answered is why I have 6 laptops with the exact same setup and this is the only one with the problems.
Is it possible that something is different on the one?



> **ctgcwiqc said:**
> Why are PPAs so evil?  Why are they frowned upon so negatively.  I dont know anyone who only uses the default repositories, there are too many essential programs which are not current enough or not available.

PPAs are not *evil*. PPAs, since they don't go through the same kind of testing that Ubuntu packages do, sometimes introduce either of two kinds of *conflicts* into a system. The PPA author don't intend to introduce these problems; when you discover them, let the author know.

1) Version conflicts - the PPA's version number is higher than the corresponding package in the next release of Ubuntu, and prevents the entire system from upgrading to the next release of Ubuntu. This is simple enough to overcome - merely uninstall the PPA software before doing a release upgrade. 

2) File conflicts - The PPA provides a different set of files, overlapping the files provided by another package. This is also easy to overcome - simply decide which of the two package you *really* want; you can't have both.

If a version is 'Not current enough', then you should probably be using a newer release of Ubuntu. The point of an LTS release is that you DON'T want newer versions of software disrupting your workflow, and that doesn't seem to be your use case.




> **ctgcwiqc said:**
> Is there a way to determine which PPA/software is the bad actor without removing all or reinstalling OS altogether?
Normally, yes. We help several people each day do that.
But your situation seems different. Reviewing the thread, your problem wasn't a PPA. Your problem was that dpkg was claiming a file conflict where none existed.
Is that still the problem?

---

### Post by ctgcwiqc on 2015-06-17
This looks a little better after removing a few PPAs.  Does this look safe to run?  It does to me.  It is trying to remove some utopic files which probably should not have been installed.  These may be why it is trying to install the utopic version of Red Eclipse Data when installing Red Eclipse?  
```
sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-lts-utopic-tools-3.16.0-33 linux-lts-utopic-tools-3.16.0-38
  linux-lts-utopic-tools-common linux-tools-3.16.0-33-generic
  linux-tools-3.16.0-38-generic
The following packages will be upgraded:
  linux-tools-common
1 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 88.6 kB of archives.
After this operation, 3,804 kB disk space will be freed.
Do you want to continue? [Y/n]  


```

Looks like it still wants to install the getdeb2 version.  Maybe this will change once the "dist-upgrade" is completed?

```
sudo apt-get install redeclipse-data 
[sudo] password for clint: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  redeclipse-data
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 781 MB of archives.
After this operation, 893 MB of additional disk space will be used.
Get:1 http://archive.getdeb.net/ubuntu/ trusty-getdeb/games redeclipse-data all 1.5.1-1~getdeb2 [781 MB]
0% [1 redeclipse-data 291 kB/781 MB 0%]^C
```

---

### Post by ian-weisser on 2015-06-17
Well, first, I recommend using apt's --simulate flag instead of ^C during package actions. Same effect, cleaner exit. Prevents abandoned lockfiles (as happened to you before).

Second, apt *remembers* that you previously told it to install redeclipse-data. It doesn't know when you change your mind, so every time you run apt, it will try to install redeclipse-data until it succeeds or you tell it differently.

Installing 781MB of packages looks bit much for one game. If you think it's correct, then sure...it's your system...feel free to try.

---

### Post by ctgcwiqc on 2015-06-17
So my first question really was in regards to the removal of > The following packages will be REMOVED:
  linux-lts-utopic-tools-3.16.0-33 linux-lts-utopic-tools-3.16.0-38
  linux-lts-utopic-tools-common linux-tools-3.16.0-33-generic
  linux-tools-3.16.0-38-generic

I don&#8217;t believe you gave me an answer in regards to that being safe to execute as it appears to be reverting back to something and removing the "utopic" files that were probably to blame for red-eclipse attempting to install the wrong package getdeb2(utopic) vs getdeb1(trusty).  Am I confusing or confused?

I know the file size is correct for redeclipse-data as it was successfully installed for quite a while prior to this mishap where I was offered an update which created this problem.  The two main issues were the fact there was a write error due to a conflicting file, as well as the wrong version (in my opinion) of the redeclipse-data file was trying to install.

---

### Post by ian-weisser on 2015-06-17
> **ctgcwiqc said:**
> So my first question really was in regards to the removal of 

Oh, [I]that.
[/I]Sorry for the misunderstanding.
That seems expected, and fine. Unrelated to your issue. Go right ahead.

---

### Post by ctgcwiqc on 2015-06-17
OK, so I ran dist-upgrade and all went well as far as I can tell.  There are no upgrades available.  So we still have the remaining issue of red eclipse not working.  I sent an email to the getdeb support people and provided a link to this forum posting.  Is there anything else I should try?  Thanks.

---

### Post by ian-weisser on 2015-06-18
That's about all that I can think of.

If the issue can be reproduced on another system, then you have done all I can think of.

If the issue cannot be reproduced on another system, then I suggest reinstalling...then see if the issue can be reproduced.

---

### Post by bapoumba on 2015-06-20
From some of the recent outputs :
> no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
May be here : [http://ubuntuforums.org/showthread.php?t=2214042](http://ubuntuforums.org/showthread.php?t=2214042)

---

### Post by ctgcwiqc on 2015-06-22
> **ak399g said:**
> Can be installed properly with:
[http://www.ubuntuupdates.org/package/getdeb_games/trusty/games/getdeb/redeclipse](http://www.ubuntuupdates.org/package/getdeb_games/trusty/games/getdeb/redeclipse) (Download "redeclipse" -> 64-bit deb package)
[http://www.ubuntuupdates.org/package/getdeb_games/utopic/games/getdeb/redeclipse-data](http://www.ubuntuupdates.org/package/getdeb_games/utopic/games/getdeb/redeclipse-data) (Download "redeclipse-data" -> All arch deb package)

Despite being billed as utopic, the redeclipse-data package is compatible with Xubuntu 14.04 (trusty). I don't know why they upgraded trusty's redeclipse-data package from getdeb1 to getdeb2 and left utopic (14.10) alone.

No errors, fonts work properly.

[http://i.imgur.com/V0cgmvA.png](http://i.imgur.com/V0cgmvA.png)

I have downloaded the files and will attempt to install them tonight.  I will also attempt to reach out to someone associated with getdeb and try to get this fixed.  This issue is now persistent on 5 laptops, Dell, HP, HP, Compaq, Samsung.  I believe they have the conflicting font file in both redeclipse as well as redeclipse-data file and this is casuing the problem as I believe you suggested previously.  Thanks to all.

---

### Post by ctgcwiqc on 2015-06-22
So the files installed and things are working, however I am back at post number 1.  I am presented with an update to redeclipse-data 1.5.1.1getdeb2.  I will still try to work with someone from getdeb to get this fixed as I am certainly not the only one experiencing this issue.

---

### Post by ctgcwiqc on 2015-06-22
> If a version is 'Not current enough', then you should probably be using a  newer release of Ubuntu. The point of an LTS release is that you DON'T  want newer versions of software disrupting your workflow, and that  doesn't seem to be your use case.



You are correct Ian-Weisser.  I picked LTS due to the fact I dont want to update OS every 6-9 months.  I have converted 7 machines to Ubuntu 14.04 from windows for myself, kids, my dad, and a webserver running Ubuntu Server 14.04.  That is a task enough to maintain without worrying about messing up the upgrade and losing data.  i would of course clone the disk prior to making an attempt to update.  

What would be the correct update path?  Set update manager to prompt me for all new releases instead of LTS only?  Clone drive.  Go through the update process.  Then update any PPAs and point them to the proper release?  I have never upgraded to next release of Ubuntu.  I came over from Linux Mint 16 or 17 and started with 14.04.

---

