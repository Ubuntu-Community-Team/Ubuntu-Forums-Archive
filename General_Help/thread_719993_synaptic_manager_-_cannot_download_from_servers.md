---
title: "synaptic manager - cannot download from servers"
date: 2008-03-09
forum: General Help
---

### Post by adammc on 2008-03-09
Hi guys,

I have just installed gutsy, im a ubuntu newb :)
Yesterday i was able to install some programs through synaptic manager, after changing the download servers a few times.

Today I am unable to download a thing, after trying multiple download servers?

Can anyone please help?

---

### Post by Oldsoldier2003 on 2008-03-09
> **adammc said:**
> Hi guys,

I have just installed gutsy, im a ubuntu newb :)
Yesterday i was able to install some programs through synaptic manager, after changing the download servers a few times.

Today I am unable to download a thing, after trying multiple download servers?

Can anyone please help?

the first thing to do is post the contents of the file /etc/apt/sources.list

---

### Post by adammc on 2008-03-09
thanks for the reply old soldier  :)


deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

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
deb [http://ftp.iinet.net.au/pub/ubuntu/](http://ftp.iinet.net.au/pub/ubuntu/) gutsy universe multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by Oldsoldier2003 on 2008-03-09
try going to System>Administration>software sources and making sure the top four boxes on the first tab are ticked.

then run synaptic again. lets see what happens.

---

### Post by adammc on 2008-03-09
Hi,

Following your suggestion I get the screen 'downloading file 7-12', it just hangs then I get failed errors.

I am able to browse the net..

---

### Post by adammc on 2008-03-09
ok, i used the choose server / find best server and it managed to reload. :)
Will I now have to keep changing download servers?

---

### Post by Oldsoldier2003 on 2008-03-09
> **adammc said:**
> Hi,

Following your suggestion I get the screen 'downloading file 7-12', it just hangs then I get failed errors.

I am able to browse the net..
sounds like you are having intermittent connectivity with your local mirrors. I wonder if its a normal thing in Au, perhaps try changing your sources to another mirror?

---

### Post by adammc on 2008-03-09
Hmmm.. I just downloaded and installed 'bluefish' through synaptic and then tried to search for another and the download failed. My internet then went?

I restarted the wireless connection showed that it weas trying to connect, it failed. I clicked it and it connected.

Any ideas what I can do to resolve this?
Any help would be greatly apreciated  :)

---

### Post by adammc on 2008-03-09
can anyone please help ?

---

### Post by jesusfreak107 on 2008-03-09
It looks like your wireless card is failing periodically, and the first time the Update Manager attempted to contact those servers, it was not working, so it blocked them out.  if you have ethernet, or if you figure out how to fix your wireless, then simply uncomment those repositories that it has commented out.  This looks like a weird Linux problem.  I checked the rep, and I was able to connect to it. you might try changing the server that your computer is trying to download from, or my original idea.

---

### Post by adammc on 2008-03-10
thanks for the reply.
I created an admin account, logged user out then logged in as admin but it wouldnt let me save the sources list?

---

### Post by Oldsoldier2003 on 2008-03-10
> **adammc said:**
> thanks for the reply.
I created an admin account, logged user out then logged in as admin but it wouldnt let me save the sources list?
edit the sources.list as superuser.

```
sudo nano /etc/apt/sources.list
```

or if you prefer gui editors

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by adammc on 2008-03-10
using 'sudo nano /etc/apt/sources.list'...
After removing all the commented out lines, what command do you give to save it?

---

### Post by Oldsoldier2003 on 2008-03-10
> **adammc said:**
> using 'sudo nano /etc/apt/sources.list'...
After removing all the commented out lines, what command do you give to save it?

ctrlX then y then enter

---

### Post by adammc on 2008-03-10
thanks old soldier, I was able to edit the sources list.
Now I just have to test if it drops out agin  :)

---

### Post by adammc on 2008-03-10
sigh***
Synaptic Manager is still failing. I am having to change servers till I find one that doesnt fail, very long process to download a single program!

Do you think its just cause of my wireless connection?

---

### Post by jesusfreak107 on 2008-03-10
yup, I this looks like a problem with the wireless connection.  I forgot if you said if you still have Windows, but if you do, or any other OS, boot onto it, and look for the driver to your wireless card.  Then, save it to a location that you can access from Ubuntu, and reboot.  Once in Ubuntu, try the new driver, and see if that works.

---

### Post by adammc on 2008-03-11
what extension would the wireless driver have?

---

