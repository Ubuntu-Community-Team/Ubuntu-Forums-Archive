---
title: "For All Newbies! Install Swiftfox!"
date: 2008-06-03
forum: General Help
---

### Post by ForksHolder on 2008-06-03
Hello dear Ubuntu users,

I guess you all know Firefox, the general Ubuntu browser.
Well, Firefox is a great browser, But you can make it faster :)

There is a Firefox based browser called Swiftfox who is very fast and great to use.

To install it, just follow this easy steps:

1. First of all, go to terminal. (Applications->Accessories->Terminal)
2. Choose the package for your processor:

for Athlon64:
> wget [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-amd64/swiftfox_3.0pre-4_athlon64.deb](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-amd64/swiftfox_3.0pre-4_athlon64.deb)

Athlon 64 (32bit OS):
> wget [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_athlon64-32bit.deb](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_athlon64-32bit.deb)

Athlon-XP:
> wget [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_athlon-xp.deb](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_athlon-xp.deb)

Sempron:
> wget [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_athlon-xp.deb](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_athlon-xp.deb)

Duron:
> wget [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_athlon-xp.deb](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_athlon-xp.deb)

Athlon (Thunderbird):
> wget [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_i686.deb](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_i686.deb)

Pentium 4:
> wget [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_pentium4.deb](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_pentium4.deb)

Prescott:
> wget [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_prescott.deb](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_prescott.deb)

Core Solo/Duo:
> wget [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_prescott.deb](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_prescott.deb)

Pentium M: (The one I use :-P )
> wget [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_pentium-m.deb](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_pentium-m.deb)

Pentium 3:
> wget [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_pentium3.deb](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_pentium3.deb)

Pentium 3M:
> wget [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_pentium3m.deb](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_pentium3m.deb)

Celeron (Willamette, Northwood, Celeron D):
> wget [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_pentium4.deb](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_pentium4.deb)

Celeron M:
> wget [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_pentium-m.deb](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_pentium-m.deb)

Celeron (Coppermine, Tualatin):
> wget [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_pentium3.deb](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_pentium3.deb)

Pentium 2:
> wget [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_i686.deb](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/swiftfox_3.0pre-4_i686.deb)


3. In the terminal, write this command:
> ls

It will show you every file/folder in the directory.
You need to see a file called something like **swiftfox_3.0pre-4_pentium-m.deb** in there.

Then, copy the file name and make this command in the Terminal:
> dpkg -i *Name of the file*

Of course you need to change it to the name of the file..
For example:

> dpkg -i swiftfox_3.0pre-4_pentium-m.deb.

5) Close Firefox, and go to Applocations->Internet->Swiftfox!

6) Enjoy the fast browser :)

*NOTE*
If you wanna make your browser even faster than it is, Install the [Fasterfox]("https://addons.mozilla.org/en-US/firefox/addon/1269") addon :)

Enjoy :]
~ForksHolder

---

### Post by ForksHolder on 2008-06-03
Oh, and forgot to say,

**Installing Swiftfox with firefox at the same time IS possable.**

That means that if you don't like Swiftfox for some reason, you can just browse in firefox, they're both installed at the same time.

Enjoy :]

---

### Post by Dr.Ninethousand on 2008-06-03
I also recommend Swiftweasel:

[http://swiftweasel.tuxfamily.org/about.php](http://swiftweasel.tuxfamily.org/about.php)


ps-  the site doesn't really tell you, but if you have a 64bit OS and want the 32bit version of Swiftweasel (for java) you just change the line like this:

apt-get install swiftweasel-cpuarchversion
apt-get install swiftweasel32-cpuarchversion

---

### Post by marcelo danico on 2008-06-06
Thanks forksholder, I needed this how-to just now.

Maybe you can edit the first post so the links are not shortened, just uncheck the "Automatically parse links in text" under Miscellaneous Options.
That way a lazy guy like me can just copy and paste into the terminal.

Cheers:)

---

### Post by marcelo danico on 2008-06-06
YES! Much, much fassster.
:guitar:

---

### Post by ForksHolder on 2008-06-09
> **marcelo danico said:**
> Thanks forksholder, I needed this how-to just now.

Maybe you can edit the first post so the links are not shortened, just uncheck the "Automatically parse links in text" under Miscellaneous Options.
That way a lazy guy like me can just copy and paste into the terminal.

Cheers:)

Ehum.. I've tried to remove the V in it but nothing will work oO wierd..

Thanks :]

---

