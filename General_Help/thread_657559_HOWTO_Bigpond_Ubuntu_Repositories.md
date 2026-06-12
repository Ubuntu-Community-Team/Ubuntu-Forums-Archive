---
title: "HOWTO: Bigpond Ubuntu Repositories"
date: 2008-01-03
forum: General Help
---

### Post by madverb on 2008-01-03
For all you people who are in the same crappy position as me and are capped at 12GB downloads with Telstra Bigpond (Australian internet sucks) here is a copy of my sources.list using the Bigpond mirror. This lets you download a lot of software without affecting your usage on Bigpond.
Replace all the text in your /etc/apt/sources.list file with the code below.
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.# Line commented out by installer because it failed to verify:
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://mirror.gamearena.com.au/ubuntu/ gutsy-security main restricted
deb http://mirror.gamearena.com.au/ubuntu/ gutsy-security universe
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-security multiverse
deb http://mirror.gamearena.com.au/ubuntu/ gutsy-updates universe main restricted
deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb http://mirror.gamearena.com.au/ubuntu/ gutsy main universe restricted
deb http://au.archive.ubuntu.com/ubuntu/ gutsy multiverse
```
Multiverse and Source Code isn't available through the Bigpond mirror. I sent them an email asking why... waiting on response.
Then obviously type in terminal:
```
sudo apt-get update
```
Edit:
Response from Bigpond
> Hi, 
Multiverse isn't mirrored for disk space reasons and legal concerns.
We're looking at including the source code packages as well though soon. 
Regards,
David

---

### Post by AlexThomson_NZ on 2008-01-03
Ahh you lucky guys across the ditch...

Here in NZ I'm on a 6GB cap, and no free national traffic :(  ...although we have had own own repos for a while now- makes a big difference

---

### Post by enbuyukfener on 2008-01-29
Have you considered BigPond's new 25GB Liberty plan? It's $10 more a month.

And seeing this is near top of relevant searches, I'll point out that sources have been added, I am running an updated list here:
[http://pastebin.ca/882686](http://pastebin.ca/882686)

---

### Post by dcstar on 2008-01-30
Anyone in Australia with an ISP that has unmetered downloads from the PIPE network has at least three choices of repositories on that network in the default Ubuntu list of "Other" repositories in Synaptic: Internode, Pacific.net and Netspace.

Simply selecting one of these can save a lot of quota, and going to the mirror sites also allows you to download ISO images without hurting your quota - very handy.

---

### Post by hyper_ch on 2008-01-30
you could condense it to:

```

deb http://mirror.gamearena.com.au/ubuntu/ gutsy-security main restricted universe multiverse
deb http://mirror.gamearena.com.au/ubuntu/ gutsy-updates main restricted universe multiverse
deb http://mirror.gamearena.com.au/ubuntu/ gutsy main restricted universe multiverse

```

---

### Post by madverb on 2008-02-04
They don't have mirrors for multiverse.

---

### Post by Jeremy23 on 2008-07-13
As distributors of binaries covered by the GPL, Telstra BigPond is legally obligated to distribute the source as well upon request.

As you have asked them to provide the source code, they are *obligated* to provide it in some way or another. See section 6 of the GPLv3.

However, judging from section 6 (d) in the license: (emphasis mine)

> d) Convey the object code by offering access from a designated place (gratis or for a charge), and offer equivalent access to the Corresponding Source in the same way through the same place at no further charge. You need not require recipients to copy the Corresponding Source along with the object code. **If the place to copy the object code is a network server, the Corresponding Source may be on a different server (operated by you or a third party) that supports equivalent copying facilities, provided you maintain clear directions next to the object code saying where to find the Corresponding Source.** Regardless of what server hosts the Corresponding Source, you remain obligated to ensure that it is available for as long as needed to satisfy these requirements.

It seems that they are legally obligated to have a link or some code instructing people on how to add the official Ubuntu Source Code repo into their sources.list file, and make sure that the Ubuntu mirror doesn't go down.

---

