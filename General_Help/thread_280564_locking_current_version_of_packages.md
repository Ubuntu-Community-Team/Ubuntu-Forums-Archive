---
title: "locking current version of packages"
date: 2006-10-19
forum: General Help
---

### Post by Rule on 2006-10-19
hey, I made a deb package using checkinstall of the new giam beta 4 but synaptic wants to "upgrade" it to beta3 :-k 

anyone know how I can tell it to keep beta4, cause when I use synaptic to do it, it doesnt work at all it still wants to "upgrade" it.

TIA
Rule

---

### Post by gborzi on 2006-10-19
Use the following command > echo <packagename> hold|sudo dpkg --set-selections
and to check that the change was successful use this > dpkg --get-selections | grep hold
that should list all the packages in hold.

---

### Post by Rule on 2006-10-19
it still wants to install gaim beta3 :(

---

### Post by AgenT on 2006-10-19
> **gborzi said:**
> Use the following command 
and to check that the change was successful use this 
that should list all the packages in hold.
That is an interesting way of doing it. You may also find using [/etc/apt/preferences]("http://jaqque.sbih.org/kplug/apt-pinning.html") a good way as well. Please be aware that there is a [bug/feature]("https://launchpad.net/distros/ubuntu/+source/synaptic/+bug/42178") where pinning with apt and pinning in synaptic do not hold for the other.

gborzi (or someone else): can you try pinning using Synaptic? It does not work for me. It looks like it's successful, but going back to the package shows that it does not pin. If it does not work for you, I will file a bug report.

---

### Post by gborzi on 2006-10-19
> **AgenT said:**
> That is an interesting way of doing it. You may also find using [/etc/apt/preferences]("http://jaqque.sbih.org/kplug/apt-pinning.html") a good way as well.

Thanks, I didn't know this other way.

> **AgenT said:**
> 
gborzi (or someone else): can you try pinning using Synaptic? It does not work for me. It looks like it's successful, but going back to the package shows that it does not pin. If it does not work for you, I will file a bug report.
It's working for me. Is the problem related to some specific package, or does it happens with any package you try ?

---

### Post by AgenT on 2006-10-19
> **gborzi said:**
> It's working for me. Is the problem related to some specific package, or does it happens with any package you try ?
I tried these packages:
metacity
some gstreamer0.10 plugin
openoffice.org
adduser
bluefish
Come to think of it, I do hope it's not working or else I may find myself with problems down the road with all these random packages being locked. Do note that none are marked locked in Synaptic, nor are they under (my custom) "Pinned" filter.

Also, sudo dpkg --get-selections | grep hold shows nothing (empty).

What package did you lock so I may have an exact example.

EDIT: Are you using a "fresh" install of Edgy or have you dist-upgraded from a previous release (and what is the earliest release that you dist-upgraded up until now?). This may be a  problem with some outdated configuration file or package left from a different Ubuntu release.

---

### Post by gborzi on 2006-10-19
I'm still using dapper. I downgraded and pinned metacity successfully. So, in dapper it's working.
I made my previous test with keytouch-editor. I'm the packager of this program, so I have a version newer than that available from the public repositories in a local repository.

---

### Post by AgenT on 2006-10-19
Synaptic does not require more than one available version of a package to be available in Synaptic for locking/pinning to work, does it?

Also, what version of Synaptic are you using?

EDIT: downloaded newest unstable version from Debian and looking at the changelog there is no mention of locking/pinning problems.

---

### Post by gborzi on 2006-10-20
I'm using synaptic 0.57.8. It is possible to pin packages available in only one version, to avoid upgrades from eventual updates of the package. I used packages with more than one version to be sure that a "Reload Package information" does not unpin packages.

---

### Post by AgenT on 2006-10-20
While the Synaptic About page lists it as 0.57.8, the package is 0.57.11. Will file a bug report.

---

