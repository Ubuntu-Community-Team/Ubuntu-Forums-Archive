---
title: "pcscd unmet dependencies - DoD CAC software"
date: 2015-11-04
forum: General Help
---

### Post by joecasanova on 2015-11-04
Hi all,

I'm attempting to set up my laptop so I can log into DoD systems using my military CAC and smart card reader(s).  I'm following these directions:  [https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard)

My issue is that pcscd will not install due to what appears to be a broken dependancy... a package it is dependant on is labelled as breaking pcscd so pcscd will not install.

Is there a way that I can force the install?  Or is that bad?  I'm kind of new to using Linux as a workstation, been using it as a server for a few years now.  Any advice would be helpful.

> joe@JoeTop:~$ sudo apt-get install libpcsclite-dev pcscd pcsc-tools libccid coolkey
[sudo] password for joe: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pcsc-tools is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libpcsclite-dev : Depends: libpcsclite1 (= 1.8.10-1ubuntu1) but 1.8.14-1ubuntu1 is to be installed
 libpcsclite1 : Breaks: libpcsclite-dev (< 1.8.14-1ubuntu1) but 1.8.10-1ubuntu1 is to be installed
                Breaks: pcscd (< 1.8.14-1ubuntu1) but 1.8.10-1ubuntu1 is to be installed
 pcscd : Depends: libpcsclite1 (= 1.8.10-1ubuntu1) but 1.8.14-1ubuntu1 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.



---

### Post by ian-weisser on 2015-11-04
> **joecasanova said:**
> libpcsclite-dev : Depends: libpcsclite1 (= 1.8.10-1ubuntu1) but 1.8.14-1ubuntu1 is to be installed

I use CAC on Ubuntu. It can be done.

You have a version conflict.
1.8.10-1ubuntu1 is from 14.04
1.8.14.1ubuntu1 is from 15.04/15.10

You seem to be running 15.04 or 15.10, but you are trying to install ancient 14.04 packages.
Any idea why?
Did you add any 'trusty' repos?

---

### Post by joecasanova on 2015-11-05
I'm running ubuntu 14.04.  I have not added any repos.

How can I force it to install 1.8.10-1ubuntu1?

---

### Post by ian-weisser on 2015-11-05
If you are running 14.04, and have added no new repo nor PPAs, then your system wouldn't be trying to install 15.04/15.10 packages. Your system cannot know about the newer packages, which are not listed in the 14.04 repos.

Forcing might fix the version conflict today, but the underlying problem usually means it won't stay fixed for long.

Apt is pretty simple in this respect. Release -> Sources -> Repos -> Versions.

Please show us the output of the following command:
```
apt-cache policy libpcsclite1
```

---

### Post by joecasanova on 2015-11-05
> **ian-weisser said:**
> Please show us the output of the following command:
```
apt-cache policy libpcsclite1
```

```
joe@JoeTop:~$ apt-cache policy libpcsclite1
libpcsclite1:
  Installed: 1.8.14-1ubuntu1
  Candidate: 1.8.14-1ubuntu1
  Version table:
 *** 1.8.14-1ubuntu1 0
        100 /var/lib/dpkg/status
     1.8.10-1ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages


```

---

### Post by ian-weisser on 2015-11-06
> **joecasanova said:**
> 
 *** 1.8.14-1ubuntu1 0
        100 /var/lib/dpkg/status
     1.8.10-1ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages


Ah, so you added some new source which you have subsequenly removed....but left the newer software installed. Or you pulled 1.8.14 manually from somewhere and installed it.

So clearly this is not your first attempt - you have leftovers from previous attempts. You didn't clean up, and that's what is causing problems.

How to fix it:

1) Clean up. Uninstall those non-14.04 versions. Delete them from your system cache so they don't magically get reinstalled. 
```
sudo apt-get purge libpcsclite1 libpcsclite-dev pcscd     ## Uninstall the non-14.04 packages
sudo apt-get clean libpcsclite1 libpcsclite-dev pcscd     ## Delete those packages from your cache
```

2) Install what you need. My list of packages is much shorter, because everything you need is pulled in as a dependency.
```
sudo apt-get install pcscd pcsc-tools
```

3) Test the card reader hardware and software before installing DOD-specific software
Insert your CAC card and run:
```
pcsc_scan
```
If the output shows your card was detected, great.
If the output shows card-not-detected, stop here. You have a problem that installing DOD software won't fix.

After that, here's how I did it: [http://cheesehead-techblog.blogspot.com/2015/10/cac-on-firefox-using-ubuntu-1504.html](http://cheesehead-techblog.blogspot.com/2015/10/cac-on-firefox-using-ubuntu-1504.html)

---

### Post by joecasanova on 2015-11-08
Thank you for all the help through this.

More headaches though:

```
joe@JoeTop:~$ sudo apt-get purge libpcsclite1 libpcsclite-dev pcscd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libpcsclite-dev' is not installed, so not removed
Package 'pcscd' is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ca-certificates-java : Depends: openjdk-7-jre-headless (>= 7~u3-2.1.1~pre1-1) but it is not going to be installed or
                                 java6-runtime-headless
 openjdk-7-jre : Depends: openjdk-7-jre-headless (= 7u85-2.6.1-5ubuntu0.14.04.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.


```

---

### Post by ian-weisser on 2015-11-09
Your headaches haven't changed. You merely have not finished cleaning up...

> **joecasanova said:**
> 
The following packages have unmet dependencies:
 ca-certificates-java : Depends: **openjdk-7-jre-headless** (**>= 7~u3-2.1.1~pre1-1**) but it is not going to be installed or
                                 java6-runtime-headless
 openjdk-7-jre : Depends: **openjdk-7-jre-headless** (= **7u85-2.6.1-5ubuntu0.14.04.1**) but it is not going to be installed

Did you notice that both problems are due to the *same* package, and indeed *two different versions* of that package, neither of which is the version in trusty-updates (openjdk-7-jre-headless 7u85-2.6.1-5ubuntu0.14.04.1) that you should be using?

That means you added *two different *non-Ubuntu sources, and unwisely tried to install software from both that conflict with each other *and* your Ubuntu system. Don't do that. Really bad idea.
Fully-compatible, tested versions of ca-certificates-java and openjdk-7-jre, each with fully-compatible dependencies, are already in the Ubuntu repositories using the normal, trustworthy Ubuntu repositories.

You really have three long-term options:
1) Get out of the bad habit of installing from non-Ubuntu sources
2) Get into the good habit of cleaning up
3) Learn how the package manager works so you can easily troubleshoot little problems like these

Keep cleaning up. Uninstall ALL those non-Ubuntu or wrong-version packages, clean them from your cache, delete the sources you got them from, update your package database, and then try again.

---

### Post by joecasanova on 2015-11-13
Hey, sorry.  It's been a few days away for me.

PCSCD seems to be working fine now.  Everything is cleaned up.

Moving forward though, I have a few questions about installing software.  I've been running an ubuntu server out of a data center for several years now... I only utilize SSH access to it and I've only ever managed via APT on that server.  If the software I need or would like for that server isn't available via APT, I don't install it.  It's a production server.

Now I've installed ubuntu to my laptop for daily work.  Should I stick to strictly APT for software management or I can I safely use Ubuntu Software Center (are they the same thing)?  Should I stay away from installing software from source code compilation?  What's safe, what isn't.  Bear in mind that I'm getting into cyber security and using this laptop and Ubuntu to help me learn hopefully faster.

---

### Post by ian-weisser on 2015-11-13
> **joecasanova said:**
> Now I've installed ubuntu to my laptop for daily work.  Should I stick to strictly APT for software management or I can I safely use Ubuntu Software Center (are they the same thing)?  Should I stay away from installing software from source code compilation?  What's safe, what isn't.  Bear in mind that I'm getting into cyber security and using this laptop and Ubuntu to help me learn hopefully faster.

Glad you seem to have pcscd sorted.

The shortest useful answer is a history lesson:

In the beginning, everybody compiled from source code and installed manually. It was complicated and error prone, and every install was custom. You can still install from source today, but be warned that there are no handrails; you're in amongst the spinning gears and the system assumes you know what you are doing.

Next came Makefiles and Installfiles and tarballs, which standardized the install, but were fragile and easily broken. They can interfere with each other. They don't upgrade easily. Dependencies can be a nightmare. Lots of software is still distributed using tarballs and makefiles. This protects from typos, but there is no protection from conflicts, overwrites, or other potential-data-loss. It's the wild west, and you have only your horse for company and advice. 

Next came deb packages, pre-compiled software and install instructions that are executed by a helper application (called 'dpkg'). Much more robust, a standard install for everyone. But they get complicated when time comes to upgrade, and they might come from untrustworthy sources. You can still use dpkg to install packages. It's a '70s disco, with hair and drugs flying everywhere...you trust who you decide to trust.

Next came apt, which added dependency logic and trusted repositories and named/numbered distro releases and simple upgrades. And that's looking a lot like the Debian and Ubuntu systems we use today. The Ubuntu Software Center is one of many mere pretty front-ends to apt.

You can still use ALL those ways to install software...though apt is the way with the most protection from user-caused-breakage. All the others lack seatbelts.
If you can't find it in the Ubuntu Software Center, look for a fork/clone/reimplementation/alternative under a different name. Try Debian. Do a little research and figure out *why* it's not in Debian/Ubuntu (there's usually a really good reason) before you start rolling your own.

There are Security teams, with lots of chatter and mailing lists, in both Debian and Ubuntu, that you can learn a lot from and ask questions in.

---

