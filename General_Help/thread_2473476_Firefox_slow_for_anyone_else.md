---
title: "Firefox slow for anyone else?"
date: 2022-04-05
forum: General Help
---

### Post by Autodave on 2022-04-05
Lately, FF has been terrible.  For instance, on Facebook, it will quit showing images.  While viewing a video, it will hang part way through.  On the forums here, it will get very laggy going out of one room and into another room.  This machine is dual booted and I do not have this problem with FF in Win10.  Wife's machine is only Xubuntu and has the same issue.

---

### Post by &amp;KyT$0P# on 2022-04-05
> **Autodave said:**
> on Facebook, it will quit showing images.

I don't use Facebook, but recently ran across a Firefox bug about a similar sounding Facebook issue that was reported fixed in Firefox 100 and maybe fixed in 99.

> On the forums here, it will get very laggy going out of one room and into another room.

I'm seeing this one as well.  Tested using this site in Vivaldi and did not encounter this issue there.

Not seeing any of the other issues you mention.

Firefox 99.0 here, installed from tarball.  What version of Firefox are you using and what type of package is it installed as?

---

### Post by iamjiwjr on 2022-04-05
The flatpak firefox is much faster.

---

### Post by Autodave on 2022-04-06
98.0.2 is my current version.  This is what was installed automatically when I reinstalled Xubuntu about 6 weeks ago.

---

### Post by ActionParsnip on 2022-04-06
What is the output of
```

lsb_release -a; uname -a; apt-cache policy firefox

```
Not a Firefox user here so can't tell you if it's slow or not

---

### Post by TenPlus1 on 2022-04-06
I use the latest Firefox .deb from linux mint repo's as it's much faster than the snap.  Note that you have to download the .deb and install yourself each time it's updated.

---

### Post by Autodave on 2022-04-06
dave@dave-MS-7B07:~$ lsb_release -a; uname -a; apt-cache policy firefox
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.4 LTS
Release:    20.04
Codename:    focal
Linux dave-MS-7B07 5.13.0-39-generic #44~20.04.1-Ubuntu SMP Thu Mar 24 16:43:35 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
firefox:
  Installed: 98.0.2+build1-0ubuntu0.20.04.1
  Candidate: 98.0.2+build1-0ubuntu0.20.04.1
  Version table:
 *** 98.0.2+build1-0ubuntu0.20.04.1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 Packages
        100 /var/lib/dpkg/status
     75.0+build3-0ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 Packages

---

### Post by &amp;KyT$0P# on 2022-04-06
Are you using uBlock Origin with "Uncloak canonical names" enabled?  If so, as a test does un-checking that option make a difference on this forum?

* sorry, never mind, that's not it.  Although the forum mostly seems to load faster with that setting disabled, it doesn't fix the intermittent lag.

---

### Post by Autodave on 2022-04-06
I was running uBlock.....disabled it and am running much better now.  I had no issues though until about a month ago......and I have been running uBlock for years.  Weird.

---

### Post by dragonfly41 on 2022-04-06
There is also Palemoon browser which derives from Firefox.

---

### Post by &amp;KyT$0P# on 2022-04-06
> **Autodave said:**
> I had no issues though until about a month ago......

That time frame suggests the problems you're experiencing may have started with the Firefox 98 update.  Are you able to try Firefox 99 even though it is not (yet?) available as a deb?

---

### Post by GhX6GZMB on 2022-04-06
It's simple: Firefox is *always* slow (and bloated and unsafe and unstable). The way of life.

---

### Post by #&amp;thj^% on 2022-04-06
> **ml9104 said:**
> It's simple: Firefox is *always* slow (and bloated and unsafe and unstable). The way of life.

unsafe is a bit harsh I'd think, for example:
So, while the current Tor Browser that's distributed is a patched version of Firefox, this is because currently Firefox is the only browser that is close enough to the requirements to meet these design goals without extensive re-engineering or having to maintain a fork.

Firefox also provides an "Extended Support Release" which is what Tor Browser is based on, which only gets security updates, not functionality updates which reduces the frequency and workload of maintaining the patch set.
safety IMHO is user-related not so much browser related. (just saying)

---

