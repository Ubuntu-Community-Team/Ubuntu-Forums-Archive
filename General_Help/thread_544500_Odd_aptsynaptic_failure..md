---
title: "Odd apt/synaptic failure."
date: 2007-09-06
forum: General Help
---

### Post by grupotux on 2007-09-06
Weird synaptic error message:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/k3b/libk3b2_1.0.3-0ubuntu3~feisty1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/k3b/libk3b2_1.0.3-0ubuntu3~feisty1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/k3b/k3b_1.0.3-0ubuntu3~feisty1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/k3b/k3b_1.0.3-0ubuntu3~feisty1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/k/k3b/libk3b2-mp3_1.0.3-0ubuntu3~feisty1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/k/k3b/libk3b2-mp3_1.0.3-0ubuntu3~feisty1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/s/sbackup/sbackup_0.10.4~feisty1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/s/sbackup/sbackup_0.10.4~feisty1_all.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


Here's the sources.list file:

#
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://pr.archive.ubuntu.com/ubuntu/](http://pr.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

# deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

# deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main


I have no idea where this comes from (excerpt found line by line):

Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

Any thoughts out there?

---

### Post by bapoumba on 2007-09-06
Do you have a proxy set up?

---

### Post by grupotux on 2007-09-06
No proxy setup, I am connected to a DSL modem by way of a Linksys router. The sam problem takes place if I connect via dialup modem using kppp.

---

### Post by bapoumba on 2007-09-06
Could you please look in the following files if there is any proxy declared:
```
cat /etc/apt/apt.conf
cat /etc/environment
cat .bashrc
```
also run and make sure the setting is on "direct":
```
gnome-network-preferences
```

---

### Post by grupotux on 2007-09-06
Aha!, here is the culprit:

cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"

# +ANON_MARK+ Don't change this while anon-proxy manages this variable.
# +ANON_MARK+ To take back control of it run dpkg-reconfigure and tell
# +ANON_MARK+ debconf not to set this variable for you.
HTTP_PROXY=http://localhost:4001 # +ANON_MARK+           # <---
http_proxy=http://localhost:4001 # +ANON_MARK+              # <---
------------------------------------------------------------------------------------------------------------

gnome-network-preferences is set for direct internet connection.

Is it sufficient to comment out the two « *ANON_MARK* » lines, or is it better to run dpkg-reconfigure?

---

### Post by grupotux on 2007-09-07
Commenting out the following two lines in the /etc/environment file

HTTP_PROXY=http://localhost:4001 # +ANON_MARK+ 
http_proxy=http://localhost:4001 # +ANON_MARK+ 

and rebooting the machine solved the problem.

Thank you for you help, bapoumba. If there's a cleaner way
to do this, please convey. I've no idea as to how or why the 
/etc/environment file was modified to add this disfunctional 
encumbrance.

---

### Post by bapoumba on 2007-09-07
Okay fine, this was what I was about to suggest.
Did you install Anon Proxy (or did it get installed by a game for ex?).
Should be fine now :)

---

### Post by grupotux on 2007-09-07
Yes, the issue is resolved. No, I did not install it, in fact, I didn't know it existed. I am now aware that «anon-proxy» is a symlink of «proxytest».

Could this localhost port 4001 rubbish be a freak side effect that warrants investigation?

I hate to think that an enthusiastic newbie might reinstall the distribution in frustration or worse, abandon Linux altogether thus to fall back into the black hole (read not anti-matter, but anti-freedom) branded by the waving MS logo.

**Kudos, cheers; hooray for the Community!!!**

---

### Post by bapoumba on 2007-09-07
You may have played with proxies at some point. I've seen this (and got to help) several times already. Once, anon-proxy got installed with a game, and helping the user with it, we got down to the /etc/environment file too.

The update error is typical of a non functional proxy setting.

Glad to see you got it fixed :)

---

### Post by grupotux on 2007-09-08
Ah, quite so; I often allow my grandson, Amadís, to use my Toshiba Satellite to play games on the Internet. Thus, the problem: «a non-functional proxy setting». Please investigate,

God Speed!

---

