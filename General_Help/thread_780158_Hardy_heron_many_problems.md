---
title: "Hardy heron many problems"
date: 2008-05-03
forum: General Help
---

### Post by vavoem on 2008-05-03
First off i really really really regret upgrading to hardy heron
I was running 7.04 without a hitch but was really interested in kde4.

So i gathered all my currage and updated the system to 7.10 first.
Seemed to be going allright but the ATI proprietary driver in 7.10 doesn't support my Radeon 9000 any more so i had to go with the very very very very slow open source driver to continue the update to 8.04. 

Ok so now i upgraded to 8.04
Not only is the Open source ati driver crawling my system to a snailspeed.
It is drawing artifacts everywhere. I don't even want to think about desktop effects.

I have dependency problems when i ran sudo apt-get install kubuntu-kde4-desktop

Kdm is broken but because this laptop is for daily use and my wife uses it i had to go with gdm.

kde 3.5 has kde4 packages everywhere

My amarok database was gone had to rebuild it (minor irritation)
My wlan driver was messed up (but fixed this myself had to install it with ndiswrapper and a new firmware)

Amarok won't play asx files anymore
My modem wont work any more (not really important i hardly use it)

System settings crashes

So from being one happy edgy efter i am now a hardly heron.
Since downgrading is no option because of other stuff still running.

To the positive side the kde4 programs seem to run much snappier then the kde3.5 programs.

Please can someone help me out because i dont know where to start anymore

My lappie is a dell latitude d600

---

### Post by ghost_ryder35 on 2008-05-03
> **vavoem said:**
> First off i really really really regret upgrading to hardy heron
I was running 7.04 without a hitch but was really interested in kde4.
 
So i gathered all my currage and updated the system to 7.10 first.
Seemed to be going allright but the ATI proprietary driver in 7.10 doesn't support my Radeon 9000 any more so i had to go with the very very very very slow open source driver to continue no worries.
 
Ok so now i am ready to upgrade to 8.04
Not only is the opensource ati driver crawling my system to a snailspeed.
It is drawing artifacts everywhere. I don't even want to think about dekstop effects.
I have dependancy problems when sudo apt-get install kubuntu-kde4-desktop
Kdm is broken because this laptop is for daily use and my wife uses it a have to go with gdm.
kde 3.5 has kde4 packages everywhere
my amarok database is gone 
my wlan driver was messed up (but fixed this myself)
Amarok won't play asx files anymore
my modem wont work any more and i feel like working on 
 
So from being one happy edgy efter i am now a hardly heron.
Since downgrading is no option because of other stuff still running.
To the positive side the kde4 programs seem to run much snappier then the kde3.5 programs.
 
Please can someone help me out because i dont know where to start anymore
backup your home directory and install a fresh copy of hardy heron.  there have been many horor stories of the upgrades going very wrong.  a fresh install should fix your problem.  once you installed the system restore your home directory and all your old programs and files should be back.

---

### Post by Zorael on 2008-05-03
I concur; you'll avoid a whole lot of frustration by doing a clean install.

---

### Post by vavoem on 2008-05-05
My word and i thought, with ubuntu, or any linux devirant for that matter, i never had to resort to such windowlike measures.
thanks! But no thanks!
I am not waiting to reinstall my lamp installation my samba my openldap my ftp server etc etc etc etc.

So i didn't

I followed this link to get my kde back to pure KDE [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
(i think i must have accidentaly installed gnome in the process)

Which fixed my dependency hell

I did
sudo dpkg-reconfigure kdm to fix my kdm

i than ran sudo aptitude install kubuntu-kde4-desktop

Only problem left is my videodriver.
I wander if there is a way to use the 7.04 propieatary driver Does anyone know?

---

