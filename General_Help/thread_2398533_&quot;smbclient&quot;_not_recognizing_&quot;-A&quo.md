---
title: "&quot;smbclient&quot; not recognizing &quot;-A&quot; flag in Bionic"
date: 2018-08-13
forum: General Help
---

### Post by harisund2 on 2018-08-13
The "smbclient" tool to connect to samba servers should recognize a "-A authfile" flag. 

While this works in Xenial as expected, in Bionic the -A file is completely ignored. I had to turn on verbose debugging on both client and server side to identify what was going on and why all my attempts at connections were being ignored. 

Is there a bug report already to address this? Can someone verify this for me and tell me if the -A flag is working for them?

---

### Post by oldos2er on 2018-08-13
Have you checked launchpad.net to see if a bug report already exists? Otherwise use ```
ubuntu-bug smbclient
``` to report it per [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

