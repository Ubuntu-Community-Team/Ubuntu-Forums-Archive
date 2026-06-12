---
title: "MEGA thread: ERR_SSL_PROTOCOL_ERROR for all Google products"
date: 2016-02-19
forum: General Help
---

### Post by Buntu Bunny on 2016-02-19
Starting yesterday I get an 

ERR_SSL_PROTOCOL_ERROR 

any time I try to access Google anything from Chromium: gmail, maps, blog dash, even Google forum where I wanted to look for an answer to the problem. I don't have this problem with Firefox or Chrome (for which I got an update this morning via update manager). I compared settings > advanced > HTTPS/SSL > manage certificates in both Chrome and Chromium and they appear to be identical. Now what?

---

### Post by t0p on 2016-02-19
Today I can't access Google using Chromium.  This isn't the end of the world, as I also have Firefox installed and that plays with Google just fine.  But it is annoying, as Chromium is the browser I use default; and as Google won't let me in, I can't get to Gmail.

This is what Google says:
> [h=1]SSL connection error[/h][COLOR=#444444][FONT=Helvetica]Unable to make a secure connection to the server. This may be a problem with the server or it may be requiring a client authentication certificate that you don't have.
[/FONT][/COLOR][COLOR=#A0A0A0][FONT=Helvetica]Error code: ERR_SSL_PROTOCOL_ERROR[/FONT][/COLOR]


The time and date on my computer are correct.  I can't think of anything I've done that would have messed with Chromium.  I tried disabling Chrome QUIC Protocol (something I found on Google) and that didn't make any difference?

Any ideas?  Help me, Ubuntuforums, you're my only hope!

Cheers.

---

### Post by ajgreeny on 2016-02-19
You could try a new chromium profile by renaming the ~/.config/chromium folder for a start to see if that solves the problem, and then take it from there.

All your bookmarks etc etc will be safe in the renamed configuration so you can restore them easily if you don't sync them over all your devices and browsers.

---

### Post by sitmex on 2016-02-19
Thanks for the suggestion, but no, that didn't work for me either.

I believe this is a bigger magnitude issue... has there been an update lately?

---

### Post by Mike Krall on 2016-02-20
There has been an update lately... or, at least for 12.04...  a few days ago.  At the end of taking the update I clicked "Check" and quite a number of other updates got in queue and I took them.  That was morning mountain time. That evening all Google related... YouTube, G-Mail, etc. showed SSL connection error.

This, to be exact...  

[I][I]SSL connection error

Unable to make a secure connection to the server. This may be a problem with the server, or it may be requiring a client authentication certificate that you don't have.
Error code: ERR_SSL_PROTOCOL_ERROR[/I][/I]


Mike

---

### Post by bcschmerker on 2016-02-20
**I have a theory on what happened:**  I opened Chromium Browser to review new posts from subscriptions at Google+® and YouTube&#8480; (both Alphabet Corporation properties) and, upon attempting to open:
```
https://accounts.google.com/ServiceLogin

```ran into the ERR_SSL_PROTOCOL_ERROR.  All available information as of 19 February 2016 points to a regression in Chromium triggered by the security updates to:

libnss3:amd64 (3.19.2.1-0ubuntu0.12.04.2, 3.21-0ubuntu0.12.04.1)
libnss3:i386 (3.19.2.1-0ubuntu0.12.04.2, 3.21-0ubuntu0.12.04.1)
libnss3-1d:amd64 (3.19.2.1-0ubuntu0.12.04.2, 3.21-0ubuntu0.12.04.1)

Mozilla® Firefox® 44.0.3-build2 behaves normally on the same URI, and Bug #1547762 for chromium-browser is already open at Launchpad&#8482;.  Recommend opening new bugs for libnss-3 and libnss3-1d.

---

### Post by BelJoost on 2016-02-20
> **bcschmerker said:**
> Bug #1547762 for chromium-browser is already open at Launchpad [...] libnss-3 and libnss3-1d.

[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1547762](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1547762)

Please add yourself if it affects you too. Both at the top "This bug affects x people. Does this bug affect you?", and in the column on the right-side "You are not directly subscribed to this bug's notifications."

---

### Post by pappo2 on 2016-02-20
I am seeing the same thing on my Ubuntu 14.04.3 LTS system.
It started a couple of days ago when I tried to login to my Gmail account.
I have no problem on Firefox either.
I also checked my certificates in Advanced settings and it looks normal there.

---

### Post by BelJoost on 2016-02-20
There is another thread about this here on Ubuntu forums.
[http://ubuntuforums.org/showthread.php?t=2314244](http://ubuntuforums.org/showthread.php?t=2314244)

A bug report is present on launchpad. It seems to have to do with a libnss3 update earlier this week.
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1547762](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1547762)

Please add yourself to the bugpost if it affects you too. Both at the top "This bug affects x people. Does this bug affect you?", and in the column on the right-side "You are not directly subscribed to this bug's notifications."

---

### Post by Buntu Bunny on 2016-02-20
> **BelJoost said:**
> There is another thread about this here on Ubuntu forums.
[http://ubuntuforums.org/showthread.php?t=2314244](http://ubuntuforums.org/showthread.php?t=2314244)

BelJoost, thanks. I see that that thread was started after mine, but who knows why some questions are answered and others don't seem to get noticed! I've added myself to the "Does this bug affect you?" list at Launchpad.

---

### Post by Buntu Bunny on 2016-02-20
I asked [this same question]("http://ubuntuforums.org/showthread.php?t=2314215") on the Forum the other day, but who knows why some questions get answered and others seem to go unnoticed! :confused: Anyway, Beljoost kindly alerted me to the conversation here, and I've added myself to the "Does this bug affect you?" list at Launchpad.

---

### Post by Mike Krall on 2016-02-20
I've added myself on at LaunchPad as well...

Mike

---

### Post by sitmex on 2016-02-21
There has been a [bug]("https://bugs.launchpad.net/bugs/1547762") reported on Launchpad and people are looking for solutions already.

---

### Post by Morgothzz on 2016-02-21
A temporarily solution is;

Open synaptic
type/find libnss3
Select libnss3 2:3.21-0ubuntu0.14.04.1 (or similar file)

Go to package-force version (in the menu)

Select with the pulldown menu your previous version (mine was libnss3 2:3.15.4-1ubuntu7)
confirm with force version
Repeat this also for libnss3-nssdb
Then apply

When you downgrade these files you must temporarily lock both files (until they fix it)

Go to the menu - package - lock version.

---

### Post by oldos2er on 2016-02-21
Merged two threads, hopefully this will make it easier for thread participants to track this problem. Also changed thread title a bit.

---

### Post by Mike Krall on 2016-02-21
It may be worth following the same thing here...  [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1547762]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1547762")

Mike

---

### Post by BelJoost on 2016-02-22
It seems to be a package issue, not a Chromium issue. At least on the Chromium tracker this issue has status: WontFix.

> Based on the bug template, you've indicated you're running version "37.0.2062.120", which is no longer supported, and has a number of critical security bugs. You should upgrade to the latest version of Chrome, which is Chrome 48. If you're running a version provided by another party, such as your distro, please inform them that they're distributing an insecure version.

[https://bugs.chromium.org/p/chromium/issues/detail?id=588146](https://bugs.chromium.org/p/chromium/issues/detail?id=588146)

So we'll have to wait till it's possible to manually add a repository to update Chromium to the latest version; or install a more recent Chromium version if available at all.

---

### Post by Mike Krall on 2016-02-22
BelJoost,

For me (12.04 current), your link provokes SSL Protocol Error.  I can get to Chromium.org but efforts to find the referred to discussion generates SSL Protocol Error

Mike

---

### Post by bcschmerker on 2016-02-23
**Update:**  Attempting to bring Chromium 48.0.2564.109-0ubuntu0.12.04.1.987 online.  This updated version is at Canonical Chromium Builds, but be advised that the stable version may need to be purged first.  Contingency commands from Terminal:

```
sudo add-apt-repository ppa:canonical-chromium-builds/stage
sudo apt-get purge --remove chromium-browser chromium-codecs-*
sudo apt-get update
sudo apt-get install chromium-browser chromium-codecs-ffmpeg-extra

```

**Update 2:** chromium-browser 48.0.2564.109-0ubuntu0.12.04.1.987 terminates on open - see text below:
```
$ chromium-browser
/usr/lib/chromium-browser/chromium-browser: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version 'GLIBCXX_3.4.18' not found (required by /usr/lib/chromium-browser/chromium-browser)
/usr/lib/chromium-browser/chromium-browser: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version 'GLIBCXX_3.4.18' not found (required by /usr/lib/chromium-browser/libs/libnet.so)
/usr/lib/chromium-browser/chromium-browser: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version 'GLIBCXX_3.4.18' not found (required by /usr/lib/chromium-browser/libs/libskia.so)

```

---

### Post by Buntu Bunny on 2016-02-23
So I have Chrome Version 48.0.2564.116 (64-bit) and
Chromium Version 37.0.2062.120 Ubuntu 12.04 (281580) (64-bit)
which is the most recent version of Chromium in the Ubuntu 12.04 Software Centre. 
I'm thinking the only thing for this is to upgrade to 14.04 (something I know I'll need to do eventually anyway but dread all the same).

---

### Post by bcschmerker on 2016-02-24
**Update from Launchpad.net:**  I'm tracking multiple Bugs related to the ERR_SSL_PROTOCOL_ERROR problem.  It appears, per [Bug #1520568](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1520568), that libnss3 2:3.21-*n*ubuntu*m* breaks multiple versions of chromium-browser (we know about the problem with chromium-browser 37.0.2062.120-0ubuntu0.12.04.1~pkg917 in [Bug #1441960](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1441960)).  Google Code division, Alphabet Corporation, apparently has the bugs of all versions of Chromium before 47.0 as RESOLVED WONTFIX due to security issues fixed as of Chrome 48.0.2564.116.  As of 24 February 2016 a fix is in progress for chromium in Ubuntu® 12.04.*x*-LTS Precise Pangolin&#8482;; wonder whether that's also the case for 14.04.*x*-LTS Trusty Tahr&#8482;?

---

### Post by larkguit on 2016-02-24
Just got an update to ca-certificates today (Feb. 24 '16) that didn't help (was hopin it would)

---

### Post by Buntu Bunny on 2016-02-25
FIXED! Word came out this morning from the Launchpad team.

```
sudo apt-get update and
sudo apt-get dist-upgrade
```

fetches and installs a Chromium replacement that *works*.

\\:D/

My sincerest thanks and congratulations to the team that did it!

---

### Post by bcschmerker on 2016-02-26
**All systems go** for chromium-browser 37.0.2062.120-0ubuntu0.12.04.2! :-)

---

### Post by plastart on 2016-11-14
[QUOTE=Buntu Bunny;13445733]FIXED! Word came out this morning from the Launchpad team.

```
sudo apt-get update and
sudo apt-get dist-upgrade
```


NOPE ..  can not confirm this on Linux Mint (Ubuntu xenial) .. only successfull solution was to install latest
[https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb) ... whats the problem with
repository packages: Chromium, Iron Browser .. .. ..?!

this ssl issue appears a week ago first.. makes unable to use common service like amazon, ebay, google.
all of my private ssl secured pages does not have this issue! eg. [https://www.plastart.de](https://www.plastart.de)

---

### Post by Buntu Bunny on 2016-11-14
> **plastart said:**
> NOPE ..  can not confirm this on Linux Mint (Ubuntu xenial) .. only successfull solution was to install latest
[https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb) ... whats the problem with
repository packages: Chromium, Iron Browser .. .. ..?!

this ssl issue appears a week ago first.. makes unable to use common service like amazon, ebay, google.
all of my private ssl secured pages does not have this issue! eg. [https://www.plastart.de](https://www.plastart.de)

Plastart, firstly, welcome to the Ubuntu forums. 

The fix we were celebrating was for 12.04 Precise Pangolin. It sounds like you need to report this as a separate bug.

---

