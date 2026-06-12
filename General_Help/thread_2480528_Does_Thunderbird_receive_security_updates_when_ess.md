---
title: "Does Thunderbird receive security updates when essential?"
date: 2022-11-01
forum: General Help
---

### Post by donald187 on 2022-11-01
I'm on Ubuntu 22.04.  Stock Thunderbird is behind in updates now.

```

$ apt policy thunderbird
thunderbird:
  Installed: 1:102.2.2+build1-0ubuntu0.22.04.1
  Candidate: 1:102.2.2+build1-0ubuntu0.22.04.1
  Version table:
 *** 1:102.2.2+build1-0ubuntu0.22.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1:91.8.0+build2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

The current release is 102.4.1.  I understand that Thunderbird updates only occasionally.  I did notice that Thunderbird updated immediately to include the patch for the zero day exploit unearthed at pwn2own.

[https://www.bleepingcomputer.com/news/security/mozilla-fixes-firefox-thunderbird-zero-days-exploited-at-pwn2own/](https://www.bleepingcomputer.com/news/security/mozilla-fixes-firefox-thunderbird-zero-days-exploited-at-pwn2own/)

If you look at the Thunderbird Security Advisories page the recent exploits have this message included.

> 
In general, these flaws cannot be exploited through email in the  Thunderbird product because scripting is disabled when reading mail, but  are potentially risks in browser or browser-like contexts.


[https://www.mozilla.org/en-US/security/advisories/mfsa2022-46/](https://www.mozilla.org/en-US/security/advisories/mfsa2022-46/)

So the fact that Thunderbird is behind in updates doesn't really matter.  There is also this excerpt from a post.

> 
[alexmurray]("https://discourse.ubuntu.com/u/alexmurray")

As such, testing etc of Firefox updates (and other desktop packages  seeded on the desktop image etc) are prioritised over Thunderbird so in  general Thunderbird updates will lag behind Firefox updates.  Unfortunately in a world where new security issues are found daily  across the vast array of software that is distributed in Ubuntu, there  is a constant stream of security updates which need to be prepared,  tested and released by a finite number of developers. The security and  desktop teams have to prioritise which packages to target and so we  prefer to take the approach of protecting the greatest number of users  as possible by updating the packages that are most used first. Hence why  unfortunately Thunderbird updates generally will come later - there are  just a lot more users of Firefox (and many other applications) than  Thunderbird.


[https://discourse.ubuntu.com/t/slow-thunderbird-updates-endanger-users/26963/18](https://discourse.ubuntu.com/t/slow-thunderbird-updates-endanger-users/26963/18)

I guess what I'm really wondering is if maybe the maintainers are strategically updating Thunderbird when it really needs it such as with the pwn2own zero day but letting it slide when the danger is not so great?  Or is it just that they get to it when they can?

EDIT:  Forgot to add that I've seen other posts in the forums saying that Ubuntu 22.04 is a LTS and updates are only when needed.  Which would seem to imply that Thunderbird is indeed updated when needed.

---

### Post by donald187 on 2022-11-01
I also notice that the Ubuntu Security tracker has most recent cve's listed as medium.

[https://ubuntu.com/security/cves?q=&package=thunderbird&priority=&version=jammy&status=](https://ubuntu.com/security/cves?q=&package=thunderbird&priority=&version=jammy&status=)

Perhaps medium does not warrant an update?  I seem to recall someone saying this (maybe on these forums?) in the past.

---

### Post by ian-weisser on 2022-11-02
> **donald187 said:**
> I understand that Thunderbird updates only occasionally.

Take a look at the Thunderbird changelogs: [https://changelogs.ubuntu.com/changelogs/pool/main/t/thunderbird/](https://changelogs.ubuntu.com/changelogs/pool/main/t/thunderbird/)

Thunderbird was version-bumped ("updated") three times in September and twice in October. It's not being ignored.


> **donald187 said:**
> I guess what I'm really wondering is if maybe the maintainers are strategically updating Thunderbird when it really needs it such as with the pwn2own zero day but letting it slide when the danger is not so great?  Or is it just that they get to it when they can?

Well, the maintainers (the Ubuntu Desktop Team) this week are doing their early-cycle sprint meetings and preparing for the Ubuntu Summit next week. Less maintenance during these two weeks is expected. That doesn't mean they have dropped the ball, only that their priority is elsewhere. If a high-priority CVE appeared in Thunderbird this week, they would work it.


> **donald187 said:**
> I've seen other posts in the forums saying that Ubuntu 22.04 is a LTS and updates are only when needed.

The *purpose* of an LTS release is that the software doesn't change (with important exceptions) for the life of the release. That's the feature writ large, not a bug. "Important exceptions" do include security patches, of course. And version-bumps for a small number of key applications, including web browsers but generally not mail clients (Evolution is patched, not bumped).

Thunderbird is an exception to that exception, and gets version bumps due to sharing so much code with Firefox (which was version-bumped about every two weeks). Since Firefox is now snapped, there are occasional discussions about whether or not to stop version-bumping and start patching. But for now Thunderbird still gets version-bumped. Just be patient about it.

---

### Post by donald187 on 2022-11-02
Thanks.  It's good to know that if a high priority cve came along that the maintainers would version-bump it.  That was what I had observed with the zero day revealed at pwn2own with the release of 91.9.1 fixing CVE=2022-1802 and CVE-2022-1529.

[https://www.bleepingcomputer.com/news/security/mozilla-fixes-firefox-thunderbird-zero-days-exploited-at-pwn2own/](https://www.bleepingcomputer.com/news/security/mozilla-fixes-firefox-thunderbird-zero-days-exploited-at-pwn2own/)

I had hoped that this was standard operating procedure and why I started this thread.

Just to clarify I didn't think that the maintainers had dropped the ball.  From reading that thread on discourse.ubuntu.com it is my understanding that it is the testing and approval process that sometimes keeps Thunderbird behind a couple of versions or so sometimes.  And this is due to not enough maintainers (EDIT: I mean testers) to go around.  Firefox and applications that have a large user base get higher priority and Thunderbird, which has a lower user base, gets lower priority.  Hope I have that right.

> 
[oSoMoN]("https://discourse.ubuntu.com/u/oSoMoN")

Hi usr11elf, and thanks for sharing your  concerns. You are right that we&#8217;re lagging behind, and this is a  potential security problem.

 Building updates in the ubuntu-mozilla-security PPA is only one part  of the process. After updates are built, they need to be tested and  validated on all supported Ubuntu releases, after which the security  team sponsors them into the respective security pockets. This is a  time-consuming process, which explains (but doesn&#8217;t excuse) the delay  between a new upstream release and its availability in Ubuntu.
 On this specific version, there is a new upstream release candidate  (91.7.0) that is currently building in the PPA, we will do our best to  get it on everyone&#8217;s machine as soon as possible.


[URL="https://discourse.ubuntu.com/t/slow-thunderbird-updates-endanger-users/26963/5"]https://discourse.ubuntu.com/t/slow-thunderbird-updates-endanger-users/26963/5

[/URL]So lagging behind sometimes can be a security problem?  Over the past couple of years I've occasionally looked into the released version of Thunderbird and it wasn't uncommon to be a couple or so versions behind.  Which is why I'm asking.

> 
[alexmurray]("https://discourse.ubuntu.com/u/alexmurray")

[@usr11elf]("https://discourse.ubuntu.com/u/usr11elf")  Indeed the delay is in the testing and approval process - and  unfortunately this takes a certain amount of time. Firefox is given  higher priority than Thunderbird because it is a lot more popular than  Thunderbird is seeded on the desktop media - and is the default web browser for Ubuntu.  With the rise of web-based mail services like gmail etc, desktop email  clients have become a lot less popular than they were 10-20 years ago. Thunderbird  has not been seeded in the desktop image since before 18.04 LTS as a  reflection of this as generally users are not using desktop email  clients - most just use the web browser to access their webmail.
 
As such, testing etc of Firefox updates (and other desktop packages  seeded on the desktop image etc) are prioritised over Thunderbird so in  general Thunderbird updates will lag behind Firefox updates.  Unfortunately in a world where new security issues are found daily  across the vast array of software that is distributed in Ubuntu, there  is a constant stream of security updates which need to be prepared,  tested and released by a finite number of developers. The security and  desktop teams have to prioritise which packages to target and so we  prefer to take the approach of protecting the greatest number of users  as possible by updating the packages that are most used first. Hence why  unfortunately Thunderbird updates generally will come later - there are  just a lot more users of Firefox (and many other applications) than  Thunderbird.

 
If you are still concerned, the immediate steps you could take would be to either:

 
[LIST=1]
[*]Consume the pre-release updates from the [Mozilla Security PPA 2]("https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa") - but note these have not gone through the full validation so may have stability or other issues 
[*]Switch to the [Thunderbird snap 1]("https://snapcraft.io/thunderbird")  - this is generally more up-to-date as it can use the same set of  dependencies across all releases and so doesn&#8217;t get held up when Mozilla  decide to depend on newer technologies/packages than are available on  older Ubuntu releases like 18.04 
[*]Switch to using the [binaries provided by Mozilla]("https://download.mozilla.org/?product=thunderbird-91.7.0-SSL&os=linux64") 
[/LIST]



[https://discourse.ubuntu.com/t/slow-thunderbird-updates-endanger-users/26963/18](https://discourse.ubuntu.com/t/slow-thunderbird-updates-endanger-users/26963/18)

---

### Post by donald187 on 2022-11-02
> **ian-weisser said:**
> Take a look at the Thunderbird changelogs: [https://changelogs.ubuntu.com/changelogs/pool/main/t/thunderbird/](https://changelogs.ubuntu.com/changelogs/pool/main/t/thunderbird/)
Thunderbird was version-bumped ("updated") three times in September and twice in October. It's not being ignored.

Most of those bumps are--not sure what to call them--internal builds?  Work being done internally?  Only the 10/4 build,  [thunderbird_102.2.2+build1-0ubuntu0.22.04.1/]("https://changelogs.ubuntu.com/changelogs/pool/main/t/thunderbird/thunderbird_102.2.2+build1-0ubuntu0.22.04.1/"), was version-bumped to Jammy in October right?   And only internal bumps in September but none to Jammy?  But I see that work is being done which I think is your point.

---

### Post by donald187 on 2022-11-03
Interesting relevant article article from the Ubuntu Blog which explains all this.  By Alex Murray, one of the posters quoted above.

[Securing Open Source through CVE Prioritisation]("https://ubuntu.com/blog/securing-open-source-through-cve-prioritisation")

---

### Post by donald187 on 2022-11-04
> **donald187 said:**
> Most of those bumps are--not sure what to call them--internal builds?  Work being done internally?  Only the 10/4 build,  [thunderbird_102.2.2+build1-0ubuntu0.22.04.1/]("https://changelogs.ubuntu.com/changelogs/pool/main/t/thunderbird/thunderbird_102.2.2+build1-0ubuntu0.22.04.1/"), was version-bumped to Jammy in October right?   And only internal bumps in September but none to Jammy?  But I see that work is being done which I think is your point.

This page seems to show the actual version-bumps for Jammy.

[https://launchpad.net/ubuntu/jammy/+source/thunderbird](https://launchpad.net/ubuntu/jammy/+source/thunderbird)

---

### Post by oldfred on 2022-11-04
I do not use snaps.
And installed the Firefox ppa which happens to include Thunderbird.
You have to both add ppa & change priorities as shown in these links.
Remove snap Firefox & use ppa
[https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd)
[https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/](https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/)
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

```

[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ apt policy thunderbird [/COLOR]
thunderbird: 
  Installed: 1:102.4.2+build1-0ubuntu0.22.04.1~mt1 
  Candidate: 1:102.4.2+build1-0ubuntu0.22.04.1~mt1 
  Version table: 
 *** 1:102.4.2+build1-0ubuntu0.22.04.1~mt1 1001 
       1001 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages 
        100 /var/lib/dpkg/status 
     1:102.2.2+build1-0ubuntu0.22.04.1 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages 
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages 
     1:91.8.0+build2-0ubuntu1 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages[/FONT]

```

---

### Post by donald187 on 2022-11-04
> **oldfred said:**
> I do not use snaps.
And installed the Firefox ppa which happens to include Thunderbird.
You have to both add ppa & change priorities as shown in these links.
Remove snap Firefox & use ppa
[https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd)
[https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/](https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/)
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

```

[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ apt policy thunderbird [/COLOR]
thunderbird: 
  Installed: 1:102.4.2+build1-0ubuntu0.22.04.1~mt1 
  Candidate: 1:102.4.2+build1-0ubuntu0.22.04.1~mt1 
  Version table: 
 *** 1:102.4.2+build1-0ubuntu0.22.04.1~mt1 1001 
       1001 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages 
        100 /var/lib/dpkg/status 
     1:102.2.2+build1-0ubuntu0.22.04.1 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages 
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages 
     1:91.8.0+build2-0ubuntu1 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages[/FONT]

```

Thanks.  I thought about doing this but I worry about ppa's.  I guess Mozilla Team is trustworthy (I think they publish stock Thunderbird after all) but I assume the same level of testing is not possible as with Thunderbird from the repositories.  I once read a long debate on ycombinator.com(?) about Flatpaks with pros and cons.  I assume much of that would carry over to snaps.   From what I've seen many if not most posters here (as well as at the Debian forums) don't like them.  But I don't mind them and have no need to do any configuring.  So I've installed snap Thunderbird (again).  It keeps up pretty well with the version-bumps.  Although it skipped 102.4.0 and 102.4.1 for some reason.  But it's right back up to date now.

```

$ snap info thunderbird
name:      thunderbird
summary:   Mozilla Thunderbird email application
publisher: Canonical&#10003;
store-url: https://snapcraft.io/thunderbird
contact:   https://launchpad.net/distros/ubuntu/+source/thunderbird
license:   unset
description: |
  Thunderbird is a free and open source email, newsfeed, chat, and
  calendaring client, that&#8217;s easy to set up and customize. One of the core
  principles of Thunderbird is the use and promotion of open standards - this
  focus is a rejection of our world of closed platforms and services that
  can&#8217;t communicate with each other. We want our users to have freedom and
  choice in how they communicate.
commands:
  - thunderbird
snap-id:      k1Ml1O9GzSO2QftV0ZlWSbUfQ78nN460
tracking:     latest/stable
refresh-date: yesterday at 08:16 PDT
channels:
  latest/stable:    102.4.2-2 2022-11-03 (272) 106MB -
  latest/candidate: 102.4.2-2 2022-11-02 (272) 106MB -
  latest/beta:      107.0b3-1 2022-11-01 (270) 108MB -
  latest/edge:      &#8593;                                
installed:          102.4.2-2            (272) 106MB -

```

---

### Post by donald187 on 2022-11-04
> **oldfred said:**
> I do not use snaps.
And installed the Firefox ppa which happens to include Thunderbird.
You have to both add ppa & change priorities as shown in these links.
Remove snap Firefox & use ppa
[https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd](https://www.kubuntuforums.net/forum/general/documentation/how-to-s/662503-how-to-set-priority-for-a-ppa-i-e-using-firefox-without-snapd)
[https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/](https://fostips.com/ubuntu-21-10-two-firefox-remove-snap/)
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

I went ahead and added the ppa using the omgubuntu link.  I didn't like it when snap Thunderbird didn't update to 102.4.0 which sent me on this journey.  It seems that the Mozilla Team ppa did update to 102.4.0 if I'm reading the successful builds right.

[https://launchpad.net/~mozillateam/+archive/ubuntu/ppa/+builds?build_text=thunderbird&build_state=built](https://launchpad.net/~mozillateam/+archive/ubuntu/ppa/+builds?build_text=thunderbird&build_state=built)

I've seen that a number of users here have the Firefox ppa so I guess if you all are not concerned about a lack of testing and approval then I'm sure it's fine.

Thanks!

---

### Post by donald187 on 2022-11-06
> **ian-weisser said:**
> Take a look at the Thunderbird changelogs: [https://changelogs.ubuntu.com/changelogs/pool/main/t/thunderbird/](https://changelogs.ubuntu.com/changelogs/pool/main/t/thunderbird/)

Thunderbird was version-bumped ("updated") three times in September and twice in October. It's not being ignored.

These must be the version-bumps for the development releases such as Lunar and Kinetic some of which Jammy gets as well.

[https://launchpad.net/ubuntu/+source/thunderbird/+publishinghistory](https://launchpad.net/ubuntu/+source/thunderbird/+publishinghistory)

---

### Post by donald187 on 2022-11-18
So I looked at the Ubuntu CVE tracker and got a list of Thunderbird cve's rated as high.  (There were no critical cve's.)

[https://ubuntu.com/security/cves?q=&package=thunderbird&priority=high&version=&status=](https://ubuntu.com/security/cves?q=&package=thunderbird&priority=high&version=&status=)

Looking at the individual cve's I found the version of Thunderbird that fixed them.  Then I looked at the actual published versions of Thunderbird in the LTS versions of Ubuntu.

[https://launchpad.net/ubuntu/+source/thunderbird/+publishinghistory](https://launchpad.net/ubuntu/+source/thunderbird/+publishinghistory)

For anyone coming across this you have to click on the arrow at the left and look for the published date.  As far as I can tell these high cve's were fixed mostly in 7 to 10 days with one taking 2 weeks. And one that took 3 months (CVE-2020-26950).  That was the upgrade of Thunderbird from the 68 series to the 78 series that took 7 months if I read the data right. That agrees with my memory as well.  I recall reading that that was a tough transition.  So it's nice to see the actual data that confirms that high cve's in Thunderbird are fixed reasonably quickly.  I only went back as far as 2019.

---

