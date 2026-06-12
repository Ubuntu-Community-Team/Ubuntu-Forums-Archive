---
title: "Error executing canonical-livepatch"
date: 2016-11-07
forum: General Help
---

### Post by mrfort on 2016-11-07
Having the same issue. Ubuntu Mate 16.10 with everything updated.

sudo apt-get install snapd  <---installed OK

sudo snap install canonical-livepatch  <--- Installed OK   [canonical-livepatch (stable) 6 from 'canonical' installed]

sudo canonical-livepatch enable (and the token I downloaded)

Error executing enable?auth-token=(token I downloaded), Connection to the daemon failed: Put [http://127.0.0.1/enable?auth-token=(token](http://127.0.0.1/enable?auth-token=(token) I downloaded): dial unix /var/snap/canonical-livepatch/17/livepatchd-priv.sock: connect: no such file or directory.

I had exactly the same error in 16.04. Is it something the Mate team has wrong or is it more wide spread? All my Ubuntu Mate have the exact same issue.

---

### Post by howefield on 2016-11-07
Post moved to own thread as nothing to do with the thread it was posted in.

Some one else will most likely chime in with some help but as I understand it, it only works with the 16.04 kernels.. not the 16.10 release.

---

### Post by #&amp;thj^% on 2016-11-07
> **howefield said:**
> Post moved to own thread as nothing to do with the thread it was posted in.

Some one else will most likely chime in with some help _but as I understand it, it only works with the 16.04 kernels_.. not the 16.10 release.

+1:)  This is meant for **Ubuntu** [B]16.04 LTS and suppoted kernels.
[/B]For more Information see this: [https://ubuntuforums.org/showthread.php?t=2340494&p=13564000#post13564000](https://ubuntuforums.org/showthread.php?t=2340494&p=13564000#post13564000)

---

