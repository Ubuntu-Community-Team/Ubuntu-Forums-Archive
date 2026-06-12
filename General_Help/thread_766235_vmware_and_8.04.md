---
title: "vmware and 8.04"
date: 2008-04-25
forum: General Help
---

### Post by mac_john on 2008-04-25
I'm unable to install **vmware** in Hardy Heron. When compilling it gives me a lot of errors...

---

### Post by StOoZ on 2008-04-25
try before installing:
> sudo apt-get update
> sudo apt-get upgrade

> sudo apt-get install build-essential

---

### Post by Saya on 2008-04-25
I believe your issue is that 8.04 has a new kernel which isn't compatible with VMware's modules. Sorry, don't know of a solution yet but there might be one.

---

### Post by StOoZ on 2008-04-25
but, the latest version of vmware server, released after the release of 8.04 kernel. 8.04 is not equipped with the latest linux kernel.

---

### Post by Saya on 2008-04-25
> **StOoZ said:**
> but, the latest version of vmware server, released after the release of 8.04 kernel. 8.04 is not equipped with the latest linux kernel.
Since he's compiling it I assumed that he might have an outdated version.

---

### Post by StOoZ on 2008-04-25
well, so he should download the latest version

---

### Post by anaconda on 2008-04-25
This thread helped me to get vmware working in hardy.. (about a month ago) 
[http://ubuntuforums.org/showthread.php?t=613976](http://ubuntuforums.org/showthread.php?t=613976)

you just need the correct any-any-update..

---

