---
title: "Problems installing apps"
date: 2007-10-01
forum: General Help
---

### Post by tech9 on 2007-10-01
I cannot install ClamAV, then I tried installing other apps and ... no dice

Here is the error...

Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up clamav-base (0.90.2-0ubuntu1) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.90.2-0ubuntu1); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
**E: Sub-process /usr/bin/dpkg returned an error code (1)**

any ideas why there are problems with dpkg?

BTW... system is "up-to-date"

---

### Post by tech9 on 2007-10-01
Nevermind! I fixed it... I am not asking 4 help anymore seeing that no one replies or bothers to help....:-x

---

### Post by kellemes on 2007-10-01
> **tech9 said:**
> Nevermind! I fixed it... I am not asking 4 help anymore seeing that no one replies or bothers to help....:-x

So you actually think we're waiting for you to come for support? So we can answer your question immediatly? We're on your payroll or what?
Sorry dude, most of us have a life and try to help in our sparetime.. If you need more support go get RHEL.

---

### Post by tech9 on 2007-10-01
> **kellemes said:**
> So you actually think we're waiting for you to come for support? So we can answer your question immediatly? We're on your payroll or what?
Sorry dude, most of us have a life and try to help in our sparetime.. If you need more support go get RHEL.

I do realize this, I was just in the "heat of the moment" I figured it out, but there is no need to be rude about it

---

