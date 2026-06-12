---
title: "Why Didn't Firefox Automatically Update (New User Question)"
date: 2024-03-25
forum: General Help
---

### Post by karyk on 2024-03-25
I'm a fairly new user of Ubuntu.  My Firefox was at 123.0.1 even though I read last week a new version was out.  Today I ran both Software Updater and Software & Updates, and neither updated it.  Last week I tried running the general commands to update through Terminal, but didn't try that today.  What did update it was opening Ubuntu Software, searching for Firefox, and installing.  Now I'm at 124.0.1, so it was out of date.

I'm a bit concerned because I don't know what else might not be updating.

---

### Post by #&amp;thj^% on 2024-03-25
This is opinionated by me, Ubuntu's support of Firefox via snap rather than apt is, if not "broken", at the very least "not delivering the experience that users have a right to expect." ATM

At times I've seen users relay the same concern as yourself, and have you ever tried:
```
snap refresh firefox
```

I use mozillas PPA for a .deb and a flatpak version as well, others just download a zip file and run it from there.

I'll quote a well known user here  ian-weisser
> 
    Snap packages MUST refresh. Auto-refresh is a key element of their design. It's one of the most attractive elements to developers, who want to minimize their own support burdens --and user complaints-- by having all users to run a single version of the software regardless of platform. Folks who don't want auto-refresh should not use Snap-packaged software.

Snap handling, like all open-source software, continues to evolve, change, and improve. Developers know about these pain points and are working on them. It can be a slow process --there are a lot of moving parts-- and volunteers to get involved, help, test, and improve the software are welcome.

---

### Post by karyk on 2024-03-25
Thanks, no I never have tried that snap command.

Are there any other apps affected by this behavior?  Thunderbird?

---

### Post by ajgreeny on 2024-03-25
I'm assuming that you are using the firefox that was installed in Ubuntu when you installed the OS which means it is the snap version. Snaps are not updated when normal updating is carried out by the user but happens automatically an at irregular intervals when a new snap is available. If you wish to check manually you can use terminal command ```
snap refresh
```
I can not give more details as I do not have any snaps on my systems but find alternatives, in the case of firefox that being a downloaded .tar.bz archive from Mozilla which is simply extracted and contains an executable file so is not installed in the usual way.  Using that archive I see notifications that a new version is available and a click on that notification updates the archive.

---

### Post by #&amp;thj^% on 2024-03-25
> **karyk said:**
> Thanks, no I never have tried that snap command.

Are there any other apps affected by this behavior?  Thunderbird?

Yes Thunderbird. I'm not aware of any others though my snap usage is very limited. (Due to I feel it's still a work in progress. Snaps)

You can take care of both of those as seen here: [https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

ajgreeny offers his method as well.
```
 snap list
Name               Version                     Rev    Tracking       Publisher      Notes
bare               1.0                         5      latest/stable  canonical&#10003;     base
core18             20231027                    2812   latest/stable  canonical&#10003;     base
core20             20240111                    2182   latest/stable  canonical&#10003;     base
gnome-3-28-1804    3.28.0-19-g98f9e67.98f9e67  198    latest/stable  canonical&#10003;     -
gtk-common-themes  0.1-81-g442e511             1535   latest/stable  canonical&#10003;     -
snapd              2.61.2                      21184  latest/stable  canonical&#10003;     snapd
surfshark          2.2.0                       10     latest/beta    surfshark1vpn  -

```
No firefox there. :)

---

### Post by ajgreeny on 2024-03-25
Chromium also is available only as a snap from the normal Ubuntu sources though there are PPAs available which I use and work well though I seldom use it, much preferring firefox.

Snaps are in my opinion an answer to a problem that never existed, though it does relieve Canonical of the responsibility of keeping those packages updated and maybe that was the basic reasoning behind the move towards them more and more. I can't really comment more because, as I said, I do not use snaps and always remove all the snap packages and the complete snap infrastructure.

---

### Post by donald187 on 2024-03-25
> **1fallen said:**
> Yes Thunderbird. I'm not aware of any others though my snap usage is very limited. (Due to I feel it's still a work in progress. Snaps)

Correct me if I'm wrong but stock Thunderbird is still a deb package on Ubuntu.  Here it is on my system where I have not installed it myself.

```

$ apt policy thunderbird
thunderbird:
  Installed: 1:115.8.1+build1-0ubuntu0.22.04.1
  Candidate: 1:115.8.1+build1-0ubuntu0.22.04.1
  Version table:
 *** 1:115.8.1+build1-0ubuntu0.22.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1:91.8.0+build2-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

So it should update along with the other packages as usual.

It seems that stock Thunderbird will be a snap on 24.04 according to the following link which shows it as a transitional package.

[https://packages.ubuntu.com/search?keywords=thunderbird](https://packages.ubuntu.com/search?keywords=thunderbird)

---

### Post by #&amp;thj^% on 2024-03-25
> **donald187 said:**
> Correct me if I'm wrong but stock Thunderbird is still a deb package on Ubuntu.  Here it is on my system where I have not installed it myself.

So it should update along with the other packages as usual.

It seems that stock Thunderbird will be a snap on 24.04 according to the following link which shows it as a transitional package.

[https://packages.ubuntu.com/search?keywords=thunderbird](https://packages.ubuntu.com/search?keywords=thunderbird)

Yep on 22.04 it is still a .deb, I'm running 24.04 which is a snap. (So I should have stated as such) ;)
ie:
```
 apt policy thunderbird && rmadison thunderbird |grep noble
thunderbird:
  Installed: 1:115.8.1+build1+snap2
  Candidate: 1:115.8.1+build1+snap2
  Version table:
 *** 1:115.8.1+build1+snap2 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
 thunderbird | 1:115.8.1+build1+snap2             | noble           | source, amd64, arm64

```

After I dump the snap version:
```
apt policy thunderbird
thunderbird:
  Installed: 1:124.0+build1-0ubuntu0.24.04.1~mt3
  Candidate: 1:124.0+build1-0ubuntu0.24.04.1~mt3
  Version table:
 *** 1:124.0+build1-0ubuntu0.24.04.1~mt3 500
        500 https://ppa.launchpadcontent.net/mozillateam/thunderbird-next/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
     1:115.8.1+build1+snap2 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages

```

---

### Post by karyk on 2024-03-25
Thanks all!  Learned a lot.

---

