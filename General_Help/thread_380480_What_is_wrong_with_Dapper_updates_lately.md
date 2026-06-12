---
title: "What is wrong with Dapper updates lately?"
date: 2007-03-09
forum: General Help
---

### Post by ardchoille42 on 2007-03-09
What is happening to the repos lately?

```

[downloads @ 12:31:11] sudo aptitude upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  dvd+rw-tools
The following packages will be upgraded:
  ekiga libspeex1 libxine-main1
3 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 6661kB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?]

```

so I chose "n" and then did:
```

[downloads @ 14:02:50] sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  dvd+rw-tools
The following packages will be upgraded:
  ekiga libspeex1 libxine-main1
4 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 6798kB of archives. After unpacking 77.8kB will be used.
The following packages have unmet dependencies:
  dvd+rw-tools: Depends: genisoimage which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
dvd+rw-tools [5.21.4.10.8-4ubuntu1 (dapper, now)]

Score is 0

Accept this solution? [Y/n/q/?]

```

It seems to me that there are more and more problems with the repos lately. I don't mean to offend anyone, but what's going on? Isn't every update checked before it goes into the repos?

I use Ubuntu on 11 machines here, I recommend Ubuntu to everyone who will listen, and I have helped over 100 people and businesses in my area switch from Windows to Ubuntu. If people keep seeing problems, they're not going to hold onto Ubuntu very long.

If the repo maintainers/packagers need help, is there any way I can help?

---

### Post by megamaced on 2007-03-09
I've got this problem too. This is starting to feel familiar.....

---

### Post by STREETURCHINE on 2007-03-09
yep same problem id say it is happening to all who have dapper

---

### Post by megamaced on 2007-03-09
Upon further inspection, the package is from the Dapper backports repository

---

### Post by ardchoille42 on 2007-03-09
> **megamaced said:**
> Upon further inspection, the package is from the Dapper backports repository

Yes, but what concerns me is this isn't the first time there has been a problem with the repos. Recently, there was a problem with the kernel, and also a problem with xorg. And it seems that the problems are becoming more frequent.

---

### Post by loell on 2007-03-09
its a good thing that i haven't been  updating lately, plus i turn off the update notification.

---

### Post by robbie75 on 2007-03-10
I do have the same problem since last night
and yes, I have backport repos in my sources.

---

### Post by Healey on 2007-03-10
Hi

I have noticed the same issue with dvd+rw-tools being held back. I only use the update Icon to inform me of updates. Normally I dont use the terminal for this.

So I decided not to update anything

Is this the best thing to do or should I update all except the broken package ???

Regards

Healey

---

### Post by lamadredelsapo on 2007-03-10
I have the same problem

---

### Post by Gerard Barberi on 2007-03-10
I got the same thing, but with a few extra...

Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  build-essential dpkg-dev dvd+rw-tools g++ libc6-dev pptp-linux

Also, I recently tried burning an ISO to DVD and was unsuccessful.

---

### Post by yabbadabbadont on 2007-03-10
I only got the dvd+rw-tools error.  I sovled it (for now) by locking it to the previous version in Synaptic.  Speaking of which, you might want to look those listed packages up in Synaptic and see if all of them are from the backports repository.  If so, it might be a good idea to disable backports for a while...

---

### Post by MJN on 2007-03-10
The new DVD+rw-tools package (v7.0-6~dapper1) from Dapper-backports requires **genisoimage** which is only available in Feisty...

Hence as mentioned above the 'best' solution for now is to leave DVD+rw-tools at the core repository version (v5.21.4.10.8-4ubuntu1).

I've raised the issue in the Backports sub-forum - [http://ubuntuforums.org/showthread.php?t=380825](http://ubuntuforums.org/showthread.php?t=380825)

Mathew

---

### Post by Gerard Barberi on 2007-03-10
> **yabbadabbadont said:**
> I only got the dvd+rw-tools error.  I sovled it (for now) by locking it to the previous version in Synaptic.  Speaking of which, you might want to look those listed packages up in Synaptic and see if all of them are from the backports repository.  If so, it might be a good idea to disable backports for a while...

I solved the problem.  It was my fault.  I was fiddling with an Edgy CD to install on my laptop and somehow added it to my sources list.  Although I don't recall...

---

### Post by MJN on 2007-03-10
So what version of dvd+rw-tools do you have installed now? Presumably not the latest Dapper-backports version? Or did you mean you've solved the problem with the other packages (and not dvd+rw-tools)?

Mathew

---

### Post by yabbadabbadont on 2007-03-10
I've got mine locked to 5.21.4.10.8-4ubuntu1.

I've only got dapper sources in my sources.list.  In fact, I just did a clean dapper install last night.

---

### Post by Gerard Barberi on 2007-03-10
> **MJN said:**
> So what version of dvd+rw-tools do you have installed now? Presumably not the latest Dapper-backports version? Or did you mean you've solved the problem with the other packages (and not dvd+rw-tools)?

Mathew

Left it at the 5.21.4.10.8 version.  It was the other packages I fixed.

---

### Post by yabbadabbadont on 2007-03-10
> **Gerard Barberi said:**
> Left it at the 5.21.4.10.8 version.  It was the other packages I fixed.

Thank you for the information.  That means it is just the dvd+rw-tools package that someone screwed up in backports.  The maintainer is probably suffering from "premature package commit" syndrome...  :lol:

---

### Post by linuksamiko on 2007-03-10
Has anybody an idea how I can lock packages with adept? I use kubuntu and don't want to install synaptic just to lock dvd+rw-tools.
A solution with apt-get would be ok too.

---

### Post by picpak on 2007-03-10
> **linuksamiko said:**
> Has anybody an idea how I can lock packages with adept? I use kubuntu and don't want to install synaptic just to lock dvd+rw-tools.
A solution with apt-get would be ok too.


Put this in your /etc/apt/preferences:

```
Package: dvd+rw-tools
Pin: version 5.21.4.10.8
Pin-Priority: 1001

```

---

### Post by Ambimom on 2007-03-10
Me too! Same problem. [http://www.ubuntuforums.org/showthread.php?t=380825](http://www.ubuntuforums.org/showthread.php?t=380825)

---

### Post by Ambimom on 2007-03-10
Me too! Same problem.  


[http://www.ubuntuforums.org/showthread.php?t=380825](http://www.ubuntuforums.org/showthread.php?t=380825)

---

### Post by MJN on 2007-03-10
That's my post! (as mentioned above)

---

### Post by Azakus on 2007-03-10
Try sudo aptitude dist-upgrade. That'll take care of it.

---

### Post by WW on 2007-03-10
Azakus: I don't think so.  The problem is that **genisoimage** does not exist in the dapper or dapper-backports repositories.

---

### Post by MJN on 2007-03-10
> **Azakus said:**
> Try sudo aptitude dist-upgrade. That'll take care of it.

No it won't, that'll just remove dvd+rw-tools! 

```

$ sudo aptitude -s dist-upgrade

Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done
The following packages are BROKEN:
  dvd+rw-tools
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 138kB of archives. After unpacking 77.8kB will be used.
The following packages have unmet dependencies:
  dvd+rw-tools: Depends: genisoimage which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
dvd+rw-tools
dvdstyler

Leave the following dependencies unresolved:
k3b recommends dvd+rw-tools
Score is -852

Accept this solution? [Y/n/q/?] y
The following packages will be automatically REMOVED:
  dvd+rw-tools dvdstyler
The following packages will be REMOVED:
  dvd+rw-tools dvdstyler
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 2408kB will be freed.
Do you want to continue? [Y/n/?] y
Would download/install/remove packages.

```

---

### Post by Azakus on 2007-03-10
Oh yes, genisoimage is an edgy package that replaces mkisofs I believe. 
Install the genisopackage package from Debian, then try upgrading dvd+rw-tools
[http://packages.debian.org/unstable/otherosfs/genisoimage](http://packages.debian.org/unstable/otherosfs/genisoimage)
Whoops, this package depends on a newer libc6 than Dapper has.
```
admin@fileserver:~$ wget http://http.us.debian.org/debian/pool/main/c/cdrkit/genisoimage_1.1.2-1_i386.deb
--11:01:26--  http://http.us.debian.org/debian/pool/main/c/cdrkit/genisoimage_1.1.2-1_i386.deb
           => `genisoimage_1.1.2-1_i386.deb'
Resolving http.us.debian.org... 64.50.238.52, 128.101.240.212, 204.152.191.7, ...
Connecting to http.us.debian.org|64.50.238.52|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 552,116 (539K) [application/x-debian-package]

100%[====================================>] 552,116      941.87K/s             

11:01:27 (940.18 KB/s) - `genisoimage_1.1.2-1_i386.deb' saved [552116/552116]

admin@fileserver:~$ sudo dpkg -i gen*
Selecting previously deselected package genisoimage.
dpkg: considering removing mkisofs in favour of genisoimage ...
dpkg: yes, will remove mkisofs in favour of genisoimage.
(Reading database ... 58925 files and directories currently installed.)
Unpacking genisoimage (from genisoimage_1.1.2-1_i386.deb) ...
dpkg: dependency problems prevent configuration of genisoimage:
 genisoimage depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
dpkg: error processing genisoimage (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 genisoimage

```

---

### Post by j5tixc on 2007-03-10
Isn't this what just happened with the kernel? Here we go again...

---

### Post by MJN on 2007-03-10
> **Azakus said:**
> Oh yes, genisoimage is an edgy package that replaces mkisofs I believe. 

Keep up at the back! ;)

We've already discussed above (post 12) that genisoimage is a **Feisty** package!

Mathew

---

### Post by WW on 2007-03-10
Bug report filed: [https://bugs.launchpad.net/dapper-backports/+bug/91180](https://bugs.launchpad.net/dapper-backports/+bug/91180)

---

### Post by Azakus on 2007-03-10
> **MJN said:**
> Keep up at the back! ;)

We've already discussed above (post 12) that genisoimage is a **Feisty** package!

Mathew

Ahh, so it was backported to edgy then. Didn't really check it when I installed it in edgy, but it worked there.

---

### Post by ardchoille42 on 2007-03-10
> **Azakus said:**
> Oh yes, genisoimage is an edgy package that replaces mkisofs I believe. 
Install the genisopackage package from Debian, then try upgrading dvd+rw-tools
[http://packages.debian.org/unstable/otherosfs/genisoimage](http://packages.debian.org/unstable/otherosfs/genisoimage)
Whoops, this package depends on a newer libc6 than Dapper has.
```
admin@fileserver:~$ wget http://http.us.debian.org/debian/pool/main/c/cdrkit/genisoimage_1.1.2-1_i386.deb
--11:01:26--  http://http.us.debian.org/debian/pool/main/c/cdrkit/genisoimage_1.1.2-1_i386.deb
           => `genisoimage_1.1.2-1_i386.deb'
Resolving http.us.debian.org... 64.50.238.52, 128.101.240.212, 204.152.191.7, ...
Connecting to http.us.debian.org|64.50.238.52|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 552,116 (539K) [application/x-debian-package]

100%[====================================>] 552,116      941.87K/s             

11:01:27 (940.18 KB/s) - `genisoimage_1.1.2-1_i386.deb' saved [552116/552116]

admin@fileserver:~$ sudo dpkg -i gen*
Selecting previously deselected package genisoimage.
dpkg: considering removing mkisofs in favour of genisoimage ...
dpkg: yes, will remove mkisofs in favour of genisoimage.
(Reading database ... 58925 files and directories currently installed.)
Unpacking genisoimage (from genisoimage_1.1.2-1_i386.deb) ...
dpkg: dependency problems prevent configuration of genisoimage:
 genisoimage depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.4.
dpkg: error processing genisoimage (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 genisoimage

```

It is NEVER a good idea to use debian packages in Ubuntu.

---

### Post by ardchoille42 on 2007-03-10
Thank you all so very much for the help and support.

These forums are awesome! :)

---

### Post by geezerone on 2007-03-10
> **WW said:**
> Bug report filed: [https://bugs.launchpad.net/dapper-backports/+bug/91180](https://bugs.launchpad.net/dapper-backports/+bug/91180)

Thankyou

---

### Post by DC@DR on 2007-03-11
Let's wait and hope the package maintainers will release a fix for this issue soon. And I do hope this kind of problem won't bother us, Dapper (LTS) users, again :-)

---

### Post by j5tixc on 2007-03-11
Seems like it's fixed now.

---

### Post by laidback on 2007-03-11
After the last problem with Evolution and Firefox upgrade ( a week or two back) I determined not to upgrade as soon as it became available or was notified. Reading the above makes me think I made the right decision.

Thanks for your inputs one and all.

PS The odd DVD message has now disappeared from updates after doing a Reload in Synaptic.

---

### Post by Qew on 2007-03-11
Still getting the message that dvd+rw-tools will be skipped in the Update Manager after a check. Using Synaptics after a reload still says that dvd+rw-tools has a dependency for genisoimage. Maybe the repository that I'm using hasn't got the updated files, so I'll check again in a few hours.

---

### Post by Pikestaff on 2007-03-11
> **j5tixc said:**
> Seems like it's fixed now.

Finally worked for me this morning as well...

---

### Post by robbie75 on 2007-03-11
Got it fixed right now ;-)

---

### Post by Qew on 2007-03-11
> **Qew said:**
> Still getting the message that dvd+rw-tools will be skipped in the Update Manager after a check. Using Synaptics after a reload still says that dvd+rw-tools has a dependency for genisoimage. Maybe the repository that I'm using hasn't got the updated files, so I'll check again in a few hours.

Yeah, it's now working fine. Must be more patient next time. ;)

---

### Post by MJN on 2007-03-13
> **ardchoille42 said:**
> It is NEVER a good idea to use debian packages in Ubuntu.
 
Any particular reason for that? I've got numerous Debian packages installed all working perfectly without fault.
 
Mathew

---

### Post by ardchoille42 on 2007-03-13
> **MJN said:**
> Any particular reason for that? I've got numerous Debian packages installed all working perfectly without fault.
 
Mathew

debian packages are meant for debian. Ubuntu packages are meant for Ubuntu. mixing distros is never a good idea, despite how close the distros may be. Seems you have been very lucky so far, but that may come back to bite you later. And, even if this has never caused problems for you, it may cause numerous problems for someone else.. that instability is one of the reason to never mix distros.

I used to mix distros like that and it worked great for almost a year. Then one day I installed updates and a large number of apps broke. After finding out all the work involved in fixing the problems, I just reinstalled and swore to never mix distros again.

---

### Post by MJN on 2007-03-13
I think 'lucky' is a bit strong - indeed I seem to be in good company with the practice.
 
Besides which, there's often little option if one want's the latest and greatest, or perhaps a non-mainstream applications, other than to install a Debian package if no port of it exists specifically for Ubuntu.
 
To put it another way, I'm sure I'd spend far more timing compiling and porting apps to Ubuntu than I will ever spend fixing something that gets broken during an upgrade, particularly given this latter situation has yet to occur since I first started using Ubuntu back in '05!
 
I'm not for one moment suggesting low-level core libraries are mixed - indeed all my 'Debian packages' are practically standalone high-level apps hence any symptoms of incompatibilities would be tightly contained.
 
Furthermore I'm not saying Debian and Ubuntu packages should be treated on an equal footing but rather that when requirements justify the installation of a Debian package it should not be ruled out under a *'it is NEVER a good idea to' *generic rule.
 
Mathew

---

### Post by ardchoille42 on 2007-03-13
> **MJN said:**
> I think 'lucky' is a bit strong - indeed I seem to be in good company with the practice.
 
Besides which, there's often little option if one want's the latest and greatest, or perhaps a non-mainstream applications, other than to install a Debian package if no port of it exists specifically for Ubuntu.
 
To put it another way, I'm sure I'd spend far more timing compiling and porting apps to Ubuntu than I will ever spend fixing something that gets broken during an upgrade, particularly given this latter situation has yet to occur since I first started using Ubuntu back in '05!
 
I'm not for one moment suggesting low-level core libraries are mixed - indeed all my 'Debian packages' are practically standalone high-level apps hence any symptoms of incompatibilities would be tightly contained.
 
Furthermore I'm not saying Debian and Ubuntu packages should be treated on an equal footing but rather that when requirements justify the installation of a Debian package it should not be ruled out under a *'it is NEVER a good idea to' *generic rule.
 
Mathew

Well, after seeing so many people bitten after mixing distros, I have to stick with the following set of rules:

1) Install from the repos
2) Find a .deb package that was built for Ubuntu
3) Compile the software yourself
4) If none of the above work, look for a different app to fill the need.

I have used Ubuntu since Warty and Linux since 2001. I have helped over 100 people and businesses in my area switch to Ubuntu and have never seen a problem yet with following those rules. Of course any user can do what they wish with their systems.. but I feel it is best to stick with the "supported" recommendations (see above list) when recommending something to another user and every Ubuntu guru I have talked to says "never mix repos".

---

### Post by dannyboy79 on 2007-03-13
Debian packages and Ubuntu packages misconception:
there are so many packages that are grabbed from debain and updated that it's not even funny. any package that you see a number in the beginning and then ubuntu added to the name, this was first a debian package, then bugs were fixed or something was updated and ubuntu turned it into there own. that's the great thing about source code, it's free!!! check out this statement from Mark Shuttleworth's website, "In his analysis he points out that the Ubuntu and Debian packages are very similar - I think that&#8217;s a credit to Ian Jackson, who I know spends a lot of time passing Ubuntu changes to Debian, trying to make sure that there&#8217;s no unnecessary divergence between Debian and Ubuntu." not to mention, you can find out if all the dependencies are met prior to installing a debain package ahead of time. Not to mention Ubuntu's own developers page states that when building packages the developer must follow the Debain Policy Manual. [https://wiki.edubuntu.org/UbuntuDevelopment#head-e52c51c05057e5a99230bfd35dbde114eee83f33](https://wiki.edubuntu.org/UbuntuDevelopment#head-e52c51c05057e5a99230bfd35dbde114eee83f33)

Failures and packages being held-back:
I would also like to point out to the many people complaining that their machines went crazy for a while is because most of them if not all are using the backport repo. this craziness is the consequence you risk by enabling the backports. It clearly states it right in your sources.list before you uncomment, "## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)"

So don't start complaining that ubuntu is broken or whatever when you are doing something that is clearly advertized as possible problems occuring!

---

### Post by MJN on 2007-03-13
That sounds more like it - there could be problems with installing Debian packages (and packages from backports) and users should be mindful of the risks but to rule the option out entirely is an overreaction (particularly when there are many of us using them quite happilly and troublefree! :)).
 
Mathew

---

### Post by ardchoille42 on 2007-03-14
> **MJN said:**
> That sounds more like it - there could be problems with installing Debian packages (and packages from backports) and users should be mindful of the risks but to rule the option out entirely is an overreaction (particularly when there are many of us using them quite happilly and troublefree! :)).
 
Mathew

It sounds to me like you wouldn't have accepted anything other than "Yes, it's ok to mix repos". I feel you just want justification for what you did so you wouldn't have to face the fact that maybe you did something you weren't supposed to do. I won't be reading this thread anymore.

---

### Post by MJN on 2007-03-14
Not at all - I was genuinely interested in possible justifications for a hard line stance of never mixing packages.
 
I accept, and agree, that it is not without pitfalls as discussed above but I have not been convinced that the option warrants ruling out entirely and hence disagree fundamentally with the idea that it is 'never a good idea'.
 
Mathew

---

### Post by dannyboy79 on 2007-03-14
> **MJN said:**
> Not at all - I was genuinely interested in possible justifications for a hard line stance of never mixing packages.
 
I accept, and agree, that it is not without pitfalls as discussed above but I have not been convinced that the option warrants ruling out entirely and hence disagree fundamentally with the idea that it is 'never a good idea'.
 
Mathew
I wish that when people were confronted with negativity such as the post directed at you more users could respond with such professionalism as you have. There is always way to much childish behaviour in pretty much all forums with people arguing about "their" way being better than another's way and it's just sickening.

It's good to be informed regarding to the consequences that could arise from using non-ubuntu repo's and  what you are allowing onto your machine but ultimately it's your machine, if you want to install debain packages and use backport repo's or even add joe-blows repo which may be a mirror for opera, realplayer and such (not official) than you can do that as long as you know the risk and you inform others of this risk when suggesting to use such a technique.

---

