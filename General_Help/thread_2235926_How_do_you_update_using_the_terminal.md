---
title: "How do you update using the terminal ?"
date: 2014-07-23
forum: General Help
---

### Post by pretty_whistle on 2014-07-23
How do you update using the terminal ?  What do I type in?

Also another question:

There are a few programs I've marked in Synaptic to not update.  If I update using the terminal will it know to not update these few programs?

---

### Post by deadflowr on 2014-07-23
You can check /etc/apt/preferences.
Looky over this
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

---

### Post by vasa1 on 2014-07-23
> **pretty_whistle said:**
> ...
Also another question:

There are a few programs I've marked in Synaptic to not update.  If I update using the terminal will it know to not update these few programs?

Look at this as well: [http://ubuntuforums.org/showthread.php?t=2235031&p=13077158#post13077158](http://ubuntuforums.org/showthread.php?t=2235031&p=13077158#post13077158)

---

### Post by gilligan216 on 2014-07-23
type "sudo apt-get update" from the terminal window.

---

### Post by deadflowr on 2014-07-23
> **gilligan216 said:**
> type "sudo apt-get update" from the terminal window.

That only updates the package lists.
sudo apt-get upgrade or sudo apt-get dist-upgrade will update the packages.

That said, on top of my previous post, all packages that can be updated will be listed, and you will always have a choice to cancel it before running the actual upgrade process, by simply choosing n(no).
I always review the packages being upgraded, even if that review is sometimes not as thorough.
I at least make note of whatever packages are listed.

---

### Post by sammiev on 2014-07-23
I usually use this command.
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by pretty_whistle on 2014-07-24
> **deadflowr said:**
> That only updates the package lists.
sudo apt-get upgrade or sudo apt-get dist-upgrade will update the packages.

That said, on top of my previous post, all packages that can be updated will be listed, and you will always have a choice to cancel it before running the actual upgrade process, by simply choosing n(no).
I always review the packages being upgraded, even if that review is sometimes not as thorough.
I at least make note of whatever packages are listed.

sudo apt-get upgrade or sudo apt-get dist-upgrade will update the packages?  Will this also upgrade 14.04 to 14.10 when it becomes available?

---

### Post by deadflowr on 2014-07-24
> **pretty_whistle said:**
> sudo apt-get upgrade or sudo apt-get dist-upgrade will update the packages?  Will this also upgrade 14.04 to 14.10 when it becomes available?

No.

To upgrade releases you would run an entirely different command:
```
do-release-upgrade
```
to upgrade to a development release, like utopic unicorn right now, simply add a -d to the end of that command.
(-d = development)
Similarly, if you ran update-manager -d, it would give you the option to upgrade to the development release via gui, much like when a new release is offer via gui(update manager) and a new banner or option comes up for whatever version is currently in development; that you can upgrade to.

Hope that helps...

---

### Post by sudodus on 2014-07-24
> **pretty_whistle said:**
> sudo apt-get upgrade or sudo apt-get dist-upgrade will update the packages?  Will this also upgrade 14.04 to 14.10 when it becomes available?

Yes, ***sudo apt-get upgrade*** or ***sudo apt-get dist-upgrade*** will update the  packages, but only within a version for example 14.04 (including the point versions 14.04.1 ... )

To also upgrade 14.04 to 14.10 when it becomes  available, you should first ***backup*** everything important, make your current version up to date, then remove PPAs and other non-standard packages to increase the chances to succeed. You can add the PPAs again afterwards.

Then run ```
sudo do-release-upgrade
```

But I keep an LTS release in my production computer until the first point release of the next LTS release instead of upgrading to the nine-months releases.

So I keep 12.04 LTS until 14.04.1 LTS is released and an upgrade directly from 12.04 LTS to 14.04(.1) LTS will be offered in the GUI updating tool.

---

### Post by pretty_whistle on 2014-07-24
Running ***sudo apt-get upgrade ***will update *only* Ubuntu packages or will it update even the 3rd party programs that I installed separately like Thunderbird email?

---

### Post by sudodus on 2014-07-24
All packages installed from the repositories and PPAs so also T-bird.

---

### Post by pretty_whistle on 2014-07-24
Ok.  Got it.  Thanks for everyone's help. :)

I'll mark this as solved.

:)

---

