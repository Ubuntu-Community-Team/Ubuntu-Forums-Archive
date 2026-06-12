---
title: "Is there a way to downgrade Firefox back to 56? The software center won't let me"
date: 2017-11-17
forum: General Help
---

### Post by llbrand on 2017-11-17
Downloaded firefox 56 deb from [here]("http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/"). Tried to install it via software center, dpkg -i and gdebi.

It tells me there are dependency conflicts, offers to solve them, but when i do, it automatically reinstalls Firefox57 without asking.

There must be a way to install an older version?

---

### Post by Richard-S on 2017-11-17
I did the same thing I downloaded 56, but it loaded 57. I have to get rid of this 57. My important add ons don't work.

---

### Post by monkeybrain20122 on 2017-11-17
No, not to 56 but you can go back further with FF-esr [https://launchpad.net/~jonathonf/+archive/ubuntu/firefox-esr](https://launchpad.net/~jonathonf/+archive/ubuntu/firefox-esr) (it coexists with FF57 and is probably FF52)

Alternatively, if you must you can download the tarball for FF56 from Mozilla (there is a page for old releases but I don't remember where it is) this is a precompiled binary, so just put it in your $HOME somewhere, click "firefox" or something like that to use it. You can make a .desktop file so it will show up in your menu/dashboard. This way it bypasses the OS's updating system all together. But using outdated browser is not recommended (eventually it will be outdated)


Edited: actually I quite like FF57 and it is super fast. Are you sure you can't find replacements for your addons if that is your issue?

---

### Post by cscj01 on 2017-11-17
I have the same issue.  I have used Passwordmaker for years to generate passwords for my web sites.  FF57 no longer supports it.  I am trying to use the Passwordmaker Pro add-on, but I can't seem to get it to work properly.  There is no documentation, and the support person has not replied to any of my emails.

---

### Post by &amp;KyT$0P# on 2017-11-17
> **monkeybrain20122 said:**
> Alternatively, if you must you can download the tarball for FF56 from Mozilla (there is a page for old releases but I don't remember where it is) 
[https://ftp.mozilla.org/pub/firefox/releases/56.0.2/]("https://ftp.mozilla.org/pub/firefox/releases/56.0.2/")

But do note that Firefox 56 contains [publicly known vulnerabilities]("https://www.mozilla.org/security/known-vulnerabilities/firefox/").

---

### Post by vasa1 on 2017-11-17
There's also an unbranded Firefox and that should allow the use of legacy extensions.

See [http://forums.mozillazine.org/viewtopic.php?f=23&t=3035164](http://forums.mozillazine.org/viewtopic.php?f=23&t=3035164) but the procedure to install this version isn't clear to me.

---

### Post by llbrand on 2017-11-18
> **monkeybrain20122 said:**
> No, not to 56 but you can go back further with FF-esr [https://launchpad.net/~jonathonf/+archive/ubuntu/firefox-esr](https://launchpad.net/~jonathonf/+archive/ubuntu/firefox-esr) (it coexists with FF57 and is probably FF52)

Alternatively, if you must you can download the tarball for FF56 from Mozilla (there is a page for old releases but I don't remember where it is) this is a precompiled binary, so just put it in your $HOME somewhere, click "firefox" or something like that to use it. You can make a .desktop file so it will show up in your menu/dashboard. This way it bypasses the OS's updating system all together. But using outdated browser is not recommended (eventually it will be outdated)


Edited: actually I quite like FF57 and it is super fast. Are you sure you can't find replacements for your addons if that is your issue?

Thank you, that could be a temporary solution. I hope that the add ons get ported to 57 until ESR runs out of support.

FYI: I found out that the dependency problems couldn't be fixed under 14.04 since the necessary package versions weren't available for it. So I took the plunge to 16.04

There is still a version problem ](*,)(with libstdc++6 if that is important to anyone), but I'll open a different thread for that [here]("https://ubuntuforums.org/showthread.php?t=2377943&p=13712622#post13712622").

I will mark this thread as solved for now.

---

