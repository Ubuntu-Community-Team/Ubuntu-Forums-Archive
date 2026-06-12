---
title: "webmin yields &quot;failure to get local socket name&quot; only???"
date: 2007-01-16
forum: General Help
---

### Post by bobmct on 2007-01-16
:confused: 
I'm building an Ubuntu 6.06.1 SERVER distro box and to assist with the general admin I've installed Webmin 1.310 from the tar and installed using its setup.sh script.  I've made the minor miniserv.conf alterations needed and it seems to start just fine.  However, when I try to access it from ANY browser it never completes.  My /var/log/webmin/error.log file shows only the above stated message about failing to get the local socket name.

Does anyone have any idea what that means and more to the point, how I might go about correcting it?  I've never had any issues installing webmin before, even on another ubuntu box.

Idease?  Help? 

Thanks](*,)

---

### Post by dcstar on 2007-01-16
> **bobmct said:**
> :confused: 
I'm building an Ubuntu 6.06.1 SERVER distro box and to assist with the general admin I've installed Webmin 1.310 from the tar and installed using its setup.sh script.  I've made the minor miniserv.conf alterations needed and it seems to start just fine.  However, when I try to access it from ANY browser it never completes.  My /var/log/webmin/error.log file shows only the above stated message about failing to get the local socket name.

Does anyone have any idea what that means and more to the point, how I might go about correcting it?  I've never had any issues installing webmin before, even on another ubuntu box.

Idease?  Help? 

Thanks](*,)

One assumes you have a web server installed and running as well?

---

### Post by bobmct on 2007-01-17
One assumes correctly!  That does work!

---

### Post by dcstar on 2007-01-17
> **bobmct said:**
> One assumes correctly!  That does work!

I remember playing around with Webmin on Ubuntu a couple of years ago and getting nowhere until I discovered that I needed another package installed to actually allow it to configure the web server correctly.

I cannot recall exactly what package it was, but I do remember that there were no obvious error messages about it.

I can only suggest you check to see what web-server based packages may not be installed and try a few of them to see if it helps (or try and compare them with a system that does work).

---

