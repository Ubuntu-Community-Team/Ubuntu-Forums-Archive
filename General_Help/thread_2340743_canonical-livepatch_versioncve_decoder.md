---
title: "canonical-livepatch version/cve decoder?"
date: 2016-10-21
forum: General Help
---

### Post by wrighrc on 2016-10-21
Hello.   I just enabled livepatch and was wondering how I'd tell if it patched 
**CVE-2016-5195**

From canonical-livepatch status --verbose
...
- kernel: 4.4.0-24.43-generic
  running: true
  livepatch:
    state: applied
    version: "13.3"
    fixes: ""


Anyone know where I go to see what version "13.3" means?    Is this version number per kernel specific?
Thanks.

---

### Post by deadflowr on 2016-10-21
Patched:
see
[https://packetstormsecurity.com/files/139277/Kernel-Live-Patch-Security-Notice-LSN-0012-1.html]("https://packetstormsecurity.com/files/139277/Kernel-Live-Patch-Security-Notice-LSN-0012-1.html")
Oddly, though the security notice comes through the normal ubuntu security notice mailing list (got it yesterday), but since it's not a [USN]("https://www.ubuntu.com/usn/") notice but rather a LSN notice it isn't showing on the USN homepage.
13.3 version is what you want, though.

---

### Post by wrighrc on 2016-10-21
Thanks.    I suppose the answer is to look for the LSN in the security announce list.   I wonder if there's a detailed change log somewhere.
 [https://lists.ubuntu.com/archives/ubuntu-security-announce/2016-October/003602.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2016-October/003602.html)

---

