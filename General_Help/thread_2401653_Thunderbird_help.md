---
title: "Thunderbird help"
date: 2018-09-20
forum: General Help
---

### Post by Dr._B on 2018-09-20
I've looked for help in the mozilla forums, but am hoping people here may have a solution. I updated thunderbird to version 60.0. Like many others have experienced, this killed lightening. So I tried to follow mozillas instructions as described here to restore functionality:[https://support.mozilla.org/en-US/kb/calendar-updates-issues-thunderbird](https://support.mozilla.org/en-US/kb/calendar-updates-issues-thunderbird)


However, when I searched for "extensions.installedDistroAddon.{..." there was no entry. So I moved onto the next step, and removed the plug-in. I restarted thunderbird...no lightening, and the version of the plug-in that comes up when you search add-ons is an old version (Version 52) that thunderbird refuses to install.


I tried the "turn off strict comparability testing" option, as per this thread, to no avail - the same old version of lightening appears when you search add-ons, and you cannot install it as it is not compatable:
[https://forum.manjaro.org/t/thunderbird-60-and-lightning/55590/15](https://forum.manjaro.org/t/thunderbird-60-and-lightning/55590/15)


I even did a complete uninstall (after backing up my data folder) and reinstall - still no lightening, even before restoring my old account information.


Does anyone know how to get it back?


Details are:
Thunderbird 60.0
OS: Ubuntu 16.04 LTS

---

### Post by TheFu on 2018-09-20
Easy answer, don't use v60.x of Thunderbird until the lightning addon is updated to support it.

I'm on 16.04, thunderbird version is v1:52.9.1+bui amd64
Lightning version is 4.0.5.2 from 2017.

Using calendaring with multiple calendars - google, zimbra, local, and some published ical versions.  I could use the webmail from Zimbra as a fallback, but that is a major hassle.

I realize this isn't the answer you were hoping to see.

---

### Post by Dr._B on 2018-09-20
Maybe not the answer I was hoping for, but if it works, it works.

Is there an easy way to roll-back to an older version?

---

### Post by TheFu on 2018-09-20
I wouldn't know. Undo whatever you did to get off the older version?   I patch every week using the Ubuntu repos.  If you are using mozilla repos, stop that.

---

### Post by Dr._B on 2018-09-20
All I did was run software updater...will have to look for a .deb or something.

---

### Post by Dr._B on 2018-09-20
I have found a work-around, if anyone else runs into this issue.


You can download lightening directly from here:
[https://archive.mozilla.org/pub/calendar/lightning/candidates/](https://archive.mozilla.org/pub/calendar/lightning/candidates/)


Install using the add-ons -> install from file option

I installed 6.2b6, and its working well

---

### Post by TheFu on 2018-09-20
That doesn't seem like a workaround. Seems like you did the right thing.  Addons always have to be manually updated.

  Will I be getting v60 this weekend?

---

### Post by walts48 on 2018-09-21
> **TheFu said:**
> I wouldn't know. Undo whatever you did to get off the older version?   I patch every week using the Ubuntu repos.  If you are using mozilla repos, stop that.

Why should they stop that?

Well, yes don't use the repos. Get the applications directly from the source. [https://www.thunderbird.net/en-US/thunderbird/all/](https://www.thunderbird.net/en-US/thunderbird/all/)

They update when new versions are released, not when some maintainer thinks it is time to offer one. 

I have Ubuntu 18.04 set to notify me of updates daily. Thunderbird 60.0 with nearly 60 new, fixed and changed items was released on Aug. 6, 2018 and still not available from Ubuntu. :P

[https://www.thunderbird.net/en-US/thunderbird/60.0/releasenotes/](https://www.thunderbird.net/en-US/thunderbird/60.0/releasenotes/)

Using a Thunderbird 52.9.1 from Thunderbird should update to version 60.0 with the correct version of Lightning bundled with it. It's been bundled with TB since version 38.

---

### Post by TheFu on 2018-09-21
> Why should they stop that?

IMHO with multiple decades of Unix/Linux experience... 

"New is the enemy of stable."

I don't want new features on a currently working, stable, system.  Don't want to patch daily either. That much patching would interrupt getting work done and when/if there are issues, tracing the problem back to a system constantly changing would be just a little harder.

Not using the repos is asking for problems.  Could be dependencies, could be unexpected interactions.  For example, Firefox decided to switch to PulseAudio and all the Lubuntu systems would have lost audio since they still use Alsa.  Mozilla has a tough job making their programs work across as many environments and distros already.

In order of best to worst:
* Use the Canonical Repos - security patches will be made based on the criticality of the issue.
* Use a trusted,well-maintained, PPA - usually these are fine. Usually.
* Use a .deb file, but expect the package manager to have dependency issues in 3-6 months. "APT Hell" likely. Manual updates required from that point on, usually. Some .deb files will add a PPA to the system, but not all.
* Flatpak/Snap-Pak ... these are newer options. Hopefully, will become useful, especially for browsers and email clients. Snaps can be easily updated via the snap manager.  IDK, but hopefully flatpaks do the same. Regardless, it is another "update" to remember. There is runtime overhead, mostly RAM, due to the method of deployment, not using external dependencies. Trade-offs. Manual updates required from that point on.
* Get an installer from the source/maintainers.  Only if you need the specific features provided. Often this is fine. Manual updates required from that point on.
* Get the source from a reputable location and built the program yourself. Manual updates required from that point on.

The 1st 2 options integrate with normal software maintenance on Debian-based systems.  These are a chief reason many people choose Linux systems over the alternatives.

All the other options require manual efforts to maintain the software.  Humans, being what we are, forget to update manually installed software and just don't go a good job at it.  In a few weeks, there could be security problems that would never be corrected until manual steps were taken.  An average Ubuntu system has 1500+ packages.  Even just 50 applications would be a huge hassle to maintain manually. 

Bad idea, IMHO.

Plus I've had very little luck getting help from Mozilla related to issues with either Firefox or Thunderbird.  So I have a personal bias against going directly to their packages unless absolutely mandatory.  

But everyone has different needs, so having the options available isn't a bad thing.

---

### Post by TheFu on 2018-09-22
Just did my weekly patching.
On my 16.04.5 laptop, 
```
thunderbird   1:52.9.1+build3-0ubuntu0.16.04.1
```
is the version installed using the Ubuntu repos.  I have no idea how someone would get a newer version unless she did something extra like adding a PPA or manually downloading something.

---

### Post by speartip on 2018-09-22
I have to agree with TheFu on this one. 10 years of using Linux has taught me, always use the repo version of something, unless it is absolutely necessary. Thunderbird 52.9 is also the Repo version in 18.04 as well as 16.04, and it just works. Newer can sometimes mean better, but more often than not it means problems.

---

### Post by PaulW2U on 2018-09-22
Neither the snap or deb version (from the Ubuntu Mozilla Security Team PPA) are ready for release although they are being worked on by Canonical's developers.
```
snap info thunderbird
```
shows that version 60 is still in the edge channel, i.e. at alpha status.

The PPA is showing build failures on several architectures for the trusty, xenial and bionic releases. If someone has downloaded an amd64 or i386 version of Thunderbird I can't think that it's been fully tested or anywhere near ready for copying to the -updates and -security repositories until everything builds successfully on the remaining architectures.

It's stated quite clearly on the Security Team PPA's front page:
> Staging PPA for Mozilla and other browser-related security updates. Unless you are testing updates, you should not install packages from this PPA
Just because something is available doesn't mean it's been tested and ready for release until it appears as an update in the default repositories.

---

### Post by walts48 on 2018-09-22
Thunderbird 60.0 released August 6, 2018 was tested prior to the release by the Thunderbird team, as are all betas and releases. 

I've been using it  from [https://www.thunderbird.net/en-US/thunderbird/all/](https://www.thunderbird.net/en-US/thunderbird/all/)

AMD® Athlon(tm) ii x3 455 processor × 3  3.2 Ghz

---

### Post by PaulW2U on 2018-09-22
> **walts48 said:**
> Thunderbird 60.0 released August 6, 2018 was tested prior to the release by the Thunderbird team
Obviously. 

But it still has to build and be tested on Ubuntu. :)

---

### Post by walts48 on 2018-09-23
> **PaulW2U said:**
> Obviously. 

But it still has to build and be tested on Ubuntu. :)

Well, sorry to see it is having build problems by the Ubuntu maintainer.

The Thunderbird team seems to be having problems building the next release on all platforms.

TB 60.0 was the first taskcluster build,  they no longer use buildbot, the build directory structure has changed, new web and add-ons site which may be on new a new infrastructure. Interesting times.

---

