---
title: "[SOLVED] Help, first real install on Xubuntu"
date: 2007-11-21
forum: General Help
---

### Post by imprez55 on 2007-11-21
This is my first linux experience, so it is a clean install with nothing but adobe flash player added on.

For the past 7 hours I have non stop been trying to install banchee. I know this should not be a difficult thing to do, but i just can't seem to get it right. I have tried the simple **sudo apt-get install banshee** and then just being under root.I have tried downloading each dependency but that did not work somehow. I did a search and it was recommended to use yum to automatically download dependencies, so i tried that for an hour or so. I noticed i needed to download rpm, so I did, but could not install that. I was able to download and install python-rpm, a weak victory because it does not help.

In short I am in over my head. If there is anyway you can help me please say so. You will probably need a readout from something, so just ask and i will give it to you

---

### Post by Craigus on 2007-11-21
What happens when you do:

> sudo apt-get install banshee

Also, which xubuntu version are we talkng about?

---

### Post by MrFSL on 2007-11-21
what is the output of:
```
sudo apt-get install banshee
```
?

Before running this it probably isn't a bad idea to update your packages:
```
sudo apt-get update
sudo apt-get upgrade
```

And also make sure you have the universe repo enabled.

System > Administration Software Sources

---

### Post by mali2297 on 2007-11-21
My guess is that you haven't enabled the "universe" repository. You can manage software repositories from within Synaptic by selecting "Settings" > "Repositories".

---

### Post by imprez55 on 2007-11-21
I am using the gutsy gibbon release of xubuntu. Also the universe repositories have, and still are in place.
Read out of everything after the install banshee command after I have updated:

***@***-desktop:~$ sudo apt-get install banshee
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  banshee: Depends: libmusicbrainz4c2a (>= 2.1.5) but it is not installable
           Depends: libnjb5 but it is not installable
           Depends: mono-runtime (>= 1.1.8.1) but it is not installable
           Depends: boo (>= 0.7.6.2237) but it is not going to be installed
           Depends: libgconf2.0-cil (>= 2.16.0) but it is not installable
           Depends: libglade2.0-cil (>= 2.10.2) but it is not installable
           Depends: libglib2.0-cil (>= 2.10.2) but it is not installable
           Depends: libgnome-vfs2.0-cil (>= 2.16.0) but it is not installable
           Depends: libgnome2.0-cil (>= 2.16.0) but it is not installable
           Depends: libgtk2.0-cil (>= 2.10.2) but it is not installable
           Depends: libmono-cairo2.0-cil (>= 1.0) but it is not installable
           Depends: libmono-corlib1.0-cil (>= 1.0) but it is not installable
           Depends: libmono-corlib2.0-cil (>= 1.2.4) but it is not installable
           Depends: libmono-security2.0-cil (>= 1.0) but it is not installable
           Depends: libmono-sharpzip2.84-cil (>= 1.0) but it is not installable
           Depends: libmono-sqlite2.0-cil (>= 1.0) but it is not installable
           Depends: libmono-system-data2.0-cil (>= 1.0) but it is not installable
           Depends: libmono-system-web2.0-cil (>= 1.0) but it is not installable
           Depends: libmono-system2.0-cil (>= 1.2.4) but it is not installable
           Depends: libmono1.0-cil (>= 1.2.4) but it is not installable
           Depends: libmono2.0-cil (>= 1.2.4) but it is not installable
           Depends: libndesk-dbus-glib1.0-cil (>= 0.3) but it is not installable
           Depends: libndesk-dbus1.0-cil (>= 0.4) but it is not installable
           Depends: libtaglib2.0-cil (>= 2.0.2.0) but it is not going to be installed
           Depends: gstreamer0.10-plugins-base but it is not installable
           Depends: gstreamer0.10-plugins-good (>= 0.10.6) but it is not installable
           Depends: gstreamer0.10-gnomevfs but it is not installable
           Depends: gnome-volume-manager but it is not installable
E: Broken packages

---

### Post by mali2297 on 2007-11-21
Have you tried to install any other package from the universe repository?

You can also check if it helps to download from another server.

---

### Post by imprez55 on 2007-11-21
I have not really tried to download anything else from the universe repository, what would you reccommend being a good test.
I tried 2 different servers and they gave the same read out as above.

---

### Post by imprez55 on 2007-11-21
Wow, do I feel stupid that I did not see this when changing the server. Somehow the main repository was unchecked. Well, thank you very much for your responses. Solved!

---

