---
title: "Apache Serving Files &gt; 2gb"
date: 2006-11-25
forum: General Help
---

### Post by krisrmgua on 2006-11-25
I installed ubuntu Edgy and went on this website [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Apache_HTTP_Server) and installed appache.  sudo apt-get install apache2
Everything works great but yet when i have files larger than 2gb they dont appear. I installed Fedora Core six and it works just fine on fedora serving large files but not on Ubuntu. I would rather use ubuntu anyone able to help on how to get it to work?

---

### Post by mayonaise15 on 2006-11-26
It looks like this was a bug that was [fixed in Apache version 2.2]("http://httpd.apache.org/docs/2.2/new_features_2_2.html").  When I open up Synaptic and search for Apache, I see that the version in the repo is 2.0.55-4 :cry:

---

### Post by krisrmgua on 2006-11-26
So do we have to wait for ubuntu to update that to fix the bug?

---

### Post by mayonaise15 on 2006-11-26
Well, a quick search for "apache 2.2 ubuntu" on Google only came up with a few how-to articles on building it from source.  That is alway an option, depending on how comfortable you are with it.

---

### Post by krisrmgua on 2007-02-09
not comfortable at all

---

### Post by towsonu2003 on 2007-02-09
you could try filing a bug against apache in launchpad.net, link your fixed bug as upstream bug, and request a backport of the fix (ie ask them upload a fixed version to the repository). 

may or may not work. probably wont work-

there is also a separate backporting team (check out their forum section) who may be able to help (or maybe not). 

the tools used by the backporting team may be very useful to you if you want to backport apache2 (2.2.3) from feisty to your ubuntu version. backporting, in this case, means using debian tools to compile apache2 2.2.3 that is uploaded to feisty from source for your system. the team's tools make that whole thing automated. 

I, for instance, backported texlive (all of it) to dapper from edgy (total of packages: 350MB) and it was very easy (following instructions).

---

