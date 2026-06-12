---
title: "How to download a package for a more recent OS than you are using?"
date: 2013-04-28
forum: General Help
---

### Post by ladasky on 2013-04-28
Hi folks,

I am in an unusual situation.  I recently moved my desktop computer, running 12.04.1, to a place where I'm having networking problems.  These problems will probably be solved if I can upgrade to 13.04.  Version 13.04 should include an updated wireless driver.  I have other reasons for wanting 13.04 as well, such as improved out-of-the-box support for Python 3.

The only tool that I have to connect me to the Internet is my older laptop, which is running 11.10.  I downloaded the 13.04 ISO file using that machine.  I moved it over to my 12.04 system on a thumb drive.  But to install 13.04 [_in the most straightforward way_]("https://help.ubuntu.com/community/Grub2/ISOBoot"), my 12.04 system needs the **grml-rescueboot** package installed.  Normally, I would just run Synaptic on 12.04, and get the package.  Obviously, that's not possible.

So, if I can only figure out how to get the *grml-rescueboot.deb* file downloaded on my 11.10 laptop, I can use the thumb drive to put it on my 12.04 machine.  But according to Synaptic, **grml-rescueboot** is not included in the 11.10 repository -- and even if it was, it might not be the right version.  How can I accomplish this?  Somewhere, there should be a web site with the repository files?  And after I get the package, I should be able to install it with a shell command?

I'm going down a parallel track -- I'm also trying to set up my laptop as a network bridge.  I have installed **bridge-utils** on my laptop, and connected the two machines with an Ethernet cable.  I have encountered several conflicting sets of instructions about how to edit the laptop's */etc/network/interfaces* file, and all of the ones I have tried have broken my connection :( .  If I had a better understanding of the issues, I could probably edit the file intelligently.  But this is something I only have to expect to do once.

Thanks for any advice!

---

### Post by ladasky on 2013-04-29
Followup: I just discovered **_[Startup Disk Creator]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu")_**.  That looks like a better choice than messing with Grub!  I may get 13.04 installed yet!

Still, the general question about how to get repositories is one that interests me... if anyone knows.

---

### Post by CatKiller on 2013-04-29
There are ways to set up local package caches, but I've never tried them.

If I need a package that isn't in the current repository (normally an older package for me) I just grab it from packages.ubuntu.com. Sometimes you have to sort out dependencies yourself, which can be a bit of a pain. Otherwise you just install the .deb file.

---

