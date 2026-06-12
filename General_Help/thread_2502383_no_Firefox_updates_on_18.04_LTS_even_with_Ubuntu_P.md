---
title: "no Firefox updates on 18.04 LTS even with Ubuntu Pro"
date: 2024-11-12
forum: General Help
---

### Post by ChrisC on 2024-11-12
Hi all ... I've been using Ubuntu for many years, updating every four years or so to the latest LTS available. I'm currently on 18.04 LTS which I know is six years old, so I'm behind schedule :)  I'm planning on updating it this winter, blocking out a lot of time because it's a Big Deal for me, especially because this time I'll be building a new computer for it.

Since Ubuntu ended regular support for 18.04 last year, I opted to sign up for Ubuntu Pro to get the extended support.  Now, this is where we go into ELI5 territory ... Is that only for security updates?  It's my first time using Ubuntu Pro to buy me some time.

Because today I started getting warnings from various websites that my old Firefox (version 113) is no longer supported.  That's when I learned that Firefox isn't supporting Ubuntu 18.04 anymore (right?), and that what I'm running is 18 months behind the times (Firefox is currently at version 132).  Gulp!

Are there any steps I can take to update Firefox, or will it have to wait until I get the entire OS upgraded?  Again that OS upgrade is only a month or two away.

---

### Post by guiverc on 2024-11-13
There was security warnings published with [Ubuntu 16.04 LTS for users opting to use ESM]("https://wiki.ubuntu.com/SecurityTeam/ESM/16.04"), and one of those was to switch to *snap* packages for some apps which were no longer being maintained via *deb* package upgrade.

I'm not aware of any relating to 18.04 (*but it's very possible that there are some, eg. I did note a number of warnings that ESM was limited to specific architectures only, limits on the packages included etc, but there is a very good chance I've forgotten or ignored much of what was said as I'm not a bionic/18.04 user anymore, thus didn't need to retain that detail*), but I'd really consider swapping your browser to the *snap* package.

A simple `snap info firefox` will show what versions are available for you via *snap* package. I do recall some users had issues with specific extensions (*when using snap and not deb package*), but this only impacted a small number of extensions (*but that could still be very significant to you, eg. some banking apps required specific extensions I recall*)

--

Addendum - the *xenial* link I provided was published for *bionic*, and you should have read it, plus other notices relating to your release.

[https://wiki.ubuntu.com/SecurityTeam/ESM/18.04](https://wiki.ubuntu.com/SecurityTeam/ESM/18.04)

You'll note firefox is specifically mentioned there too (*just as with 16.04*)

> 
Firefox, Thunderbird, Chromium and LibreOffice are made available only  through the Snap Store. Get the latest supported version at:


---

### Post by grahammechanical on 2024-11-13
ESM? Extended Security Maintenance.

> ESM provides 10 years of vulnerability management for critical, high and  selected medium CVEs for all software packages shipped with Ubuntu.

[https://ubuntu.com/pro](https://ubuntu.com/pro)

Ten Year security coverage.

> Security maintenance for the entire collection of software packages shipped with Ubuntu.

           ESM enables continuous vulnerability management for critical, high and medium CVEs

[https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)

They will keep Firefox and other applications secure but no mention of upgrading them to newer versions. On the other hand the snap version of Firefox, maintained by Mozilla, gets regular upgrades to newer version. This is my experience with using the Firefox snap version.

Regards

---

### Post by Dennis N on 2024-11-13
You are right. Firefox in the Ubuntu 18.04 with Pro is not being updated by Ubuntu. I opted for the Firefox ESR from Mozilla. On another system, I used the Firefox Flatpak. Both are good solutions.

---

### Post by hifron on 2024-11-13
Debian with light-ware(like Mate, Xfce or even Gnome Flashback(if apps and hw allows)) is alternative for 16.04+ LTS but may require some compiling for needed apps(even codium=code :)

---

### Post by ChrisC on 2024-11-13
Thanks guys for the responses so far!  I'll investigate those solutions.  Relieved that I may not need to drop everything and do the computer upgrade immediately ...

Unrelated aside: it took me a while to find the signature edit function ( [https://ubuntuforums.org/profile.php?do=editsignature](https://ubuntuforums.org/profile.php?do=editsignature) ), but it won't let me save changes, so that's why my sig is stuck in 2014 ...

---

