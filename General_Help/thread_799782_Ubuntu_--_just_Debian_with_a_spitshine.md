---
title: "Ubuntu -- just Debian with a spitshine?"
date: 2008-05-19
forum: General Help
---

### Post by judolars on 2008-05-19
Is there really any difference between Ubuntu and Debian? I mean, yes, Ubuntu has a nice graphical installer, it comes on a LiveCD, it has some nice Ubuntu-specific configuration tools, etc., but IMHO these are only superficial differences. They are all nice features, which make the OS more user-friendly and fun to use, but they are not crucial for a "power user".

What I'd like to know is: How different is Ubuntu from Debian "under the hood"? Is it more secure? Does it detect more hardware automatically? Do Ubuntu packagers make a lot of changes to the packages, or are they just copied directly from the Debian repos? Have the Ubuntu guys patched the kernel differently than the Debian guys? Etc. etc. etc.

In short: Can I build a system equivalent to Hardy by installing a core Debian system and picking the corresponding packages from the repositories (stable/unstable/testing)? (And before you ask "why would you do that???", I don't intend to. It's just a hypothetical question. :))

Regards,
Lars

---

### Post by sardion on 2008-05-20
> **judolars said:**
> Is there really any difference between Ubuntu and Debian? I mean, yes, Ubuntu has a nice graphical installer, it comes on a LiveCD, it has some nice Ubuntu-specific configuration tools, etc., but IMHO these are only superficial differences. They are all nice features, which make the OS more user-friendly and fun to use, but they are not crucial for a "power user".

What I'd like to know is: How different is Ubuntu from Debian "under the hood"? Is it more secure? Does it detect more hardware automatically? Do Ubuntu packagers make a lot of changes to the packages, or are they just copied directly from the Debian repos? Have the Ubuntu guys patched the kernel differently than the Debian guys? Etc. etc. etc.

In short: Can I build a system equivalent to Hardy by installing a core Debian system and picking the corresponding packages from the repositories (stable/unstable/testing)? (And before you ask "why would you do that???", I don't intend to. It's just a hypothetical question. :))

Regards,
Lars



So, yes, ubuntu is built off of Debian.  Speaking as a power user, the answer is, no there is a much bigger difference than you think.

Ubuntu is a polished version of Debian that is updated more frequently.  Basically, every six months (give or take) Debian testing is frozen as the next ubuntu.  Then the ubuntu teams polish those packages and make it ready for release, not just graphically, but all around.

How can they do this?  By not focusing on 11 arch's, and instead by focusing on 3.

Speaking as longtime (8 years) Debian user (and developer), my servers will always run Debian.  Its security is unmatched (ignore that little ssh bug just recently).  My desktops have been ubuntu since dapper.

You can mostly recreate ubuntu by installing the stuff from Debian... but only if you use testing or sid, and there will be more (many more) issues in the Debian packages.

---

### Post by kerry_s on 2008-05-20
> In short: Can I build a system equivalent to Hardy by installing a core Debian system and picking the corresponding packages from the repositories (stable/unstable/testing)? (And before you ask "why would you do that???", I don't intend to. It's just a hypothetical question. )



yes, using lenny/testing you'll be more up to date than the latest ubuntu, ubuntu is a snap shot of sid, by the time ubuntu gets relesed most of the stuff is fixed and in testing already. try it for yourself.

lenny net installer->
[http://cdimage.debian.org/cdimage/lenny_di_beta1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_beta1/i386/iso-cd/debian-testing-i386-businesscard.iso)

a straight install gives you gnome, it can also install kde, use the f# keys for instructions. you can also install just the base and build up from there, which is what i do to customize it for my specs.

> You can mostly recreate ubuntu by installing the stuff from Debian... but only if you use testing or sid, and there will be more (many more) issues in the Debian packages.

this is not true at all, ubuntu is built on unstable, it will always be unstable. using testing most of the bugs have been worked out before moving from sid, there is little to no problems using it everyday.

---

