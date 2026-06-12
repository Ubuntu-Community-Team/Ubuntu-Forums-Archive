---
title: "Help with Synaptic"
date: 2007-07-10
forum: General Help
---

### Post by 2ndgenerationphan on 2007-07-10
I just made the switch to Ubuntu a few months ago with the help of a co-worker.  I love the system, but am not too cool about the fact that I can't install anything using Synaptic.
Anytime I want to install ANYTING using Synpatic, I get this message:

[B]E: Type 'wget' is not known on line 58 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.[/B]

It's driving me insane!!

Please someone help me.

-H

---

### Post by ThrobbingBrain66 on 2007-07-10
could you please post the contents of your sources.list file?

In or around line 58 (oddly enough :)) you have to remove 'wget' because apt doesn't recognize it.  Most likely it's from a 3rd party repo that you added.

(use gedit /etc/apt/sources.list and copy and paste the contents here)

---

### Post by 2ndgenerationphan on 2007-07-10
I hope this is what you wanted--

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main multiverse universe #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

## Automatix repo
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main


#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy multiverse #Added by software-properties
#AUTOMATIX REPOS END

wget [http://www.getautomatix.xom/apt/key.gpg.asc](http://www.getautomatix.xom/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C
sudo apt-key add

wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc) 
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C
sudo apt-key add
sudo apt- get update
wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc) gpg --import key.gpg.asc gpg --export --armor 521A9C7C
sudo apt-key add
sudo apt- get update
sudo apt-get install automatix2

--H

---

### Post by FuturePilot on 2007-07-10
Just delete everything after 
#AUTOMATIX REPOS END
Then run
```
sudo apt-get update
```

---

### Post by 2ndgenerationphan on 2007-07-11
I deleted the code , but I can't save anything.  It's a read-only file.
Any suggestions?
-H

---

### Post by AlexenderReez on 2007-07-11
you should 

> gksudo gedit /etc/apt/sources.list

---

### Post by gepatino on 2007-07-11
For editing as superuser:

gksudo gedit /etc/apr/sources.list

---

### Post by dpar on 2007-07-11
Use gksudo gedit  /etc/apt/souces.list
to edit the files


Edit:I came in last again:(

---

### Post by 2ndgenerationphan on 2007-07-11
OMG...thank you!!
It works now!!
-H

---

