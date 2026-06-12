---
title: "[SOLVED] Update Manager Error 302, Failed to fetch updates"
date: 2008-05-30
forum: General Help
---

### Post by timcape on 2008-05-30
When I try to run the Update Manager, a window pops up that says 

"An error has occurred. The following details are provided:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-ubuntu-modules-2.6.22/linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.38_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-ubuntu-modules-2.6.22/linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.38_i386.deb)
  302 Moved Temporarily


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.22.1.1-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.22.1.1-0ubuntu3_i386.deb)
  302 Moved Temporarily


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.22.1.1-0ubuntu3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.22.1.1-0ubuntu3_all.deb)
  302 Moved Temporarily


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.22.1.1-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.22.1.1-0ubuntu3_i386.deb)
  302 Moved Temporarily


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gdb/gdb_6.8-1ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gdb/gdb_6.8-1ubuntu2_i386.deb)
  302 Moved Temporarily


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.20.6-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.20.6-0ubuntu2_i386.deb)
  302 Moved Temporarily


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-about_2.22.2-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-about_2.22.2-0ubuntu1_i386.deb)
  302 Moved Temporarily


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-desktop-data_2.22.2-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-desktop-data_2.22.2-0ubuntu1_all.deb)
  302 Moved Temporarily


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/libgnome-desktop-2_2.22.2-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/libgnome-desktop-2_2.22.2-0ubuntu1_i386.deb)
  302 Moved Temporarily"


The same thing happens when I try to add a program using Add/Remove Applications. Is this because everything has actually been moved temporarily, or is there something wrong on my end?

---

### Post by pedro_orange on 2008-05-30
Check your software sources.
(System > Admin > Software Sources)

Do you have repos in there you can't access? 
Might be an idea to remove 3rd party ones and just stick with the Ubuntu ones.

Might be an idea to post your sources.lst file

---

### Post by werries on 2008-05-30
i've only ever seen that with internet issues. but i guess if you're posting from that computer, thats not the case is it

---

### Post by timcape on 2008-05-30
I removed all of my 3rd party repos, but still got the same error.
here's my sources.lst file (after I removed the 3rd party repos):

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe multiverse main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted

---

### Post by timcape on 2008-05-31
Anyone have any ideas as to what's going on?

---

### Post by zvacet on 2008-05-31
System>admin<software sources> see if you have all cheched under ubuntu softwaer and updates tab.If you don´t do it.If you do change server to main.

---

### Post by timcape on 2008-05-31
That's what I've got

---

### Post by pedro_orange on 2008-06-01
Ok. 

Try this:

```
sudo nano -w /etc/apt/sources.list
```

Then clean it out and stick this in instead:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ru.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ru.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
```

I think your sources.list got foobar'd when you upgraded. Replacing it with a clean HH sources.list should sort it. 
Let us know how you get on.

---

### Post by timcape on 2008-06-01
I'm still getting the same error messages.

This might be a shot in the dark, especially since I'm a complete noob...Ever since I came home from school for the summer, I haven't been able to update. I installed Ubuntu in November while I was at school in Ohio and I've only installed updates while on campus. Now that I'm at home in Wisconsin, I can't update anything and I'm getting the "Failed to fetch updates" error message. Could it possibly have something to do with my change of location? or something with a network setting I'm overlooking?

---

### Post by pedro_orange on 2008-06-02
I'm skeptical that a change in location would effect your ability to update. The location of the files you are trying to access have not moved.
I'm in England, and if I click the links in your original post I can download the .tar.gz file you link. 

I'm not sure what's left to suggest. We can try cleaning and rebuilding your apt-cache.

```

sudo apt-get clean
sudo apt-get update
```

Then we can try triggering the updating from the command line:

```
sudo apt-get upgrade
```

Good luck!

---

### Post by timcape on 2008-06-04
It looks like that worked, but I still can't add programs from add/remove. Doing it from the terminal works though. Any insight on why?

btw, thank you so much for helping me out so far!

---

