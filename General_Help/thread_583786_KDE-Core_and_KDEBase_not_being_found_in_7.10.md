---
title: "KDE-Core and KDEBase not being found in 7.10"
date: 2007-10-20
forum: General Help
---

### Post by Igtenio on 2007-10-20
On Thursday, I downloaded Gutsy Gibbon. I was looking forward to playing with both CDs, since for Feisty Fawn, I'd created a script to setup a system just the way I like it. It adds some repositories, installs packages, et cetera.

I run it on a Command-Line installation system, since that gives me what I want; a no-frills OS that has enough Ubuntu to make me happy, while not having any branding, so to speak.

My Desktop of choice is KDE, so I install KDE-Core.

I got the Alternate CD, installed a command-line system, and went to install the bare essentials first; Xorg, KDE-Core, KDM, and Synaptic.

I got an error about KDE-Core not being available. So I substituted KDEBase for it, and got a similar error message.

I've run apt-get update already, and it does the same thing. Here're the error messages when I run just "apt-get install kde-core" or kdebase;

KDE-Core
```

igtenio@Deucalion:~$ sudo apt-get install kde-core
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package kde-core
igtenio@Deucalion:~$

```

KDEBase
```

igtenio@Deucalion:~$ sudo apt-get install kdebase
Package kdebase is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  gnome-icon-theme
E: Package kdebase has no installation candidate
igtenio@Deucalion:~$

```

Any ideas? Initially, I figured the servers might just be bogged down and spitting out errors. But by now, the best I can think of is that, possibly, Canonical has removed the major KDE elements from the Ubuntu repository and shunted them into solely being in the Kubuntu repository. I figure, however, I would've read something somewhere about it if that was the case.

It's just a base installation of the Command-Line system; I haven't installed anything or played with any of the settings. At the moment, I'm just experimenting, so I haven't altered anything out of the gate.

---

### Post by FredB on 2007-10-20
KdeBase is available, and kde-core too.

Maybe a not really up-to-date apt database ?

---

### Post by Igtenio on 2007-10-21
I'm hoping that's it. I knew I missed something. I don't mess with repositories much, so I haven't thought of them not having updated the listings.

I've just run apt-get update again a few moments ago, and I get the exact same results when I try "apt-get install kde-core" or kdebase.

It makes me wonder, however, why no one else has come across issues if that's really the problem.

Or I really am the first schmuck to try installing KDE-Core and KDEBase on Gutsy. :P

**Update**: I just went looking in Sources.list, on a hunch, and found a few lines commented out by the installer because it "failed to verify". Which is weird, since I sat right here and watched it install on the machine physically connected to the router, and nothing went wrong.

This'll probably fix it, but it still makes me wonder what went wrong, and when.

---

