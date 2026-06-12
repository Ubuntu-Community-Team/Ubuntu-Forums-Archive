---
title: "installing from universe repos not possible, have checked it in Software Sources"
date: 2007-06-05
forum: General Help
---

### Post by mopi on 2007-06-05
Hi al.

Perhaps I'm missing something trivial but according to this link
[http://packages.ubuntu.com/feisty/games/gnugo]("http://packages.ubuntu.com/feisty/games/gnugo") the package gnugo should be in universe. However, in "Add/Remove Applications" I search for "gnugo" and select "All" category. No match shows up for gnugo. 

In "Software Sources" I have "Community-maintained Open Source software (universe)" selected. It was like that when I first opened the application. I have tried setting repo server to both my default Swedish mirror and the main server.

What to do?
Thanks in advance.

---

### Post by dfreer on 2007-06-05
could you post your /etc/apt/sources.list file please?

---

### Post by mopi on 2007-06-05
Here it is.

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://se.archive.ubuntu.com/ubuntu/ feisty main restricted universe
deb-src http://se.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://se.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe
deb-src http://se.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://se.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://se.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://se.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://se.archive.ubuntu.com/ubuntu/ feisty-security main restricted universe
deb-src http://se.archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb http://se.archive.ubuntu.com/ubuntu/ feisty-security multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ feisty-security multiverse
```

---

### Post by aysiu on 2007-06-05
I see Universe in there.

Can you post the output of this command? ```
sudo apt-get update && sudo apt-get install gnugo
```

---

### Post by wpshooter on 2007-06-05
Have you tried going into Synaptic and doing RELOAD ?

---

### Post by WW on 2007-06-05
The same thing happens in Dapper.  gnugo does not show up in "Add/Remove Applications", but it does show up in Synaptic.  Does the "Add/Remove Applications" program only access a subset of the Ubuntu repository?

---

### Post by aysiu on 2007-06-05
> **WW said:**
> The same thing happens in Dapper.  gnugo does not show up in "Add/Remove Applications", but it does show up in Synaptic.  Does the "Add/Remove Applications" program only access a subset of the Ubuntu repository?
Yes.

Add/Remove generally display popular point-and-click applications for desktop users.

Synaptic displays everything available.

---

### Post by WW on 2007-06-05
Well, there you go, mopi.  Use Synaptic to install gnugo (or use the command aysiu gave earlier).

The "Advanced" button in "Add/Remove Applications" will switch you to Synaptic, if you already have "Add/Remove..." running.

---

### Post by mopi on 2007-06-05
Synaptic solved it!

I didn't know that Add/Remove... only displayed a subset, good to know. Btw, I have no Advanced button in Add/Remove Applications. It there something I need to configure to see that?

---

### Post by WW on 2007-06-05
Not necessarily--I am still running Dapper (6.06).  The program has probably changed in Feisty (7.04).

---

### Post by mopi on 2007-06-05
Yes probably. 

Thank you all for helping out.

---

### Post by aysiu on 2007-06-05
**Advanced** got removed for Edgy and Feisty, for some mysterious reason.

---

