---
title: "Target package is configured multiple times"
date: 2016-05-29
forum: General Help
---

### Post by Evil Wayz on 2016-05-29
This doesn't sound like something I want.  So how do I figure out what stays and what goes?  

```
W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:39 and /etc/apt/sources.list.d/xenial-partner.list:4

```

---

### Post by Bashing-om on 2016-05-29
Evil Wayz; Hey ...

Find the duplicate entry:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
and decide on which is the duplicate and remove ONE of them .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Evil Wayz on 2016-05-30
But how do I know which is the right one?  I would assume sources is the one I want to keep since that's what update uses.

First command yields:
```
wolf@shaitan:~$ cat -n /etc/apt/sources.list
     1	
     2	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     3	# newer versions of the distribution.
     4	deb http://dist1.800hosting.com/ubuntu/ xenial main restricted
     5	
     6	## Major bug fix updates produced after the final release of the
     7	## distribution.
     8	deb http://dist1.800hosting.com/ubuntu/ xenial-updates main restricted
     9	
    10	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    11	## team. Also, please note that software in universe WILL NOT receive any
    12	## review or updates from the Ubuntu security team.
    13	deb http://dist1.800hosting.com/ubuntu/ xenial universe
    14	deb http://dist1.800hosting.com/ubuntu/ xenial-updates universe
    15	
    16	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    17	## team, and may not be under a free licence. Please satisfy yourself as to 
    18	## your rights to use the software. Also, please note that software in 
    19	## multiverse WILL NOT receive any review or updates from the Ubuntu
    20	## security team.
    21	deb http://dist1.800hosting.com/ubuntu/ xenial multiverse
    22	deb http://dist1.800hosting.com/ubuntu/ xenial-updates multiverse
    23	
    24	## N.B. software from this repository may not have been tested as
    25	## extensively as that contained in the main release, although it includes
    26	## newer versions of some applications which may provide useful features.
    27	## Also, please note that software in backports WILL NOT receive any review
    28	## or updates from the Ubuntu security team.
    29	deb http://dist1.800hosting.com/ubuntu/ xenial-backports main restricted universe multiverse
    30	
    31	deb http://dist1.800hosting.com/ubuntu/ xenial-security main restricted
    32	deb http://dist1.800hosting.com/ubuntu/ xenial-security universe
    33	deb http://dist1.800hosting.com/ubuntu/ xenial-security multiverse
    34	
    35	## Uncomment the following two lines to add software from Canonical's
    36	## 'partner' repository.
    37	## This software is not part of Ubuntu, but is offered by Canonical and the
    38	## respective vendors as a service to Ubuntu users.
    39	deb http://archive.canonical.com/ubuntu xenial partner
    40	deb-src http://archive.canonical.com/ubuntu xenial partner
    41	
    42	deb http://dist1.800hosting.com/ubuntu/ xenial-proposed main universe multiverse restricted
    43	#Added by software-properties
    44	deb http://ubuntusatanic.org/hell quantal main # disabled on upgrade to wily
    45	deb-src http://ubuntusatanic.org/hell quantal main # disabled on upgrade to wily
    46	# deb http://ppa.launchpad.net/cdemu/ubuntu wily main # disabled on upgrade to wily
    47	# deb-src http://ppa.launchpad.net/cdemu/ubuntu wily main # disabled on upgrade to wily
    48	deb http://www.bunkus.org/ubuntu/xenial/ ./ # disabled on upgrade to wily
    49	deb-src http://www.bunkus.org/ubuntu/xenial/ ./ # disabled on upgrade to wily
    50	# deb http://ppa.launchpad.net/skoruppa/ppa/ubuntu hardy main
    51	# deb-src http://ppa.launchpad.net/skoruppa/ppa/ubuntu hardy main
    52	# deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
    53	# deb-src [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

```

Second command yields:
```
wolf@shaitan:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/alex-wv-pulseaudio-equalizer-ppa-trusty.list <==
# deb http://ppa.launchpad.net/alex-wv/pulseaudio-equalizer-ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/alex-wv/pulseaudio-equalizer-ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/alex-wv-pulseaudio-equalizer-ppa-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/alex-wv/pulseaudio-equalizer-ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/alex-wv/pulseaudio-equalizer-ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/alex-wv-pulseaudio-equalizer-ppa-trusty.list.save <==
# deb http://ppa.launchpad.net/alex-wv/pulseaudio-equalizer-ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/alex-wv/pulseaudio-equalizer-ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/atareao-atareao-trusty.list <==
# deb http://ppa.launchpad.net/atareao/atareao/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main

==> /etc/apt/sources.list.d/atareao-atareao-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/atareao/atareao/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main

==> /etc/apt/sources.list.d/atareao-atareao-trusty.list.save <==
# deb http://ppa.launchpad.net/atareao/atareao/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main

==> /etc/apt/sources.list.d/atareao-ubuntu-atareao-xenial.list <==
deb http://ppa.launchpad.net/atareao/atareao/ubuntu xenial main
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu xenial main

==> /etc/apt/sources.list.d/atareao-ubuntu-atareao-xenial.list.save <==
deb http://ppa.launchpad.net/atareao/atareao/ubuntu xenial main
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu xenial main

==> /etc/apt/sources.list.d/brandonsnider-gnome-mplayer-dev-trusty.list <==
# deb http://ppa.launchpad.net/brandonsnider/gnome-mplayer-dev/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/brandonsnider/gnome-mplayer-dev/ubuntu trusty main

==> /etc/apt/sources.list.d/brandonsnider-gnome-mplayer-dev-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/brandonsnider/gnome-mplayer-dev/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/brandonsnider/gnome-mplayer-dev/ubuntu trusty main

==> /etc/apt/sources.list.d/brandonsnider-gnome-mplayer-dev-trusty.list.save <==
# deb http://ppa.launchpad.net/brandonsnider/gnome-mplayer-dev/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/brandonsnider/gnome-mplayer-dev/ubuntu trusty main

==> /etc/apt/sources.list.d/caffeine-developers-ppa-trusty.list <==
# deb http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/caffeine-developers-ppa-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/caffeine-developers-ppa-trusty.list.save <==
# deb http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/dropbox.list <==
deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu xenial main

==> /etc/apt/sources.list.d/dropbox.list.distUpgrade <==
deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu wily main

==> /etc/apt/sources.list.d/dropbox.list.save <==
deb [arch=i386,amd64] http://linux.dropbox.com/ubuntu xenial main

==> /etc/apt/sources.list.d/embrosyn-ubuntu-cinnamon-xenial.list <==
deb http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial main
# deb-src http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial main

==> /etc/apt/sources.list.d/embrosyn-ubuntu-cinnamon-xenial.list.save <==
deb http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial main
# deb-src http://ppa.launchpad.net/embrosyn/cinnamon/ubuntu xenial main

==> /etc/apt/sources.list.d/gambas-team-gambas3-trusty.list <==
# deb http://ppa.launchpad.net/gambas-team/gambas3/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/gambas-team/gambas3/ubuntu trusty main

==> /etc/apt/sources.list.d/gambas-team-gambas3-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/gambas-team/gambas3/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/gambas-team/gambas3/ubuntu trusty main

==> /etc/apt/sources.list.d/gambas-team-gambas3-trusty.list.save <==
# deb http://ppa.launchpad.net/gambas-team/gambas3/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/gambas-team/gambas3/ubuntu trusty main

==> /etc/apt/sources.list.d/getdeb.list <==
deb http://archive.getdeb.net/ubuntu xenial-getdeb apps

==> /etc/apt/sources.list.d/getdeb.list.distUpgrade <==
# deb http://archive.getdeb.net/ubuntu trusty-getdeb apps # disabled on upgrade to wily

==> /etc/apt/sources.list.d/getdeb.list.save <==
deb http://archive.getdeb.net/ubuntu xenial-getdeb apps

==> /etc/apt/sources.list.d/gnome-shell-extensions-ppa-trusty.list <==
# deb http://ppa.launchpad.net/gnome-shell-extensions/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/gnome-shell-extensions/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/gnome-shell-extensions-ppa-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/gnome-shell-extensions/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/gnome-shell-extensions/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/gnome-shell-extensions-ppa-trusty.list.save <==
# deb http://ppa.launchpad.net/gnome-shell-extensions/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/gnome-shell-extensions/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main 

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/kirillshkrogalev-ffmpeg-next-trusty.list <==
# deb http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu trusty main

==> /etc/apt/sources.list.d/kirillshkrogalev-ffmpeg-next-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu trusty main

==> /etc/apt/sources.list.d/kirillshkrogalev-ffmpeg-next-trusty.list.save <==
# deb http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu trusty main

==> /etc/apt/sources.list.d/lestcape-cinnamon-trusty.list <==
# deb http://ppa.launchpad.net/lestcape/cinnamon/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/lestcape/cinnamon/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/lestcape/cinnamon/ubuntu trusty main

==> /etc/apt/sources.list.d/lestcape-cinnamon-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/lestcape/cinnamon/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/lestcape/cinnamon/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/lestcape/cinnamon/ubuntu trusty main

==> /etc/apt/sources.list.d/lestcape-cinnamon-trusty.list.save <==
# deb http://ppa.launchpad.net/lestcape/cinnamon/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/lestcape/cinnamon/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/lestcape/cinnamon/ubuntu trusty main

==> /etc/apt/sources.list.d/mc3man-mplayer-test-trusty.list <==
# deb http://ppa.launchpad.net/mc3man/mplayer-test/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/mc3man/mplayer-test/ubuntu trusty main

==> /etc/apt/sources.list.d/mc3man-mplayer-test-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/mc3man/mplayer-test/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/mc3man/mplayer-test/ubuntu trusty main

==> /etc/apt/sources.list.d/mc3man-mplayer-test-trusty.list.save <==
# deb http://ppa.launchpad.net/mc3man/mplayer-test/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/mc3man/mplayer-test/ubuntu trusty main

==> /etc/apt/sources.list.d/mc3man-trusty-media-trusty.list <==
# deb http://ppa.launchpad.net/mc3man/trusty-media/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main

==> /etc/apt/sources.list.d/mc3man-trusty-media-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/mc3man/trusty-media/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main

==> /etc/apt/sources.list.d/mc3man-trusty-media-trusty.list.save <==
# deb http://ppa.launchpad.net/mc3man/trusty-media/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mc3man/trusty-media/ubuntu trusty main

==> /etc/apt/sources.list.d/megasync.list.distUpgrade <==
# deb http://mega.nz/linux/MEGAsync/xUbuntu_14.04/ ./ # disabled on upgrade to wily

==> /etc/apt/sources.list.d/megasync.list.save <==
deb http://mega.nz/linux/MEGAsync/xUbuntu_14.04/ ./

==> /etc/apt/sources.list.d/moorkai-cinnamon-trusty.list <==
# deb http://ppa.launchpad.net/moorkai/cinnamon/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/moorkai/cinnamon/ubuntu trusty main

==> /etc/apt/sources.list.d/moorkai-cinnamon-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/moorkai/cinnamon/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/moorkai/cinnamon/ubuntu trusty main

==> /etc/apt/sources.list.d/moorkai-cinnamon-trusty.list.save <==
# deb http://ppa.launchpad.net/moorkai/cinnamon/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/moorkai/cinnamon/ubuntu trusty main

==> /etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-xenial.list <==
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main

==> /etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-xenial.list.save <==
deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main

==> /etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list <==
# deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main

==> /etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main

==> /etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list.save <==
# deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main

==> /etc/apt/sources.list.d/noobslab-ubuntu-indicators-xenial.list <==
deb http://ppa.launchpad.net/noobslab/indicators/ubuntu xenial main
# deb-src http://ppa.launchpad.net/noobslab/indicators/ubuntu xenial main

==> /etc/apt/sources.list.d/noobslab-ubuntu-indicators-xenial.list.save <==
deb http://ppa.launchpad.net/noobslab/indicators/ubuntu xenial main
# deb-src http://ppa.launchpad.net/noobslab/indicators/ubuntu xenial main

==> /etc/apt/sources.list.d/opera-stable.list <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

deb https://deb.opera.com/opera-stable/ stable non-free #Opera Browser (final releases) disabled on upgrade to wily

==> /etc/apt/sources.list.d/opera-stable.list.distUpgrade <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

# deb https://deb.opera.com/opera-stable/ stable non-free #Opera Browser (final releases) disabled on upgrade to wily

==> /etc/apt/sources.list.d/opera-stable.list.save <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

deb https://deb.opera.com/opera-stable/ stable non-free #Opera Browser (final releases) disabled on upgrade to wily

==> /etc/apt/sources.list.d/pipelight-stable-trusty.list <==
# deb http://ppa.launchpad.net/pipelight/stable/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu trusty main

==> /etc/apt/sources.list.d/pipelight-stable-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/pipelight/stable/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu trusty main

==> /etc/apt/sources.list.d/pipelight-stable-trusty.list.save <==
# deb http://ppa.launchpad.net/pipelight/stable/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu trusty main

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_soundwheel_ubuntu.list <==
# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/soundwheel/ubuntu wily main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to wily

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_soundwheel_ubuntu.list.distUpgrade <==
# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/soundwheel/ubuntu wily main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to wily

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_soundwheel_ubuntu.list.save <==
# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/soundwheel/ubuntu wily main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to wily

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_youtube-to-mp3_ubuntu.list <==
# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/youtube-to-mp3/ubuntu wily main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to wily

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_youtube-to-mp3_ubuntu.list.distUpgrade <==
# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/youtube-to-mp3/ubuntu wily main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to wily

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_youtube-to-mp3_ubuntu.list.save <==
# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/youtube-to-mp3/ubuntu wily main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to wily

==> /etc/apt/sources.list.d/pywapi-devel-ppa-trusty.list <==

==> /etc/apt/sources.list.d/pywapi-devel-ppa-trusty.list.save <==

==> /etc/apt/sources.list.d/ravefinity-project-ppa-trusty.list <==
# deb http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu wily main # disabled on upgrade to wily

==> /etc/apt/sources.list.d/ravefinity-project-ppa-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu wily main # disabled on upgrade to wily

==> /etc/apt/sources.list.d/ravefinity-project-ppa-trusty.list.save <==
# deb http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu wily main # disabled on upgrade to wily

==> /etc/apt/sources.list.d/rvm-smplayer-trusty.list <==
# deb http://ppa.launchpad.net/rvm/smplayer/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu trusty main
# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu trusty main

==> /etc/apt/sources.list.d/rvm-smplayer-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/rvm/smplayer/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu trusty main
# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu trusty main

==> /etc/apt/sources.list.d/rvm-smplayer-trusty.list.save <==
# deb http://ppa.launchpad.net/rvm/smplayer/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu trusty main
# deb-src http://ppa.launchpad.net/rvm/smplayer/ubuntu trusty main

==> /etc/apt/sources.list.d/saiarcot895-ubuntu-flightgear-xenial.list <==
deb http://ppa.launchpad.net/saiarcot895/flightgear/ubuntu xenial main
# deb-src http://ppa.launchpad.net/saiarcot895/flightgear/ubuntu xenial main

==> /etc/apt/sources.list.d/saiarcot895-ubuntu-flightgear-xenial.list.save <==
deb http://ppa.launchpad.net/saiarcot895/flightgear/ubuntu xenial main
# deb-src http://ppa.launchpad.net/saiarcot895/flightgear/ubuntu xenial main

==> /etc/apt/sources.list.d/skoruppa-ppa-trusty.list.save <==

==> /etc/apt/sources.list.d/skunk-ubuntu-pepper-flash-xenial.list <==

==> /etc/apt/sources.list.d/skunk-ubuntu-pepper-flash-xenial.list.save <==

==> /etc/apt/sources.list.d/skype.list <==
# deb http://download.skype.com/linux/repos/debian/ stable non-free #Repository for Skype (stable)

==> /etc/apt/sources.list.d/skype.list.distUpgrade <==
# deb http://download.skype.com/linux/repos/debian/ stable non-free #Repository for Skype (stable)

==> /etc/apt/sources.list.d/skype.list.save <==
# deb http://download.skype.com/linux/repos/debian/ stable non-free #Repository for Skype (stable)

==> /etc/apt/sources.list.d/spotify.list <==
# deb http://repository.spotify.com stable non-free # disabled on upgrade to wily

==> /etc/apt/sources.list.d/spotify.list.distUpgrade <==
# deb http://repository.spotify.com stable non-free # disabled on upgrade to wily

==> /etc/apt/sources.list.d/spotify.list.save <==
# deb http://repository.spotify.com stable non-free # disabled on upgrade to wily

==> /etc/apt/sources.list.d/steam.list <==
# deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam # disabled on upgrade to wily
# deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam # disabled on upgrade to wily

==> /etc/apt/sources.list.d/steam.list.distUpgrade <==
# deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam # disabled on upgrade to wily
# deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam # disabled on upgrade to wily

==> /etc/apt/sources.list.d/steam.list.save <==
# deb [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam # disabled on upgrade to wily
# deb-src [arch=amd64,i386] http://repo.steampowered.com/steam/ precise steam # disabled on upgrade to wily

==> /etc/apt/sources.list.d/stebbins-handbrake-releases-trusty.list <==
# deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu trusty main

==> /etc/apt/sources.list.d/stebbins-handbrake-releases-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu trusty main

==> /etc/apt/sources.list.d/stebbins-handbrake-releases-trusty.list.save <==
# deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu trusty main

==> /etc/apt/sources.list.d/strukturag-libde265-trusty.list <==
# deb http://ppa.launchpad.net/strukturag/libde265/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main
# deb-src http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main
# deb-src http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main

==> /etc/apt/sources.list.d/strukturag-libde265-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/strukturag/libde265/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main
# deb-src http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main
# deb-src http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main

==> /etc/apt/sources.list.d/strukturag-libde265-trusty.list.save <==
# deb http://ppa.launchpad.net/strukturag/libde265/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main
# deb-src http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main
# deb-src http://ppa.launchpad.net/strukturag/libde265/ubuntu trusty main

==> /etc/apt/sources.list.d/sunab-sigil-release-trusty.list <==
# deb http://ppa.launchpad.net/sunab/sigil-release/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/sunab/sigil-release/ubuntu trusty main

==> /etc/apt/sources.list.d/sunab-sigil-release-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/sunab/sigil-release/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/sunab/sigil-release/ubuntu trusty main

==> /etc/apt/sources.list.d/sunab-sigil-release-trusty.list.save <==
# deb http://ppa.launchpad.net/sunab/sigil-release/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/sunab/sigil-release/ubuntu trusty main

==> /etc/apt/sources.list.d/thebernmeister-ubuntu-ppa-xenial.list <==
deb http://ppa.launchpad.net/thebernmeister/ppa/ubuntu xenial main
# deb-src http://ppa.launchpad.net/thebernmeister/ppa/ubuntu xenial main

==> /etc/apt/sources.list.d/thebernmeister-ubuntu-ppa-xenial.list.save <==
deb http://ppa.launchpad.net/thebernmeister/ppa/ubuntu xenial main
# deb-src http://ppa.launchpad.net/thebernmeister/ppa/ubuntu xenial main

==> /etc/apt/sources.list.d/thopiekar-mt7601-trusty.list <==
# deb http://ppa.launchpad.net/thopiekar/mt7601/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/thopiekar/mt7601/ubuntu trusty main

==> /etc/apt/sources.list.d/thopiekar-mt7601-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/thopiekar/mt7601/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/thopiekar/mt7601/ubuntu trusty main

==> /etc/apt/sources.list.d/thopiekar-mt7601-trusty.list.save <==
# deb http://ppa.launchpad.net/thopiekar/mt7601/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/thopiekar/mt7601/ubuntu trusty main

==> /etc/apt/sources.list.d/tiheum-ubuntu-equinox-xenial.list <==

==> /etc/apt/sources.list.d/tiheum-ubuntu-equinox-xenial.list.save <==

==> /etc/apt/sources.list.d/transmissionbt-ppa-trusty.list <==
# deb http://ppa.launchpad.net/transmissionbt/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/transmissionbt/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/transmissionbt-ppa-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/transmissionbt/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/transmissionbt/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/transmissionbt-ppa-trusty.list.save <==
# deb http://ppa.launchpad.net/transmissionbt/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/transmissionbt/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/ubuntuhandbook1-apps-trusty.list <==
# deb http://ppa.launchpad.net/ubuntuhandbook1/apps/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/ubuntuhandbook1/apps/ubuntu trusty main

==> /etc/apt/sources.list.d/ubuntuhandbook1-apps-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/ubuntuhandbook1/apps/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/ubuntuhandbook1/apps/ubuntu trusty main

==> /etc/apt/sources.list.d/ubuntuhandbook1-apps-trusty.list.save <==
# deb http://ppa.launchpad.net/ubuntuhandbook1/apps/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/ubuntuhandbook1/apps/ubuntu trusty main

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list <==
# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu wily main # disabled on upgrade to wily

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu wily main # disabled on upgrade to wily

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.save <==
# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu wily main # disabled on upgrade to wily

==> /etc/apt/sources.list.d/videolan-master-daily-trusty.list <==
# deb http://ppa.launchpad.net/videolan/master-daily/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/videolan/master-daily/ubuntu trusty main

==> /etc/apt/sources.list.d/videolan-master-daily-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/videolan/master-daily/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/videolan/master-daily/ubuntu trusty main

==> /etc/apt/sources.list.d/videolan-master-daily-trusty.list.save <==
# deb http://ppa.launchpad.net/videolan/master-daily/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/videolan/master-daily/ubuntu trusty main

==> /etc/apt/sources.list.d/videolan-stable-daily-trusty.list.save <==

==> /etc/apt/sources.list.d/weather-indicator-team-ppa-trusty.list.save <==

==> /etc/apt/sources.list.d/webupd8team-java-trusty.list <==
# deb http://ppa.launchpad.net/webupd8team/java/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-java-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/webupd8team/java/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-java-trusty.list.save <==
# deb http://ppa.launchpad.net/webupd8team/java/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-pulseaudio-eq-trusty.list <==
# deb http://ppa.launchpad.net/webupd8team/pulseaudio-eq/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/webupd8team/pulseaudio-eq/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/pulseaudio-eq/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-pulseaudio-eq-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/webupd8team/pulseaudio-eq/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/webupd8team/pulseaudio-eq/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/pulseaudio-eq/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-pulseaudio-eq-trusty.list.save <==
# deb http://ppa.launchpad.net/webupd8team/pulseaudio-eq/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/webupd8team/pulseaudio-eq/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/pulseaudio-eq/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-tor-browser-trusty.list <==
# deb http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-tor-browser-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-tor-browser-trusty.list.save <==
# deb http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-ubuntu-tor-browser-xenial.list <==
deb http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu xenial main
# deb-src http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu xenial main

==> /etc/apt/sources.list.d/webupd8team-ubuntu-tor-browser-xenial.list.save <==
deb http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu xenial main
# deb-src http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu xenial main

==> /etc/apt/sources.list.d/webupd8team-ubuntu-y-ppa-manager-xenial.list <==
deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu xenial main
# deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu xenial main

==> /etc/apt/sources.list.d/webupd8team-ubuntu-y-ppa-manager-xenial.list.save <==
deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu xenial main
# deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu xenial main

==> /etc/apt/sources.list.d/whatsapp-purple-ppa-trusty.list <==
# deb http://ppa.launchpad.net/whatsapp-purple/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/whatsapp-purple/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/whatsapp-purple-ppa-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/whatsapp-purple/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/whatsapp-purple/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/whatsapp-purple-ppa-trusty.list.save <==
# deb http://ppa.launchpad.net/whatsapp-purple/ppa/ubuntu wily main # disabled on upgrade to wily
# deb-src http://ppa.launchpad.net/whatsapp-purple/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/xenial-partner.list <==
# channel for the xenial (16.04) partner channel
# 
#:description:This channel contains the partner software for xenial
deb http://archive.canonical.com/ubuntu xenial partner

==> /etc/apt/sources.list.d/xenial-partner.list.save <==
# channel for the xenial (16.04) partner channel
# 
#:description:This channel contains the partner software for xenial
deb http://archive.canonical.com/ubuntu xenial partner

==> /etc/apt/sources.list.d/yktooo-ubuntu-ppa-xenial.list <==
deb http://ppa.launchpad.net/yktooo/ppa/ubuntu xenial main
# deb-src http://ppa.launchpad.net/yktooo/ppa/ubuntu xenial main

==> /etc/apt/sources.list.d/yktooo-ubuntu-ppa-xenial.list.save <==
deb http://ppa.launchpad.net/yktooo/ppa/ubuntu xenial main
# deb-src http://ppa.launchpad.net/yktooo/ppa/ubuntu xenial main
wolf@shaitan:~$ 
```

---

### Post by Bashing-om on 2016-05-30
Evil Wayz; Yuk !

Let's begin: - a huge amount of 3rd party sources .
These 2
> 
  44	deb [http://ubuntusatanic.org/hell](http://ubuntusatanic.org/hell) quantal main

remove .. having quantal as a source is a no no - release 12.10 is End_Of_Life .

Line 39 and 40 are correct in the file /etc/apt/sources.list .. the duplicate(s) to be removed are in the 3rd party directory "/etc/apt/sources.list.d" 
> 
#:description:This channel contains the partner software for xenial
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

==> /etc/apt/sources.list.d/xenial-partner.list.save <==
# channel for the xenial (16.04) partner channel
# 
#:description:This channel contains the partner software for xenial
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner


BK

As you have a huge amount of 3rd party software sources .. be aware there is a limit (40) to how many keys you can maintain .
How many do you presently have ?
```

ls /etc/apt/trusted.gpg.d | wc -l

```

I checked all the PPAs that are presently active on your system.. and all are valid ! wow !

[INDENT][INDENT]not so bad
[INDENT][INDENT][INDENT]after all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-06-03
Evil Wayz; Hey ??

Did I loose you ? What is your status ?

All done ? Then:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

with your closing remarks for resolution.

[INDENT][INDENT]'buntu
[INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by newbielennie on 2017-02-07
Thanks, this helped me. It's unfortunate the original poster didn't mark it as solved.

---

