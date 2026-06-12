---
title: "Clamav error message on updating"
date: 2006-12-03
forum: General Help
---

### Post by lolwhites on 2006-12-03
When I install updates I get the following error message:
*E: clamav-base: subprocess post-installation script returned error exit status 1*

What does it mean? Is it something I should worry about and what can I do about it?

---

### Post by sitedesign on 2006-12-03
After it has installed, even with the error message try running:
dpkg-reconfigure clamav-base
in a terminal. That should help.

PS What do you want the Anti Virus for, is it to scan files that Windows boxes are using? There is no need to AV a Linux box, Linux doesn´t have any viruses yet!

---

### Post by lolwhites on 2006-12-03
Thanks for the tip - will try it next time it crops up. Then again, might I as well just uninstall clamav altogether? IIRC Automatix picked it up for me and I just went with the flow.

---

### Post by sitedesign on 2006-12-03
Clamav server little purpose protecting a Linux machine since viruses won´t hurt it.

Just uninstall it using either automatix or synaptic.

---

### Post by PrinceArithon on 2006-12-03
Sometimes the clamav just comes on during installation.  I had that same problem and I got rid of it, after that everything worked.

---

### Post by gerdt on 2006-12-13
[http://www.ubuntuforums.org/showthread.php?t=316729&highlight=clamav+crash+after+update](http://www.ubuntuforums.org/showthread.php?t=316729&highlight=clamav+crash+after+update)

---

