---
title: "sources.list"
date: 2016-12-21
forum: General Help
---

### Post by cmcanulty on 2016-12-21
I am getting multiple error suddenly about /etc/apt/sources.list I don't see any duplicates. Here is the error list. Thank you


```

W: Target Packages (partner/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Packages (partner/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en_CA) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target Translations (partner/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11 (partner/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:4
W: Target DEP-11-icons (partner/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:45 and /etc/apt/sources.list.d/xenial-partner.list:
```4

and here is the /etc/apt/sources.list

```
# deb cdrom:[Xubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu xenial main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted
# deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu xenial universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial universe
deb http://archive.ubuntu.com/ubuntu xenial-updates universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu xenial multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://archive.ubuntu.com/ubuntu xenial-updates multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://archive.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://archive.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://archive.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
deb http://download.virtualbox.org/virtualbox/debian xenial contrib

```


I am unclear as it lists /etc/apt/sources.list and /etc/apt/sources.list.d is there supposed to be nothing in appearing in both lists?

---

### Post by oldfred on 2016-12-21
Check this:
ls -l /etc/apt/sources.list.d

And then every file in that list. It would seem you have duplicates there.

---

### Post by papibe on 2016-12-21
Hi cmcanulty.

Could you open a terminal, run this command and post back the results?
```
find /etc/apt/  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```

Regards.

---

### Post by cmcanulty on 2016-12-22
I did check that file also see below. Unless they count the commented out lines or the ones that are name and name.save as the same I don't see duplicates. Thank you


```
cmcanulty@ubuntu1:~$ 
cmcanulty@ubuntu1:~$ 
cmcanulty@ubuntu1:~$ find /etc/apt/  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list

     1	# deb cdrom:[Xubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main multiverse restricted universe
     2	
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	deb http://archive.ubuntu.com/ubuntu xenial main restricted
     6	# deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted
    11	# deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team, and may not be under a free licence. Please satisfy yourself as to
    15	## your rights to use the software. Also, please note that software in
    16	## universe WILL NOT receive any review or updates from the Ubuntu security
    17	## team.
    18	deb http://archive.ubuntu.com/ubuntu xenial universe
    19	# deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial universe
    20	deb http://archive.ubuntu.com/ubuntu xenial-updates universe
    21	# deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-updates universe
    22	
    23	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    24	## team, and may not be under a free licence. Please satisfy yourself as to 
    25	## your rights to use the software. Also, please note that software in 
    26	## multiverse WILL NOT receive any review or updates from the Ubuntu
    27	## security team.
    28	deb http://archive.ubuntu.com/ubuntu xenial multiverse
    29	# deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial multiverse
    30	deb http://archive.ubuntu.com/ubuntu xenial-updates multiverse
    31	# deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    32	
    33	## N.B. software from this repository may not have been tested as
    34	## extensively as that contained in the main release, although it includes
    35	## newer versions of some applications which may provide useful features.
    36	## Also, please note that software in backports WILL NOT receive any review
    37	## or updates from the Ubuntu security team.
    38	deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
    39	# deb-src http://ca.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    40	
    41	## Uncomment the following two lines to add software from Canonical's
    42	## 'partner' repository.
    43	## This software is not part of Ubuntu, but is offered by Canonical and the
    44	## respective vendors as a service to Ubuntu users.
    45	deb http://archive.canonical.com/ubuntu xenial partner
    46	# deb-src http://archive.canonical.com/ubuntu xenial partner
    47	
    48	deb http://archive.ubuntu.com/ubuntu xenial-security main restricted
    49	# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
    50	deb http://archive.ubuntu.com/ubuntu xenial-security universe
    51	# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
    52	deb http://archive.ubuntu.com/ubuntu xenial-security multiverse
    53	# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
    54	deb http://download.virtualbox.org/virtualbox/debian xenial contrib
    55	
    56	

/etc/apt/sources.list.d/fontforge-ubuntu-fontforge-xenial.list

     1	deb http://ppa.launchpad.net/fontforge/fontforge/ubuntu xenial main
     2	# deb-src http://ppa.launchpad.net/fontforge/fontforge/ubuntu xenial main

/etc/apt/sources.list.d/ubuntu-mate-dev-ubuntu-ppa-xenial.list


/etc/apt/sources.list.d/xenial-partner.list

     1	# channel for the xenial (16.04) partner channel
     2	# 
     3	#:description:This channel contains the partner software for xenial
     4	deb http://archive.canonical.com/ubuntu xenial partner

/etc/apt/sources.list.d/george-edison55-ubuntu-nitroshare-xenial.list

     1	deb http://ppa.launchpad.net/george-edison55/nitroshare/ubuntu xenial main
     2	# deb-src http://ppa.launchpad.net/george-edison55/nitroshare/ubuntu xenial main

/etc/apt/sources.list.d/remmina-ppa-team-ubuntu-remmina-next-xenial.list

     1	deb http://ppa.launchpad.net/remmina-ppa-team/remmina-next/ubuntu xenial main
     2	# deb-src http://ppa.launchpad.net/remmina-ppa-team/remmina-next/ubuntu xenial main

/etc/apt/sources.list.d/google-chrome.list

     1	### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2	# You may comment out this entry, but any other modifications may be lost.
     3	deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main

/etc/apt/sources.list.d/vikoadi-ubuntu-ppa-xenial.list

     1	deb http://ppa.launchpad.net/vikoadi/ppa/ubuntu xenial main

/etc/apt/sources.list.d/upubuntu-com-ubuntu-sdk-xenial.list


/etc/apt/sources.list.d/pmcenery-ubuntu-ppa-xenial.list


/etc/apt/sources.list.d/ubuntu-mate-dev-ubuntu-xenial-mate-xenial.list


/etc/apt/sources.list.d/neovim-ppa-ubuntu-unstable-xenial.list

     1	deb http://ppa.launchpad.net/neovim-ppa/unstable/ubuntu xenial main
     2	# deb-src http://ppa.launchpad.net/neovim-ppa/unstable/ubuntu xenial main

/etc/apt/sources.list.d/nilarimogard-ubuntu-webupd8-xenial.list

     1	deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial main

/etc/apt/sources.list.d/webupd8team-ubuntu-java-xenial.list

     1	deb http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main
     2	# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu xenial main

/etc/apt/sources.list.d/mint.list


/etc/apt/sources.list.d/jonabeck-ubuntu-ppa-xenial.list


/etc/apt/sources.list.d/mjblenner-ubuntu-ppa-hal-xenial.list

     1	deb http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu xenial main
     2	# deb-src http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu xenial main

/etc/apt/sources.list.d/phablet-team-ubuntu-tools-xenial.list

     1	deb http://ppa.launchpad.net/phablet-team/tools/ubuntu xenial main
     2	# deb-src http://ppa.launchpad.net/phablet-team/tools/ubuntu xenial main

/etc/apt/sources.list.d/xubuntu-dev-ubuntu-extras-xenial.list

     1	deb http://ppa.launchpad.net/xubuntu-dev/extras/ubuntu xenial main
     2	# deb-src http://ppa.launchpad.net/xubuntu-dev/extras/ubuntu xenial main

/etc/apt/sources.list.d/skype-stable.list

     1	deb [arch=amd64] https://repo.skype.com/deb stable main

/etc/apt/sources.list.d/vivaldi.list

     1	### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2	# You may comment out this entry, but any other modifications may be lost.
     3	deb http://repo.vivaldi.com/stable/deb/ stable main

/etc/apt/sources.list.d/langdalepl-ubuntu-gvfs-mtp-xenial.list

     1	# deb http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu xenial main
     2	# deb-src http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu xenial main

/etc/apt/sources.list.d/webupd8team-ubuntu-unstable-xenial.list

     1	deb http://ppa.launchpad.net/webupd8team/unstable/ubuntu xenial main
     2	# deb-src http://ppa.launchpad.net/webupd8team/unstable/ubuntu xenial main
     3	# deb-src http://ppa.launchpad.net/webupd8team/unstable/ubuntu xenial main

/etc/apt/sources.list.d/pipelight-ubuntu-stable-xenial.list

     1	deb http://ppa.launchpad.net/pipelight/stable/ubuntu xenial main
     2	# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu xenial main

/etc/apt/sources.list.d/mkusb-ubuntu-ppa-xenial.list

     1	deb http://ppa.launchpad.net/mkusb/ppa/ubuntu xenial main
     2	# deb-src http://ppa.launchpad.net/mkusb/ppa/ubuntu xenial main
     3	# deb-src http://ppa.launchpad.net/mkusb/ppa/ubuntu xenial main

/etc/apt/sources.list.d/alexlarsson-ubuntu-flatpak-xenial.list


/etc/apt/sources.list.d/webupd8team-ubuntu-haguichi-xenial.list


/etc/apt/sources.list.d/google-earth.list

     1	### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2	# You may comment out this entry, but any other modifications may be lost.
     3	deb http://dl.google.com/linux/earth/deb/ stable main

/etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list

     1	deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial main
     2	# deb-src http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial main
cmcanulty@ubuntu1:~$ 
```

---

### Post by papibe on 2016-12-22
Thanks.

Line 45 of /etc/apt/sources.list is repeated in the 4th line of /etc/apt/sources.list.d/xenial-partner.list
```
deb http://archive.canonical.com/ubuntu xenial partner
```
It looks like a system that was on a previous version, then ppa's were added to get it closer to 16.04, and then finally upgrated to 16.04.

At this moment you don't need the ppa that generated the file /etc/apt/sources.list.d/xenial-partner.list. Either remove that ppa, or simple remove the file.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by dragonfly41 on 2016-12-22
I'm just adding that the package Y PPA Manager GUI might help you.

[https://launchpad.net/~webupd8team/+archive/ubuntu/y-ppa-manager](https://launchpad.net/~webupd8team/+archive/ubuntu/y-ppa-manager)

Use the Advanced Tab to delete duplicate PPA's.

---

### Post by cmcanulty on 2016-12-22
OK thanks I looked forever and missed that

---

