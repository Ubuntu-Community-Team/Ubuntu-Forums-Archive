---
title: "few app's not loading in 7.10."
date: 2007-10-26
forum: General Help
---

### Post by TRDownShift on 2007-10-26
Hi, about last week i updated to 7.10 with the update manager and now some of my programs wont load, and alot of installers i've downloaded wont start, it's not that theres an error.... they just dont start, plane and simple, i click.... computer trys to do something but then it's like i never clicked anything T.T i would like to know if anyone has fixed this. it's kinda starting to tick me off :P i download something but nothing happens wen i click, no matter how many times i click or what. one of them is even add/remove programs LMFAO.... any way, thanks for any help, later :D

---

### Post by Maestro23 on 2007-10-26
> **TRDownShift said:**
> Hi, about last week i updated to 7.10 with the update manager and now some of my programs wont load, and alot of installers i've downloaded wont start, it's not that theres an error.... they just dont start, plane and simple, i click.... computer trys to do something but then it's like i never clicked anything T.T i would like to know if anyone has fixed this. it's kinda starting to tick me off :P i download something but nothing happens wen i click, no matter how many times i click or what. one of them is even add/remove programs LMFAO.... any way, thanks for any help, later :D

You can't install anything from the repos?

Please post your **sources.list** file.

> cat /etc/apt/sources.list

*Your sources are probably all commented out with #

---

### Post by TRDownShift on 2007-10-27
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

# deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main
# deb-src [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main
# deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

ah, alright, theres the list file. i really dont know what wrong though it might be looking me in the face and i wouldnt know it cus i really dont understand haff of linux yet ^^"

EDIT: sorry you got the idea my package manager doesn't work (though the updates wont just load with a click i have right click and hit install all updates) it's mainly just app's that won't load, like if i go under applications and click add/remove, nothing happens, and it's ben happening alot with alot of programs ^^"

---

### Post by TRDownShift on 2007-10-29
Ok, you guys gota help me... this is really starting to tick me off with the random app's just not working at all, i just found out listen music player doesn't load, and just now wen i was going to burn a CD the Cd burning app doesn't work.... whats with this... T.T 

i mean if you guys really have no clue just tell me how to downgrade back to 7.04 without loseing all my crap cus 7.10 is starting to get on my last nerve.... >:(

---

### Post by TRDownShift on 2007-10-30
bump.


still haven't found a fix, and i haven't found anyone who has had or is having the same prob i am... just now i found out whatever app it is that installs .deb packages doesn't run, and the terminal closes at random, some times even the instant i open terminal it closes. 

this new release just isn't running well for me at all. so far it seems like with each passing day i'm finding more and more that "just doesn't load" :confused:


i'm thinking by the end of the week if this isn't fixed i'm going to format everything and just load a fresh install of 7.04 becus i really have no clue at all whats doing this. well, how could i have a clue, i've only used linux now for near 2 moths or so.... i think... im not good at keeping track of time :lolflag:

---

### Post by TRDownShift on 2007-10-30
ahh.... this time i seem to have goten somewhere with it XD i tryed runing one of the app's in terminal and got this back. (i ran 2 of the app's, both gave back the same error so i don't see a point in posting both.

ImportError: could not import gtk
Traceback (most recent call last):
  File "/usr/lib/listen/listen.py", line 40, in <module>
    import gtk,gobject, bonobo
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents

umm... help at this point would be kick *** cus i how no clue what to do from here ^^" thanks XD

---

