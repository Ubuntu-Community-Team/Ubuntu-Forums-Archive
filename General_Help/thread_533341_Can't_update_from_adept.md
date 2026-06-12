---
title: "Can't update from adept"
date: 2007-08-23
forum: General Help
---

### Post by G_Stewart on 2007-08-23
You know how Ubuntu lets you know there are updates available? Well, I can't update. I have done it regularly for a while, but the update for Foomatic GUI is a broken and I can not download a thing. I have tried to unselect Foomatic, but it won't let me and when I try to download I get...

There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. 

I hit OK and it just ends. I mean it closes nicely, no hang ups... but no update either.

Help....


Gary

---

### Post by aysiu on 2007-08-24
Close Adept and Add/Remove

Press Alt-F2 and type ```
konsole
```

In the terminal that opens up, paste in this command: ```
sudo dpkg --configure -a
``` Then paste the resulting output (including error messages) back here.

---

### Post by G_Stewart on 2007-08-24
Here's what I got:

dpkg: dependency problems prevent configuration of foomatic-gui:
 foomatic-gui depends on python (<< 2.4); however:
  Version of python on system is 2.5.1-0ubuntu3.
dpkg: error processing foomatic-gui (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 foomatic-gui

Hope it helps.

---

### Post by aysiu on 2007-08-24
Can you post the output of these two commands, then? ```
sudo apt-get -f install
``` ```
cat /etc/apt/sources.list
```

---

### Post by G_Stewart on 2007-08-24
First response:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package sherpath needs to be reinstalled, but I can't find an archive for it.

---

### Post by G_Stewart on 2007-08-24
Second response:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by aysiu on 2007-08-24
Your repositories list looks okay. Try this: ```
sudo aptitude update
sudo aptitude install foomatic-gui
```

---

### Post by G_Stewart on 2007-08-24
It went well until I ran the second run of code. That went through to the end, almost, and output the following...

E: I wasn't able to locate a file for the sherpath package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

---

### Post by G_Stewart on 2007-08-28
The issue is surely this "sherpath" file. I can't delete it (so I can reinstall a good one) and I can't use any of the auto systems to download or update anything.
Can anyone help me fix this "sherpath" file?

Gary:confused:

---

### Post by G_Stewart on 2007-09-02
](*,)
I've even gone into the shell and tried to get a new sherpath. It seems to work, 

$ sudo apt-get install sherpath
Reading package lists... Done
Building dependency tree
Reading state information... Done

but at the end I get this:

E: The package sherpath needs to be reinstalled, but I can't find an archive for it.

What am I doing? Or what's wrong?
Gary

---

### Post by G_Stewart on 2007-09-03
I Googled sherpath and found out it was a groupware program which seems to be no longer supported. I didn't even know it was on the system.
But, I am still on square one... I can't delete it, I can't over-write and I still can't update anything else.

Gary

---

### Post by G_Stewart on 2007-09-15
OK, here's where I am now. I tried to use apt-get to get a new sherpath and I get this:

desktop:~$ sudo apt-get install sherpath
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I also tried this:

desktop:~$ sudo apt-get install sherpath_0.92.deb
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


What do these lines mean?

:confused:
Gary

---

