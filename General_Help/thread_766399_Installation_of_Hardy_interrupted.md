---
title: "Installation of Hardy interrupted"
date: 2008-04-25
forum: General Help
---

### Post by Sheix on 2008-04-25
Power went off in the middle of installation, after dl'ing all of the updates
And I don't know what to do...
tried to dpkg --configure -a; apt-get update/upgrade, install through synaptic... didn't help.

When I try to continue the installation it fails with error :
> dpkg: error processing /var/cache/apt/archives/libpt-1.10.10-plugins-alsa_1.10.10-1ubuntu6_i386.deb (--unpack):
 failed to delete `/var/lib/dpkg/tmp.ci': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libpt-1.10.10-plugins-alsa_1.10.10-1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I tried to remove this package, but it fails too because it's not installed properly :(.

All of gnome defaults are screwed up, i have no idea how to fix them, I think that reinstall of Hardy will help... Any ideas?

---

### Post by bullring on 2008-04-25
I'm having the same problem:

ValueError: bad marshal data
dpkg: error processing /cdrom//pool/main/p/python-apt/python-apt_0.7.4ubuntu7_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /cdrom//pool/main/p/python-apt/python-apt_0.7.4ubuntu7_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Sheix on 2008-04-25
Looks like i going to reinstall the whole thing... didn't fount any answer yet :(

---

### Post by DenKain on 2008-04-25
After hearing all of the Hardy horror upgrade stories I think I will just d/l the alt dic and use that to upgrade it instead of using the update tool....

---

### Post by Sheix on 2008-04-25
This could be ok, i have previous experience of upgrading, and it works great (on my second PC i even installed Hardy Beta)...
But who knew that power on whole block will go down??

---

