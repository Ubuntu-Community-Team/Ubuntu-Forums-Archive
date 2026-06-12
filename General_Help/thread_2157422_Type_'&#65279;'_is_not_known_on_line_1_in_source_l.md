---
title: "Type '&#65279;' is not known on line 1 in source list /etc/apt/sources.list"
date: 2013-06-25
forum: General Help
---

### Post by Bananarchy on 2013-06-25
Hello
I tried to install tor, and one of the steps required me to add the source to my /etc/apt/sources.list file, which I did. I wasn't able to save it with gedit despite using the chown command so I used libre to edit and save it (That might have caused this problem). Now whenever I try to run 'sudo apt-get update' or install software via the terminal, I get the error 'E: Type '&#65279;' is not known on line 1 in source list /etc/apt/sources.list'. I edited the sources.list file back to it's original state but I still get this error.
Any help would be greatly appreciated.

---

### Post by Cheesemill on 2013-06-25
Can you post the contents of the file please...
```
cat /etc/apt/sources.list
```

---

### Post by Bananarchy on 2013-06-25
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring-updates main restricted
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring universe
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring universe
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring-updates universe
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring multiverse
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring-updates multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main

---

### Post by MidnightGrey on 2013-06-25
> **Bananarchy said:**
> Hello
I wasn't able to save it with gedit despite using the chown command so I used libre to edit and save it 

I think you may have inadvertently taken ownership of the file / and away from root.
can you paste this output:
```

ls /etc/apt/ -l
```

edit: what were the instructions you followed for installing tor? because they seem a bit iffy if you had to manually edit sources.list, can you paste them here.

---

### Post by Bananarchy on 2013-06-25
Sorry for the delay
> total 76drwxr-xr-x 2 root     root      4096 juin  24 22:45 apt.conf.d
drwxr-xr-x 2 root     root      4096 avril 13 01:51 preferences.d
-rw-r--r-- 1 santiago santiago  3109 juin  25 14:30 sources.list
drwxr-xr-x 2 root     root      4096 juin  24 23:33 sources.list.d
-rw-r--r-- 1 santiago santiago  3106 juin  24 23:25 sources.list.save
-rw------- 1 root     root      1200 juin  25 14:24 trustdb.gpg
-rw-r--r-- 1 root     root     21578 juin  25 14:24 trusted.gpg
-rw-r--r-- 1 root     root     21578 juin  25 14:24 trusted.gpg~
drwxr-xr-x 2 root     root      4096 juin  25 14:24 trusted.gpg.d




And I used the guide on the tor website found here
[https://www.torproject.org/docs/debian.html.en](https://www.torproject.org/docs/debian.html.en)

---

### Post by MidnightGrey on 2013-06-25
sources.list and sources.list.save should both be root, not santiago(you).
do ```
sudo chown root:root sources.list*
``` to reverse it back and you should be fine now.

---

### Post by MidnightGrey on 2013-06-25
use this command to edit the sources.list file as root:
```
gksu gedit sources.list
```

---

### Post by Bananarchy on 2013-06-25
I still get the same error, unfortunately

---

### Post by steeldriver on 2013-06-25
How did you revert back to the original file? editing using LibreOffice may have left some non-printing / control characters which are not visible in the text but are tripping up the package management tools - if so you may be able to see what's wrong with

```
cat -net /etc/apt/sources.list
```

---

### Post by Bananarchy on 2013-06-25
Here's what came up:
> 1	M-oM-;M-?# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted$     2	$
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to$
     4	# newer versions of the distribution.$
     5	deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring main restricted$
     6	deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring main restricted$
     7	$
     8	## Major bug fix updates produced after the final release of the$
     9	## distribution.$
    10	deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring-updates main restricted$
    11	deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring-updates main restricted$
    12	$
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu$
    14	## team. Also, please note that software in universe WILL NOT receive any$
    15	## review or updates from the Ubuntu security team.$
    16	deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring universe$
    17	deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring universe$
    18	deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring-updates universe$
    19	deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring-updates universe$
    20	$
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu $
    22	## team, and may not be under a free licence. Please satisfy yourself as to $
    23	## your rights to use the software. Also, please note that software in $
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu$
    25	## security team.$
    26	deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring multiverse$
    27	deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring multiverse$
    28	deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring-updates multiverse$
    29	deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring-updates multiverse$
    30	$
    31	## N.B. software from this repository may not have been tested as$
    32	## extensively as that contained in the main release, although it includes$
    33	## newer versions of some applications which may provide useful features.$
    34	## Also, please note that software in backports WILL NOT receive any review$
    35	## or updates from the Ubuntu security team.$
    36	deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse$
    37	deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse$
    38	$
    39	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted$
    40	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted$
    41	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe$
    42	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe$
    43	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse$
    44	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse$
    45	$
    46	## Uncomment the following two lines to add software from Canonical's$
    47	## 'partner' repository.$
    48	## This software is not part of Ubuntu, but is offered by Canonical and the$
    49	## respective vendors as a service to Ubuntu users.$
    50	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner$
    51	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner$
    52	$
    53	## This software is not part of Ubuntu, but is offered by third-party$
    54	## developers who want to ship their latest software.$
    55	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main$
    56	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main$



I'm new to Ubuntu so I am not sure what I'm supposed to be watching out for

---

### Post by MidnightGrey on 2013-06-25
> **Bananarchy said:**
> Here's what came up:

I'm new to Ubuntu so I am not sure what I'm supposed to be watching out for

This:
1	**M-oM-;M-?**# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted$

---

### Post by Bananarchy on 2013-06-25
How can I edit that out? It doesn't appear if I open it in gedit or libre.

---

### Post by steeldriver on 2013-06-25
You may have to do something like this - it backs up your current file (just in case) then removes any characters up to the first # or d (for deb)

```
sudo sed -i.bak -r '1 s/([^#d]*)(.*)/\2/' /etc/apt/sources.list
```

After that, try the 'cat -net' again to see if the non-printing characters are gone

---

### Post by Bananarchy on 2013-06-25
That worked, phew! Thanks for all the help everybody

---

