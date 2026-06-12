---
title: "Add/remove program error"
date: 2007-05-27
forum: General Help
---

### Post by jasond123 on 2007-05-27
I got this error when i tried to install a program usiung the add/remove program feature

Could not download all repository indexes

[http://za.archive.ubuntu.com/ubuntu/...6/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/...6/Packages.gz:) Sub-process gzip returned an error code (1)
[http://za.archive.ubuntu.com/ubuntu/...ce/Sources.gz:](http://za.archive.ubuntu.com/ubuntu/...ce/Sources.gz:) Sub-process gzip returned an error code (1)
[http://za.archive.ubuntu.com/ubuntu/...6/Packages.gz:](http://za.archive.ubuntu.com/ubuntu/...6/Packages.gz:) Sub-process gzip returned an error code (1)

after this is shown it fails to download or remove any software. Newbie to linux. Please HELP. Greatly Appreciated.

---

### Post by taurus on 2007-05-27
Edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and remove the **za.** from all the repos.  Save it and from a terminal, run

```
sudo aptidude update
sudo aptitude upgrade
```

---

### Post by jasond123 on 2007-05-27
hey, sorry but i just have a question. i entered the code into the terminal and a whole bunch of stuff came came up. must i remove .za everywere i see it or just certain ones? sorry.

---

### Post by taurus on 2007-05-27
All the lines/repos in /etc/apt/sources.list.

---

### Post by jasond123 on 2007-05-27
it does not recognise the first command of 
sudo aptidude update
and i did what you said i deleted the following in red

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
[COLOR="Red"]deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty universe[/COLOR]

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
[COLOR="Red"]deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty multiverse[/COLOR]

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

one of the three error messages disapperead ie [http://za.archive.ubuntu.com/ubuntu/...ce/Sources.gz:](http://za.archive.ubuntu.com/ubuntu/...ce/Sources.gz:) Sub-process gzip returned an error code (1). 
did i not delete the correct ones?

---

### Post by arpitubun on 2008-06-17
Hey I am new to ubuntu,I could not  find how to post problem on forum .I tried here.
I am not able to install any of the programs in Applications=>Add/Remove
It shows the following error

W: Failed to fetch [http://sg.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_SG.bz2](http://sg.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_SG.bz2)  Could not resolve 'sg.archive.ubuntu.com'


Please help!

---

