---
title: "How can I report a bug?"
date: 2014-12-12
forum: General Help
---

### Post by ygoe on 2014-12-12
There's a problem with upgrading packages that require a reboot, not creating the /var/run/reboot-required file. I need to report a bug but that doesn't seem to be possible. Whenever I click the "Report a bug" link on Launchpad, I get to a lengthy documentation about how to report bugs, without a single link to actually let me do that. The Launchpad questions section is currently broken with repeated "Timeout" errors. Last try is here, hopefully the forum still works.

If someone knows a quicker answer than going the bug report path, here's an initial report that doesn't get any attention: [http://askubuntu.com/questions/560539/var-run-reboot-required-not-set-after-unattended-kernel-update](http://askubuntu.com/questions/560539/var-run-reboot-required-not-set-after-unattended-kernel-update)

---

### Post by bapoumba on 2014-12-12
[https://launchpad.net/ubuntu/+search](https://launchpad.net/ubuntu/+search)
You should file a bug against a package, so search for it and then file the bug report.

For ex here, with abiword : [https://launchpad.net/ubuntu/+search?text=abiword](https://launchpad.net/ubuntu/+search?text=abiword), you have a report bug link that leads you here [https://launchpad.net/ubuntu/+source/abiword/+filebug](https://launchpad.net/ubuntu/+source/abiword/+filebug) where you can file your bug from the web interface.

---

### Post by ygoe on 2014-12-12
There is no package, it's the entire thing. Or what would be appropriate here? The kernel? apt-get? unattended-upgrades? dpkg?

---

### Post by ian-weisser on 2014-12-12
I think filing against the 'linux' package (for kernel-related issues) would be appropriate.

---

### Post by ygoe on 2014-12-13
Where is the URL to report bugs for the linux package? The Launchpad search is still broken and I can't find any way to search packages there.

---

### Post by bapoumba on 2014-12-13
> **LonelyPixel said:**
> Where is the URL to report bugs for the linux package? The Launchpad search is still broken and I can't find any way to search packages there.

[https://launchpad.net/ubuntu/+search?text=linux](https://launchpad.net/ubuntu/+search?text=linux)

A bit more info could help. Looked around for bugs reported on your issue, not sure these are relevant :

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=694732](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=694732)
[https://answers.launchpad.net/ubuntu/+source/update-motd/+question/156743](https://answers.launchpad.net/ubuntu/+source/update-motd/+question/156743)
[https://lists.ubuntu.com/archives/kernel-bugs/2010-October/152222.html](https://lists.ubuntu.com/archives/kernel-bugs/2010-October/152222.html)

---

### Post by ygoe on 2014-12-13
No, those links are not what I mean.

What more info do you need? I think I described all there is in the askubuntu question linked in my first post.

---

### Post by bapoumba on 2014-12-13
Do not you see this ? May be some config or extension in your browser ?

---

### Post by ygoe on 2014-12-13
Yes, now I get what's on the screenshot. Before, it just said "Timeout error - we have logged this error" or something. Looked like a ligitimate error message from Launchpad. Seems fixed.

---

