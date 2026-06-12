---
title: "What about Thunderbird 78 on Ubuntu 18.04.5"
date: 2021-01-13
forum: General Help
---

### Post by thog on 2021-01-13
Thunderbird was updated to version 78 already a long time (Aug.2020?) ago. Does anybody know when an update for Ubuntu 18.04 will be available and integrated into the distribution? I'm not very keen on new features but there have been reports on a couple of vulnerabilities of Thunderbird - the latest as of today ([https://www.heise.de/news/Sicherheitsupdate-Kritische-Schadcode-Luecke-in-Thunderbird-5022816.html](https://www.heise.de/news/Sicherheitsupdate-Kritische-Schadcode-Luecke-in-Thunderbird-5022816.html)). So IMHO there is some urgency about this issue.

Thanks for any helpful replies.
Thomas

---

### Post by walts48 on 2021-01-13
> **thog said:**
> Thunderbird was updated to version 78 already a long time (Aug.2020?) ago. Does anybody know when an update for Ubuntu 18.04 will be available and integrated into the distribution? I'm not very keen on new features but there have been reports on a couple of vulnerabilities of Thunderbird - the latest as of today ([https://www.heise.de/news/Sicherheitsupdate-Kritische-Schadcode-Luecke-in-Thunderbird-5022816.html](https://www.heise.de/news/Sicherheitsupdate-Kritische-Schadcode-Luecke-in-Thunderbird-5022816.html)). So IMHO there is some urgency about this issue.

Thanks for any helpful replies.
Thomas

You can follow along with these two bug reports.

[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1895643](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1895643)  and [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1901829](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1901829)

Other distributions are up to 78.6.0.

---

### Post by TheFu on 2021-01-13
Use a PPA, if you feel you need newer.

18.04 is an LTS.  That means the program versions should be frozen to be stable for people who depend on those versions. You can read more about what an LTS is here: [https://ubuntu.com/blog/what-is-an-ubuntu-lts-release](https://ubuntu.com/blog/what-is-an-ubuntu-lts-release) and a few other places.

If you want the latest version of software then you need to move to a new release every 6 months - or use a PPA. 20.10 has the newer Thunderbird version. Sometimes there are dependencies which aren't trivial to resolve with bleeding edge software.

Security fixes from *Canonical supported software* get back-ported or mitigated in some other way.

**New is the enemy of stable.** Always remember that.

I'm confused as to why an email thick client would be a security risk if you have the settings locked down for security already.  For example, never allow HTML emails, always run the program inside a constrained container system like firejail, and stay with supported versions.  
Your email server(s) should be blocking 99%+ of the bad stuff from getting to you already. Too bad they aren't always good at blocking the annoying stuff too.

I'm interested in the integrated gpg, but also need server-based calendar and address book support.  Until all three of those are available, any new version would break my email, so it cannot be allowed.  A broken email client is a [DOS]("https://en.wikipedia.org/wiki/Denial-of-service_attack") - worse than some security problem that I have other mitigations to handle already.

IMHO.

I've been running commercial email systems for 25+ yrs.
I use thunderbird daily and have for a very long time. Used Netscape Mail in the 1990s, before they split off the email from the browser.

Don't know whether this is helpful or not. Sorry if it isn't.
There are a few other threads here specifically about Thunderbird 78.x.  Those probably say what I've said above, perhaps in a nicer way?

---

### Post by Hagar Delest on 2021-01-13
You can also download the tar file, unzip it in /opt and make a custom .desktop menu file.
I've done so for years without any problem.

---

### Post by ajgreeny on 2021-01-13
> **Hagar Delest said:**
> You can also download the tar file, unzip it in /opt and make a custom .desktop menu file.
I've done so for years without any problem.
Does adding the tar that way and using the executable in that give you automatic updates?

The last time I looked, though I did not investigate very deeply, it did not autoupdate in the way that firefox does if you use the tar archive.
Perhaps you have to set it to autoupdate in the application settings; as I say, I did not look too closely.

---

### Post by Hagar Delest on 2021-01-13
It has been a while I haven't done that (I used the beta version to have an extra feature long time lacking the stable release).
But I'm pretty sure it did not update automatically, I had to check the help dialog to see if a new one was available.

---

### Post by Irihapeti on 2021-01-13
I'm currently running Thunderbird 78 on 20.04.  Just this morning, it warned me that there was an update available for download. So you get the notification, but have to tell it to install. I would imagine that 18.04 would behave in the same way.

Unless you have changed the ownership on the /opt/thunderbird directory (or wherever else you keep it) to your own userid, you won't be able to actually run the update from within the program.

---

### Post by walts48 on 2021-01-14
I know all the ways to add it, but Thunderbird 78.something should have been offered as an update through the Software Updater long ago.

Looks like Red Hat is the first distro to update users to 78.6.1. yesterday.

[https://lwn.net/Articles/842557/](https://lwn.net/Articles/842557/)

Oracle today.

[URL="https://lwn.net/Articles/842673/"]https://lwn.net/Articles/842673/

[/URL]I think I'll solve the problem by switching to a more responsible distribution. Fedora 33 looks good.

---

