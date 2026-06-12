---
title: "xmlcopyeditor on 12.04"
date: 2012-10-24
forum: General Help
---

### Post by pastim on 2012-10-24
On 12.04, 64 bit, I cannot get a stable version of xmlcopyeditor.  The version from Software Centre installs but does not run.   Even from a terminal it outputs no messages to the terminal, and fails to do anything at all.

Following instructions in bug report #901547 12 ([https://bugs.launchpad.net/ubuntu/+source/xmlcopyeditor/+bug/901547/comments/12](https://bugs.launchpad.net/ubuntu/+source/xmlcopyeditor/+bug/901547/comments/12)) I installed a version that does run.  

However, ubuntu now says it wants to install an update.  If I let it proceed then I get the version that does not work.  I then have to reinstall the version that does work.  Both versions have the same number - 1.2.0.6-2 .  

I tried freezing the version that works using synaptic, but Software Updater still insists it must update the version.  

I am well aware I don't need to let Software Updater go ahead and replace the working version with one that won't run, but it's a nuisance to have to un-tick it every time.  It's also a nuisance that I am constantly told there are updates to install for this version.

I have found this no annoying I had to remove xmlcopyeditor.

Is there any solution?

---

### Post by danielbauwens on 2012-10-24
Found this, hope it helps.
[QUOTE=Hagar Delest]On 12.04, installed that one: [http://pkgs.org/debian-wheezy/debian-main-amd64/xmlcopyeditor_1.2.0.6-2+b1_amd64.deb.html](http://pkgs.org/debian-wheezy/debian-main-amd64/xmlcopyeditor_1.2.0.6-2+b1_amd64.deb.html)
and it works fine.[/QUOTE]

---

### Post by pastim on 2012-10-25
There is now a ppa that provides a fixed version for ubuntu precise and quantal, both i386 & amd64.  This is documented in the launchpad bug report, and also see  [https://code.launchpad.net/~mariusko/+recipe/xmlcopyeditor-daily](https://code.launchpad.net/~mariusko/+recipe/xmlcopyeditor-daily)

---

