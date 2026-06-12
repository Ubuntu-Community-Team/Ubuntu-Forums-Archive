---
title: "Building app from source - uninstall prev. version first?"
date: 2008-06-13
forum: General Help
---

### Post by HunterSBuntu on 2008-06-13
Hi,

I'm new to compiling applications from source, should I be uninstalling a previously installed version beforehand or is any updating / overwriting taken care of in the build process?

Specifically, I'm looking at going from nmap 4.53 to 4.60, but I'm curious about the issue in general.

In the case of nmap, if I uninstall 4.53 using Synaptics, will it remove libraries I need for 4.60 giving me a dependency nightmare?

Thanks.

---

### Post by cariboo on 2008-06-13
Out of curiosity what does the new version do that the old one doesn't. I couldn't find a changelog (mind you I didn't look to hard either:) )

Jim

---

### Post by HunterSBuntu on 2008-06-14
Changelog is here:
[http://nmap.org/changelog.html]("http://nmap.org/changelog.html")

I don't actually need to upgrade for any particular reason, just saw there was a newer version and figured this was a good excuse to learn about compiling programs from the source code.

---

### Post by DirtDawg on 2008-06-14
I would recommend uninstalling any previous version before installing a freshly built version.

In general, if you uninstall an application, Synaptic will only remove dependent libraries if the said program is the only one dependent on the library (if that makes sense). Usually, it will ask you if you would like to remove the library in question. Well, that's what happens when using the command line anyways, I'm not sure about the GUI package manager.

Also, you could build the program (configure, make), then uninstall the older version before using the install or checkinstall commands. That way you won't need to worry about dependencies being removed.

Hope this helps.

---

### Post by nowshining on 2008-06-14
to create a deb

sudo checkinstall -D make install

y for docs Question

create a description i usually copy+paste the one in synaptic or so or on the website a part of it.

type 0 - use a diff maintainer than root - u can use ur ubuntu username if u'd like, etc..

:)

hopefully it will install.

However install build-essential first and if it asks for any libs - u need the -dev versions - then try again until u ./configure correctly.

it's easier than u might think. :) i too once thought it would be hard to do so and wondered how it would be done until i started using linux. Now again I know it's Easy. ;)

- lastly i suggest sharing it - create a 4shared free account. :)

---

