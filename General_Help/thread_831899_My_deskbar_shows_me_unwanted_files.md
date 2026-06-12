---
title: "My deskbar shows me unwanted files"
date: 2008-06-17
forum: General Help
---

### Post by gaijindewanai on 2008-06-17
Hi, I'm new in ubuntu.
I am using Beagle n Deskbar as my search tool and I got one problem:

my deskbar show me some unwatanted files.

for example, when I type "theme," it show me some files such as glines.xml, HACKING.html, etc.

I tried to enclude file pattern: *.xml from beagle-settings, yet I couldn't get it fixed. :(

I am totally lost here  and have no idea about what's wrong with my ubuntu..:confused:

Please help me..

Thanx in advance

------I attach my desktop screenshots, please have a look and help me

---

### Post by dbera on 2008-06-17
> **gaijindewanai said:**
> Hi, I'm new in ubuntu.
I am using Beagle n Deskbar as my search tool and I got one problem:

my deskbar show me some unwatanted files.

for example, when I type "theme," it show me some files such as glines.xml, HACKING.html, etc.

I tried to enclude file pattern: *.xml from beagle-settings, yet I couldn't get it fixed. :(

I am totally lost here  and have no idea about what's wrong with my ubuntu..:confused:

Please help me..

Thanx in advance

------I attach my desktop screenshots, please have a look and help me

Those results are not coming from the files in your home directory but from the documentation index (used mainly by yelp to search in gnome documentation). If you dont want to search in the documentation index, disable that backend in the "Backends" tab and then restart beagled by typing from a terminal "beagled --restart" (or logout/login).

---

### Post by gaijindewanai on 2008-06-17
I did that and the result is:

> 
Unknown argument '--restart'
Beagle Daemon exited with errors.  See ~/.beagle/Log/current-Beagle for more details.

I opened ~/.beagle/Log/current-Beagle and it says:
> 
20080618 04:40:03.3118 05678 Beagle  INFO: Starting Beagle Daemon (version 0.3.3)
20080618 04:40:03.8424 05678 Beagle  INFO: Running on Mono 1.2.6
20080618 04:40:03.8430 05678 Beagle  INFO: Command Line: /usr/lib/beagle/BeagleDaemon.exe --replace --bg
20080618 04:40:03.9160 05678 Beagle  WARN: Extended attributes are not supported on this filesystem. Performance will suffer as a result.

any idea?

---

### Post by dbera on 2008-06-17
> **gaijindewanai said:**
> I did that and the result is:



I opened ~/.beagle/Log/current-Beagle and it says:


any idea?

My bad :-D. "beagled --replace" or if that does not work then "beagle-shutdown" followed by "beagled"

---

