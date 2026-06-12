---
title: "Update error"
date: 2013-08-09
forum: General Help
---

### Post by Hungry Man on 2013-08-09
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/restricted amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring-updates/restricted amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring-updates_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring-updates/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring-updates_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

apt-get update doesn't fix it.

---

### Post by Bashing-om on 2013-08-09
Hungry Man; Hi !

The package manager advises you that there are duplicated source entries .....so;
check the file "/etc/apt/sources.list" for duplicated lines...then->
Check the files in the 3rd party directory "/etc/apt/sources.list.d/" for any files duplicated; as well as a repeat of any line in any of those files from the primary source file "/etc/apt/sources.list" file. 

[INDENT][INDENT][INDENT]just try'n to help
[/INDENT][/INDENT][/INDENT]

---

### Post by Hungry Man on 2013-08-09
Is there some way to check for duplicates? There's quite a large number of entries that are very similar.

---

### Post by Bashing-om on 2013-08-09
Hungry Man; Hey,

Unfortunately I do not know of an easy way to search the duplicated entries.
What I generally do is load the file into the file editor "gedit" ... open up all the files in separate tabs and one line at a time enter a portion of the line into "search for text" field -> hit the "next" button and see if it finds a next. Do this for every entry enabled ...Yeah time consuming ... I just do not know of a better advisement that is as certain to find the duplicates.

Others with greater experience may advise better methods ...this is ubuntu and there are excellent file manipulation tools, one has just to be aware of them.


[INDENT][INDENT]short on skills
[/INDENT][/INDENT]

---

### Post by ibjsb4 on 2013-08-09
Let us have a look, post it :)

In terminal:

```
cat /etc/apt/sources.list
```

---

### Post by Hungry Man on 2013-08-10
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) raring-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-backports main restricted universe multiverse


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-proposed main universe multiverse restricted
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main

---

### Post by Bashing-om on 2013-08-10
Hungry Man; What I see:The 3rd line in the first  stanza:
> 
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) raring-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates main restricted

as a repeat of the  1st line in this stanza:
> 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security multiverse


I suggest removing the first instance (3rd line) and running:
```

sudo apt-get update
sudo apt-get upgrade

```
once more and see what results.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Hungry Man on 2013-08-10
That worked! Thanks very much.

---

### Post by gautam_chand on 2013-08-10
i just parchased new laptop.  it has preinstalled ubuntu12.04.  it is not supporting flv files in vlc, mpplayer, sm player, xine,totem player so i plan to upgrade it to 12.10 and it suddenly stop upgrading and after that my upgrade manager  and software center not opening... it show following massage

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal_multiverse_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.' 

please solve my problem........

---

### Post by Bashing-om on 2013-08-10
@ gautam_chand; Hi ! Welcome to the forum.
Though your problem is similar .. it is not the of the same cause. You should have opened up your own thread -try'n to keep the forum tidy.
However, try this:
Terminal codes:
```

sudo apt-get clean
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
sudo apt-get upgrade

```
The "apt-get" command will repopulate the data base that was removed. -> advise us of what results.

[INDENT][INDENT]ubuntu, always fixable
[/INDENT][/INDENT]

---

### Post by ibjsb4 on 2013-08-10
@ gautam_chand;

If your not familiar with the terminal

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

