---
title: "Securing Xubuntu"
date: 2007-10-15
forum: General Help
---

### Post by spliner on 2007-10-15
I recently loaded up Xubuntu 7.04 on a spare machine since it only had 128mb ram, and was primarily going to be used as a Nessus server.  Anyway, it works great for that, but I ran into an issue I am having difficulty with.  When I scan the machine itself I come up with this vulerability:

It was discovered that a buffer overflow of the RPC library of the MIT
Kerberos reference implementation allows the execution of arbitrary code.
The oldstable distribution (sarge) is not affected by this problem.
For the stable distribution (etch) this problem has been fixed in
version 1.4.4-7etch3.
For the unstable distribution (sid) this problem has been fixed in
version 1.6.dfsg.1-7.
We recommend that you upgrade your Kerberos packages.

How to I go about fixing that issue?  I have done a system upgrade, re-scanned and keep coming up with that same vulnerability.

Thanks in advance.. and yes I am a newb to Linux/Ubuntu.

Also:  I found this ... [http://www.ubuntu.com/usn/usn-511-1](http://www.ubuntu.com/usn/usn-511-1)

It tells me which packages to upgrade but not "how" to upgrade them.  Nothing shows up in my synaptic manager.  The Kerberos website itself has only debian docs, which are about as clear as mud for me at the moment.  I'm at the following guides stage of my learning, and unfortunately need some detailed instructions.

---

### Post by kerry_s on 2007-10-15
you'll get that alot, you got to remember that the *ubuntu's are a snapshot of debian, so they freeze it at a certain point, after that your just stuck.

you should use straight debian for your serving needs. it's a heck of alot more stable and faster.

xfce4-> [http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

---

### Post by bodhi.zazen on 2007-10-15
> **kerry_s said:**
> you'll get that alot, you got to remember that the *ubuntu's are a snapshot of debian, so they freeze it at a certain point, after that your just stuck.

you should use straight debian for your serving needs. it's a heck of alot more stable and faster.

xfce4-> [http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

ooo

That is one of my favorite iso's

---

### Post by kerry_s on 2007-10-15
> **bodhi.zazen said:**
> ooo

That is one of my favorite iso's

it's okay if you want to get up and running fast. i prefer the small net installer->
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso)

i like doing mine from scratch. i usually start with a base install, then add the lenny repo's and dist-upgrade, after that i just pick what i want.

currently, i'm using->
file type jfs
apt-get install xserver-xorg-video-neomagic xorg synaptic jwm emelfm iceweasel swapd


installed about 4 days ago. on this install, i'm trying the jfs with deadline elevator for lower cpu usage and realtime performance, i'm using auto swap(uses swap file) instead of a swap partion. i only have the browser with flash,mplayer,xpdf, no extensions, i'm using a hosts block file to block ad's. nothing is slow on this 450mhz 256ram clunker. :)

---

### Post by bodhi.zazen on 2007-10-15
Very nice set up kerry_s

---

### Post by kerry_s on 2007-10-15
> **bodhi.zazen said:**
> Very nice set up kerry_s

thanks, i'm really liking this setup. i'm really surprised at how such little changes, like using jfs instead of ext2 that i usually use, barely hd activity and cpu usage is amazingly low. using swapd instead of a swap partion makes everything use ram first, i have the swap setting set to start when my free mem reaches less than 75% of my total, i have to be doing alot for it to even make a swap. the only thing i'm worried about is i use DSL for recovery if i bone my system and it don't do jfs, so i made my former swap into storage ext2 just in case.

i may keep this setup at least a month, till i figure out what i want to try next. :lolflag:

---

### Post by spliner on 2007-10-16
So anyone have instructions on how to install the latest Kerberos?  I'd rather not bother reinstalling until 7.10 comes out.

Here are the packages listed to upgrade:

For Ubuntu 7.04:
&#8226; libkadm55 1.4.4-5ubuntu3.2
&#8226; librpcsecgss3 0.14-2ubuntu1.1

So how do I upgrade those?

libkadm55 and librpcsecgss3 show as the latest versions but "sudo apt-get install 1.4.4-5ubuntu3.2" and "sudo apt-get install 0.14-2ubuntu1.1" return the error: "Couldn't find package".  Am I missing the package source somewhere?

---

### Post by kerry_s on 2007-10-16
> **spliner said:**
> So anyone have instructions on how to install the latest Kerberos?  I'd rather not bother reinstalling until 7.10 comes out.

Here are the packages listed to upgrade:

For Ubuntu 7.04:
&#8226; libkadm55 1.4.4-5ubuntu3.2
&#8226; librpcsecgss3 0.14-2ubuntu1.1

So how do I upgrade those?

libkadm55 and librpcsecgss3 show as the latest versions but "sudo apt-get install 1.4.4-5ubuntu3.2" and "sudo apt-get install 0.14-2ubuntu1.1" return the error: "Couldn't find package".  Am I missing the package source somewhere?


do you have all the repository's turned on? they should be in fiesty-security repo.
[http://www.mail-archive.com/feisty-changes@lists.ubuntu.com/msg08386.html](http://www.mail-archive.com/feisty-changes@lists.ubuntu.com/msg08386.html)
[http://www.securityfocus.com/archive/1/478608/30/450/threaded](http://www.securityfocus.com/archive/1/478608/30/450/threaded)

---

### Post by spliner on 2007-10-16
enabling the backports sources seems to be triggering an update of gnupg, I'll post again if that alleviates the problem.  Those are the only sources in the sources.list file that were not enabled.

---

### Post by spliner on 2007-10-16
enabling the backports seems to have solved that paticular problem with gnupg.  It has now updated to a stable version 1.4.6-2.

Now all I have left on a Nessus scan of the machine is something about Iceweasel and warnings about network shares being enumerated.

I would like to have this thing secure so I can be put on the public net and used as a remote scanner from time to time.  Thanks for the help!

Spliner

---

### Post by kerry_s on 2007-10-16
```

## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ feisty free
deb http://medibuntu.sos-sts.com/repo/ feisty non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free
deb-src http://medibuntu.sos-sts.com/repo/ feisty non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.)
deb http://archive.canonical.com/ubuntu feisty-commercial main

## Listen
#deb http://theli.free.fr/packages/ feisty listen

```

---

