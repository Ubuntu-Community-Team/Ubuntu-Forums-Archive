---
title: "Upgrading from Debian to Xbuntu by editing sources.list"
date: 2007-01-14
forum: General Help
---

### Post by Third Thoughts on 2007-01-14
I've got an old laptop with no CD drive that I managed to get Debian onto through much dint of effort and hacking around. It involved using a Debian specific boot disk and an external CD drive, and I know of no way of replicating the feet with an Xbuntu CD disk. So my question is would it be possible to upgrade to Xbuntu simply by editing my /etc/apt/source.list file, and if so exactly how would this edit look. The Debian system I've got has been alright, but there are a few things that I know would be easier with Xbuntu just because I'm more used to the Ubuntu system. It seems that it should be theoretically possible to do this, but I'm reluctant to break a system that I've at least got stable, although not as functional as I'd like.

~Andrew S.

---

### Post by kerry_s on 2007-01-14
You can just add xfce4 to debian to get a xubuntu like system. But since it sounds like you want to try any ways.Here's my sources.list-> 

```
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe

deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe

deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu/ edgy-security main restricted multiverse universe

# deb http://www.debian-multimedia.org/ etch main

```

---

### Post by Ramses de Norre on 2007-01-14
It can work if all ubuntu packages have a higher version number than the debian ones, but if there are debian packages with a higher version too you'll get a mix of ubuntu and debian packages which could result in an almost unresolvable dependency hell...

If you've got a fairly old debian version the chance of being successful will be higher I think. But in any case the upgrade isn't meant to be made so it's at your own risk.

PS: I know it was possible with breezy, but ubuntu was closer to debian at that time than it is now.

---

### Post by nezroy on 2007-01-27
I just did this on a box running debian unstable (no particular dist probably... been going for 3+ years with random dist-upgrades along the way, so it was quite current anyhow), and it actually worked, though it was a fair bit of effort.

First I stripped all the packages off the system that I didn't absolutely need; went from ~1300 to about ~300. It was basically just a minimal command line server at that point. Then I updated my sources.list with the entries provided by an above poster, and did an apt-get update and apt-get dist-upgrade. You may want to grab the Ubuntu public keys from one of those sources first and add it with apt-key, or else just ignore the various signing warnings.

After several rounds of dist-upgrade, I had a setup that apt was at least happy with, though it was by no means Ubuntu. I then went through and downgraded every single package I had installed to the Ubuntu version (since the debian unstable versions I had were generally slightly newer). I started with aptitude and a few other core things (sysv stuff and upstart), following dependencies as needed. (Do this in aptitude by highlighting the package and hitting "v" to see the available versions... generally the Ubuntu versions say "ubuntu" in them, or else they're just the one older version than what you're running if you have debian unstable).

During this phase there were a few things that I had to dpkg --force-depends --purge out, because the debian packages conflicted with Ubuntu packages and apt was not smart enough to figure out the cross-dependencies. There were also a few --force-overwrite's in there as well for the same reasons. I only did this for a few items though. After about 6 or 7 rounds of this, I had pretty much my entire package list on Ubuntu releases. Oh, at some point in there I also installed the ubuntu-standard package to pick up any odds and ends I was lacking from Ubuntu's standard install, though apt dependencies picked up pretty much everything anyway.

The last issue I had was that several packages seemed to be stuck with their debian layout/config, even after downgrading to the Ubuntu version, forcing a re-install, and trying a reconfigure. These I ended up just dpkg --force-depends --purge'ing on the command line, and then immediately running aptitude to download and reinstall the Ubuntu equivalent. This seemed most prominent with /etc stuff between dists... in particular I had issues with udev and mdadm along these lines, but the purge/reinstall sorted that out. I also didn't have much by way of custom configuration for either of these so that was good.

Lastly, I grabbed the Ubuntu 2.6.17-generic kernel image and configured grub to launch that. Note that Ubuntu 6.10 does the whole weird UUID thing for drive names, so /etc/fstab and your root= kernel parameter can be somewhat goofy looking. My /etc/fstab got automatically updated by Ubuntu's netbase package, and my update-grub got everything right in my menu.lst.

And then, crossing my fingers, I rebooted my box and up it came with Ubuntu startup tools and a working generic kernel. Note that I had not restarted since starting the whole process, and I doubt it was in a bootable state at any time earlier, so if you hose yourself, you're probably done for. Even my backup kernel would not load for some reason after these changes, so luckily the generic kernel worked just fine for me, otherwise I would have been toast.

Then it was just a matter of going through and dpkg-reconfigure'ing the remaining stuff that's changed, or else just doing the dpkg --force-depends --purge/reinstall on them, to get the last bits and pieces over to a fully Ubuntu-style install on disk.

NOTE: On my first boot, I had a variety of md/raid and eth* issues, but these were ultimately caused by the mixed state of mdadm and udev packages. Purging and resintalling them resolved my problems though. I don't boot of my raid drive so missing it wasn't a big problem, and likewise I had a local connection to the box so not having networking for a while wasn't an issue either, but it could potentially but someone else in a totally borked state if you have more restrictions than I do.

---

