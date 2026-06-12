---
title: "Moin (MoinMoin) change from debian unstable"
date: 2005-05-19
forum: General Help
---

### Post by jamesc on 2005-05-19
I've recently installed Hoary Hedgehog on a system that was previously debian unstable.  On this I was running the latest version of the 'moin' package for the moinmoin wiki.   The data was stored in my /home partition which hasn't changed between installs.  The version of moin in Ubuntu Hoary though seems to use a completely different fomat for its data.  

I can't seem to find a way to import the old data into the even older version.

Other suggestions?

-James

---

### Post by matej on 2005-05-21
[QUOTE=jamesc]I've recently installed Hoary Hedgehog on a system that was previously debian unstable. On this I was running the latest version of the 'moin' package for the moinmoin wiki. The data was stored in my /home partition which hasn't changed between installs. The version of moin in Ubuntu Hoary though seems to use a completely different fomat for its data. 
[/QUOTE]
What version of MoinMoin was in debian unstable?

What version of MoinMoin have you now?
[QUOTE=jamesc] I can't seem to find a way to import the old data into the even older version.
Other suggestions?[/QUOTE]
Look at [MoinMoin]("http://moinmoin.wikiwikiweb.de") site, there are surely suggestions for conversion.

---

### Post by jamesc on 2005-05-21
The problem is that the data is in the format used by the version in debian unstable. (1.3.4-3) whereas ubuntu Hoary only has a now obsolete format used in version 1.2.4.

The conversion scripts provided by moinmoin seem only to go from 1.2.4 (or earlier) upwards towards the latest format 1.3.4, rather than the other way around.

Is there a straightforward way to get the most recent version of moinmoin in ubuntu?

I'd hate to have to manually convert all the data, and then only have to convert it back when 1.3.4 makes it into ubuntu.

Suggestions?

---

### Post by matej on 2005-05-22
[QUOTE=jamesc]
Is there a straightforward way to get the most recent version of moinmoin in ubuntu?[/QUOTE]
I think you can install package from debian unstable. It's not recommended to mix Ubuntu and Debian repositories, so you can download .deb [package(s)]("http://packages.debian.org/cgi-bin/search_packages.pl?keywords=moin&searchon=names&subword=1&version=unstable&release=all") and install them or temporarily add debian unstable repositories to /etc/apt/sources.list and apt-get install it.

---

