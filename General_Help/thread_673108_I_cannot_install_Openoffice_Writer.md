---
title: "I cannot install Openoffice Writer"
date: 2008-01-20
forum: General Help
---

### Post by sunwatcher on 2008-01-20
I have a fresh installation of Gutsy Gibbon from a downloaded CD.  Pretty much everything is working well, but for some reason there was no Openoffice installed by default.  I went to Synaptic, beefed up the repositories, then tried to install the Openoffice Suite.  Most features seem to have installed correctly except Writer.  I subsequent tried: "sudo apt-get install openoffice.org-writer", but I got the following error message:

[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  openoffice.org-gcj
Recommended packages:
  openoffice.org-filter-binfilter
The following NEW packages will be installed:
  openoffice.org-writer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6676kB of archives.
After unpacking 20.0MB of additional disk space will be used.
(Reading database ... 106086 files and directories currently installed.)
Unpacking openoffice.org-writer (from .../openoffice.org-writer_1%3a2.3.0-1ubuntu5.3_i386.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)[/INDENT]

Does anyone have any ideas?

---

### Post by sunwatcher on 2008-01-21
No ideas?

I tried going with another mirror, but got the same result.

I tried downloading the deb files  (in a tar.giz) from Openoffice.org.  Extracted the file and tried to install the deb files directly.  This is what I got from the package manager: when I tried to install the writer deb, I was told that I was missing the core01 deb. Went to core01 and was told I was missing core02. Went to core02 and was told was missing core01.  Complete dead end.

I have been able to install and uninstall everything else without a hitch.  Openoffice Writer is just  no go.

Help!

---

### Post by Hagar Delest on 2008-01-26
If you want the official version, you need to remove the Ubuntu one, see here: install the official version of OOo : [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

