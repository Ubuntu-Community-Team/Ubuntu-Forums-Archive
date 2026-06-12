---
title: "OpenStack Havana Installation Help"
date: 2013-11-21
forum: General Help
---

### Post by btcinema on 2013-11-21
Hello,

I have the latest ubuntu 13.10. It says that it should comes with OpenStack Havana. I only managed to install Ubuntu 13.10 core.
How can I get OpenStack Havana now? 

I'm new to this (linux, cloud drives), so I'm might be asking wrong questions. But I need OpenStack havana and I don't know how to get it :)

Please help me with this and thanks in advance!

---

### Post by grahammechanical on 2013-11-21
You need to download and install Ubuntu 13.10 server if you want Ubuntu to come with Openstack Havana.

[https://wiki.ubuntu.com/SaucySalamander/ReleaseNotes](https://wiki.ubuntu.com/SaucySalamander/ReleaseNotes)

> **Ubuntu Server**

**OpenStack 2013.2 (Havana)**

[COLOR=#333333][FONT=Ubuntu Beta]Ubuntu 13.10 includes the 2013.2 Havana release of OpenStack. OpenStack projects supported in 13.10 include: Nova, Glance, Swift, Keystone, Horizon, Cinder, Neutron and Ceilometer. Heat is also included in 13.10 in Ubuntu Universe.[/FONT][/COLOR]


[http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server)

Regards.

---

### Post by btcinema on 2013-11-21
That is the page from where I've downloaded Ubuntu 13.10. It gave me some errors and I've only managed to install the core... After 6 hours I have managed to install a GUI and other apps. Now I want Open Stack Havana :)

---

### Post by philinux on 2013-11-21
@graham

Not at my box just now. But shouldn't those packages be in the desktop repo as well?

---

### Post by btcinema on 2013-11-21
Added: deb [http://ubuntu-cloud.archive.canonical.com/ubuntu](http://ubuntu-cloud.archive.canonical.com/ubuntu) precise-updates/havana main 
to sources.list, but i get this

> #root@irix:/etc/apt# add-apt-repository cloud-archive:havana
 Ubuntu Cloud Archive for Openstack havana
 More info: [https://wiki.ubuntu.com/ServerTeam/CloudArchive](https://wiki.ubuntu.com/ServerTeam/CloudArchive)
Press [ENTER] to continue or ctrl-c to cancel adding it
cloud-archive only supported on precise#

---

### Post by keith_newstadt on 2014-01-07
Has anyone come across a solution for this yet?  Do I need to start over again with 12.04?

---

