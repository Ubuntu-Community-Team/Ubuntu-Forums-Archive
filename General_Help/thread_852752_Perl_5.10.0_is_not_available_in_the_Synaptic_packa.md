---
title: "Perl 5.10.0 is not available in the Synaptic package manager"
date: 2008-07-07
forum: General Help
---

### Post by manish779 on 2008-07-07
Hi,

I am a perl programmer, I am running ubuntu hardy 8.04. My Perl version is 5.8.8.
--
$ perl -v

This is perl, v5.8.8 built for i486-linux-gnu-thread-multi
--
My colleagues in my office use the latest perl 5.10.0 on WINDOWS. Why that is not available in the Ubuntu? When I went to the Perl.org and checked the version is available there for LINUX.

When can I expect that my lovely language is available in the Synaptic Package manager?

Regards,
Manish.

---

### Post by sdennie on 2008-07-07
Perl 5.10.0 was released in the middle of the Ubuntu 8.04 release cycle so, chances are very good that it will never be in Ubuntu 8.04.  I don't know if it's scheduled for Ubuntu 8.10 or not but, at the moment, I think the only way you can install it would be to download it from perl.org.  However, that's non-trivial because you'd likely have to uninstall 5.8.8 first which would probably break your system in the process.  Though, you might be able to install it for just your user in your home directory and then modify your environment to point at it.

---

### Post by unutbu on 2008-07-07
Perl is quite good at keeping its files in version specific directories. I had an old Red Hat system on which I compiled a version of Perl which coexisted happily along side Red Hat's rpm version.

---

### Post by nhandler on 2008-07-07
Currently, perl 5.10.0 is in the Intrepid repositories. I wouldn't recommend trying to install this on Hardy. Most likely, it would cause many other applications to stop working. However, if you have a spare machine sitting around, you can install Intrepid on that, and then install perl 5.10.0.

---

### Post by unutbu on 2008-07-07
Use checkinstall if you decide to try installing Perl 5.10.0. Then if there is a problem, at least you can uninstall it via the apt package manager.

Cheater, why do you believe apps will stop working?

---

### Post by danbuter on 2008-07-07
> **manish779 said:**
> Hi,

I am a perl programmer, I am running ubuntu hardy 8.04. My Perl version is 5.8.8.
--
$ perl -v

This is perl, v5.8.8 built for i486-linux-gnu-thread-multi
--
My colleagues in my office use the latest perl 5.10.0 on WINDOWS. Why that is not available in the Ubuntu? When I went to the Perl.org and checked the version is available there for LINUX.

When can I expect that my lovely language is available in the Synaptic Package manager?

Regards,
Manish.

Unless you want to run beta, or try installing it on your own, you have to wait until August. My biggest gripe about Ubuntu/Debian. I wish they could make it more of a rolling release.

---

### Post by manish779 on 2008-07-08
Thanks to all of you. I will wait for the 8.10 version not too far away to release :).

---

### Post by nhandler on 2008-07-11
> **unutbu said:**
> Use checkinstall if you decide to try installing Perl 5.10.0. Then if there is a problem, at least you can uninstall it via the apt package manager.

Cheater, why do you believe apps will stop working?

Certain applications require a specific version of perl to work. If he were to install perl 5.10.0 from the intrepid repositories, and then try to install an application that depends on perl 5.8.8, he would be unable to install the application without installing it from the intrepid repositories as well. Once he starts installing multiple packages from the intrepid repositories, he will start running into larger issues. My advice, just wait until Intrepid is released.

---

### Post by unutbu on 2008-07-11
Cheater, thank you very much for this piece of information.
However, I'm still confused. Let's consider Frozen Bubble.

```
apt-cache show frozen-bubble
? ([Y]/n/q) 
Package: frozen-bubble
Priority: extra
Section: universe/games
Installed-Size: 712
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Josselin Mouette <joss@debian.org>
Architecture: i386
Version: 2.1.0-1
Replaces: frozen-bubble-lib
Depends: libsdl-perl (>= 1.20-8), perl (>= 5.8.8-6.1), perlapi-5.8.8, libc6 (>= 2.5-0ubuntu1), libglib2.0-0 (>= 2.12.0), libpango1.0-0 (>= 1.15.0), libsdl-mixer1.2 (>= 1.2.6), libsdl-pango1, libsdl1.2debian (>= 1.2.10-1), frozen-bubble-data (= 2.1.0-1), fb-music-high | fb-music-low
```

Frozen bubble depends on having a perl package with version number >= 5.8.8. Wouldn't 5.10.0 suffice?
If the OP were to turn off the Intrepid repos (in sources.list) after installing perl 5.10.0, wouldn't his system continue to function? Couldn't he, for example, install frozen bubble?

---

