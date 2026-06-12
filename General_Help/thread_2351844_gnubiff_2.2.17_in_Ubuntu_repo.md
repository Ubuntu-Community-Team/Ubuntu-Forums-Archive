---
title: "gnubiff 2.2.17 in Ubuntu repo?"
date: 2017-02-07
forum: General Help
---

### Post by fizikz on 2017-02-07
When will gnubiff 2.2.17 be available in the Ubuntu repo for Xenial? The current version 2.2.16 has a bug where the configuration file is not written or read, so that gnubiff must be reconfigured on each reboot. [https://sourceforge.net/p/gnubiff/bugs/60/](https://sourceforge.net/p/gnubiff/bugs/60/)

Of course, it can be compiled from source, but it's much easier to maintain if it comes from the repo.

---

### Post by ian-weisser on 2017-02-07
See [https://tracker.debian.org/pkg/gnubiff](https://tracker.debian.org/pkg/gnubiff)

The volunteer package maintainer has dropped it, so nobody has packaged 2.2.17 for Debian, and nobody has address this issue in [Debian Bug #815632]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=815632"). Nobody in Ubuntu has volunteered to Triage or Upstream the [Ubuntu bug reports]("https://bugs.launchpad.net/ubuntu/+source/gnubiff/+bugs"). A new volunteer maintainer or two is most welcome so the community can get progress.

Since 2.2.17 is not packaged, the older, broken version was merged from Debian in 16.10 and 17.04.

When 2.2.17 is packaged, tested in Debian, merged into Ubuntu (perhaps 17.10, if a maintainer steps up soon), and released in Ubuntu comes the next hurdle: A [Stable Release Update]("https://wiki.ubuntu.com/StableReleaseUpdates") (SRU) to backport the fixed version to 16.04. SRUs are slow - A community member to propose the SRU, and Canonical engineers must test it.

There are ways to shortcut the process, but they usually wind up making more work for the few volunteers.

---

### Post by fizikz on 2017-02-07
Thanks, ian-weisser. It's unfortunate gnubiff has been orphaned; it worked pretty well.

Is there a solid mail notification package out there? I look for: multi-protocol client, icon for the panel, works nicely with gnome2, shows mail count, and being able to read email headers with a single click is a great bonus.

I'm looking into mail-notification, claws-mail-multi-notifier, newmail, coolmail, mailnag, xlassie, imaprowl, and of course gnubiff compiled from source. Many of these are not very updated or have strange glitches.

---

### Post by fizikz on 2017-02-08
Finally, I ended up compiling gnubiff-2.2.17 from source. To make installation/uninstallation a bit easier, I used the package "checkinstall", which creates a .deb file out of the installation so that it can later be uninstalled easily with dpkg. 

So, after the typical 

```
.configure
make
``` 

I followed with

```
 sudo checkinstall
``` 

instead of the usual

```
 sudo make install
```


Note: I'm using gnome2 and gnubiff developers state to use version 2.2.13 as later versions were made for gnome3+. However 2.2.13 has older dependencies that were not found in Ubuntu 16.04, such as libpanel-applet-2.0 and libgnomeui-2.0. So, I installed 2.2.17 and it seems fine.

---

