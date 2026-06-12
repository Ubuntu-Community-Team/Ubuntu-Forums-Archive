---
title: "apt-pinning not working as expected; what have I misunderstood?"
date: 2012-12-26
forum: General Help
---

### Post by ArlieS on 2012-12-26
Hi Folks,

I'm attempting to maintain a basically 12.04 (precise) system, with a limited number of packages from 12.10 (quantal). What I seem to have done is convinced my system that I want to upgrade to quantal. The result is that I don't dare update anything, which implies not picking up security fixes - this is distinctly sub-optimal, so I'd appreciate some help.

Being ignorant of apt pinning, I followed the instructions at [http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html) modifying URLs etc. to convert from debian to ubuntu, and then did something like ```
sudo apt-get install pidgin-sipe/quantal
``` 

Now if I do:
```

$ sudo apt-get update
$ sudo apt-get upgrade
```

It cheerfully tells me:
> 
...
280 upgraded, 0 newly installed, 0 to remove and 189 not upgraded.
Need to get 129 MB of archives.
After this operation, 2,270 kB of additional disk space will be used.
Do you want to continue [Y/n]?                      


I responded with n.

Here are the files I believe to be relevant:
```

$ cat /etc/apt/sources.list
# /etc/apt/sources.list

# Main distribution - precise pangolin aka 12.04.1 LTS
deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse

# 12.10 distribution, for an extremely limited set of purposes
deb http://archive.ubuntu.com/ubuntu/ quantal main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ quantal-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ quantal-updates main restricted universe multiverse

``````

$ cat /etc/apt/preferences
Package: *
Pin: release a=precise
Pin-Priority: 700

Package: *
Pin: release a=quantal
Pin-Priority: 650

``````

$ ls -l /etc/apt/preferences.d/
total 0

```
[/code]
```

$ cat /etc/apt/preferences 
Package: * 
Pin: release a=precise Pin-Priority: 700  Package: * Pin: release a=quantal Pin-Priority: 650

```
```

$ ls -l /etc/apt/preferences.d/ 
total 0
```
I originally thought this was merely an issue with the Unity update manager, resulting in the following thread:  [http://ubuntuforums.org/showthread.php?p=12412602#post12412602](http://ubuntuforums.org/showthread.php?p=12412602#post12412602) I'm repeating the same thing here now that I've determined that I get the same undesired behaviour using apt-get commands directly.

---

### Post by bodhi.zazen on 2012-12-26
Mixing repositories is asking for trouble. What you should do, IMO, is use pinning for a **[color=red]single package**[/color](or set of packages), and not all the packages. 

"apt-get upgrade" is going to make a mess and likely eventually break your system.

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

---

### Post by ArlieS on 2012-12-26
> **bodhi.zazen said:**
> Mixing repositories is asking for trouble. What you should do, IMO, is use pinning for a **[COLOR=red]single package[/COLOR]**(or set of packages), and not all the packages. 

"apt-get upgrade" is going to make a mess and likely eventually break your system.

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

Ouch. I'd originally tried simply downloading the needed package, and installing it, but it required later versions of various other packages. Naturally I only remember one of those for sure. 

What I'm gathering from experience (and e.g. the link you posted) is that there's no supported/sane way to pick up later versions of a package _and all its dependencies_, without messing up everything else.

So if I go this route, I'd probably have to bring everything back to 12.04/precise, if I can, then pin the package I want, then recursively pin dependencies till I can get the result to install.

Worse, and hopefully inaccurate - but reading between the lines, I'm wondering whether there's a problem with bogus dependencies. What happens if pkg foo uses library bar, relying only on interfaces that were current as of bar version 2.0 - but the foo pkg is built on/for a Ubuntu system where bar is at version 10.0? Is foo going to be packaged as requiring bar 10.0?  This could get very messy if bar is libc :-(

This would account for the suggestion of building from source - which is what I would have tried, except (a) the package I want (pidgin-sipe) has a warning that it's hard to get all its dependencies together to build it and (b) I don't understand how executables built from source packages - or source tarballs - interact with the package management system. What happens if/when precise wants to update something that I've since rebuilt from a source package, or that something I've built depends upon? 

And most importantly from my POV - am I likely to shoot myself in the foot trying this recursive binding hack? Should I try building from source? Should I give up - the pidgin-sipe I installed is in any case not doing what I expected it to do - and if so, how do I roll back from where I am now?

Put another way, what I know about package management can probably be written on my thumbnail in large print ;-) I clearly need a clue transfusion. I'm glad folks here are generally willing to help.

---

### Post by bodhi.zazen on 2012-12-26
I would (in order)

1. Upgrade Ubuntu.

2. Build from source.

3. Ask for the package to be back ported.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

[https://wiki.ubuntu.com/UbuntuBackports](https://wiki.ubuntu.com/UbuntuBackports)

But yes, pinning is a bit of work and if you take shortcuts can cause carnage.

---

### Post by ArlieS on 2012-12-26
I tried simply reducing the priority for quantal in /etc/apt/preferences from 500 to 100, following examples in [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports). Now apt-get upgrade only wants to install 72 packages, but finds another 91 it wants to keep  back. This is a much more believable number for what's now a couple of weeks of updates to 12.04, though it seems a little high; I wish I could determine what it would have reported the day I made the original change. 

There seems to be something strange in the apt-get mechanism (as used by Ubuntu), as well as the possibility that mixed Ubuntu releases simply aren't stable.  

Does anyone know whether it's safe to get rid of the quantal sources, and update normally? Also what would happen to packages at a version beyond anything available in precise, if I did an apt-get update and apt-get upgrade with only precise packages in the sources list?

[Update: I noticed that Debian examples used "Pin: release a=foo" whereas Ubuntu examples used "Pin: release n=foo" in the preferences file, and made that change as well as the numeric priority change.  Now "apt-get upgrade" only wants to upgrade 33 packages and keep back 3. It looks like what I have is a collection of bugs in my /etc/apt/preferences and possibly also /etc/apt/sources.list - I don't suppose people would appreciate a bug report like "documentation incomprehensible to at least one naive luser :-("

How could I have determined that archive names don't match release codenames on Ubuntu, and the archive names aren't especially useful?  I'm not even sure what apt-get means by those 2 terms.]

---

### Post by ArlieS on 2012-12-26
Even with the 2 changes to /etc/apt/preferences, the output of "apt-cache policy" still makes me nervous. 

Some lines with quantal show priority 100, as intended, but some show priority 500.
And some lines with precise show priority 700, again as intended, but some of them show priority 500. Presumably the 500s will be confused.

```

$ cat /etc/apt/preferences
Package: *
Pin: release n=precise
Pin-Priority: 700

Package: *
Pin: release n=quantal
Pin-Priority: 100

``````

$ apt-cache policy
100 /var/lib/dpkg/status
     release a=now
 500 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe Translation-en
 500 http://archive.ubuntu.com/ubuntu/ quantal-updates/restricted Translation-en
 500 http://archive.ubuntu.com/ubuntu/ quantal-updates/multiverse Translation-en
 500 http://archive.ubuntu.com/ubuntu/ quantal-updates/main Translation-en
 100 http://archive.ubuntu.com/ubuntu/ quantal-updates/multiverse i386 Packages
     release v=12.10,o=Ubuntu,a=quantal-updates,n=quantal,l=Ubuntu,c=multiverse
     origin archive.ubuntu.com
 100 http://archive.ubuntu.com/ubuntu/ quantal-updates/universe i386 Packages
     release v=12.10,o=Ubuntu,a=quantal-updates,n=quantal,l=Ubuntu,c=universe
     origin archive.ubuntu.com
...
 500 http://security.ubuntu.com/ubuntu/ precise-security/universe Translation-en
 500 http://security.ubuntu.com/ubuntu/ precise-security/restricted Translation-
en
 500 http://security.ubuntu.com/ubuntu/ precise-security/multiverse Translation-
en
 500 http://security.ubuntu.com/ubuntu/ precise-security/main Translation-en
 700 http://security.ubuntu.com/ubuntu/ precise-security/multiverse i386 Package
s
     release v=12.04,o=Ubuntu,a=precise-security,n=precise,l=Ubuntu,c=multiverse
     origin security.ubuntu.com
 700 http://security.ubuntu.com/ubuntu/ precise-security/universe i386 Packages
     release v=12.04,o=Ubuntu,a=precise-security,n=precise,l=Ubuntu,c=universe
     origin security.ubuntu.com
 700 http://security.ubuntu.com/ubuntu/ precise-security/restricted i386 Package
s
     release v=12.04,o=Ubuntu,a=precise-security,n=precise,l=Ubuntu,c=restricted
     origin security.ubuntu.com
 700 http://security.ubuntu.com/ubuntu/ precise-security/main i386 Packages
     release v=12.04,o=Ubuntu,a=precise-security,n=precise,l=Ubuntu,c=main
     origin security.ubuntu.com
 700 http://security.ubuntu.com/ubuntu/ precise-security/multiverse amd64 Packag
es
     release v=12.04,o=Ubuntu,a=precise-security,n=precise,l=Ubuntu,c=multiverse
     origin security.ubuntu.com
...

```

---

### Post by dcstar on 2012-12-28
> **bodhi.zazen said:**
> Mixing repositories is asking for trouble. What you should do, IMO, is use pinning for a **[color=red]single package**[/color](or set of packages), and not all the packages. 

"apt-get upgrade" is going to make a mess and likely eventually break your system.


+1 - it is an incredibly stupid thing to do.

Add in the fact that the Synaptic Pinning is not full respected by the underlying APT pinning so certain updates replace pinned packages anyway (this is an ancient bug) and you are virtually guaranteed to commit your system to an early doom by taking this path.

---

### Post by ArlieS on 2012-12-28
> **dcstar said:**
> +1 - it is an incredibly stupid thing to do.

Add in the fact that the Synaptic Pinning is not full respected by the underlying APT pinning so certain updates replace pinned packages anyway (this is an ancient bug) and you are virtually guaranteed to commit your system to an early doom by taking this path.

I found a couple of relevant bug reports at [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/42178](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/42178) and [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/67146](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/67146) and a how to blog that claims it's a simple case of separate but identically formatted preferences files ([http://sysblogd.wordpress.com/2007/09/09/pinning-a-debpackage-systemwide-for-apt-get-and-synaptic-alike/](http://sysblogd.wordpress.com/2007/09/09/pinning-a-debpackage-systemwide-for-apt-get-and-synaptic-alike/)). 

But even if all this is current, it might not be my problem. I'm on 12.04, where the synaptic package manager  - apparently a GUI front end tool - is no longer the Ubuntu default, replaced with the "Ubuntu software center", which appears to be an independent development line, if Wikipedia is to be believed: [http://en.wikipedia.org/wiki/Ubuntu_Software_Center](http://en.wikipedia.org/wiki/Ubuntu_Software_Center)

I don't know whether Ubuntu software center is in fact bug-for-bug compatible with the synaptic package manager - but in any case, I'm now only using apt-get, and still seeing strange effects.

---

