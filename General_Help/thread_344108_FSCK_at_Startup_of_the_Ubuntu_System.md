---
title: "FSCK at Startup of the Ubuntu System"
date: 2007-01-22
forum: General Help
---

### Post by RagonichaFulva on 2007-01-22
I have changed from Dapper Drake to Edgy Eft (clean installation, not upgrading) and every time I load Ubuntu Linux in my laptop it as to test my disks with fsck. I see no errors in the diagnostics. Actually, I hae instaled the same version in my workstation and I haven't this problem.

Can anyone tell me why is this happening? My systems takes very long to load due to this prcess that takes place every time I start up my computer.

---

### Post by evilghost on 2007-01-22
```
tune2fs -c 30 <drive>
``` will set the check count.

---

### Post by RagonichaFulva on 2007-01-23
Ok, I have read the manual of tune2fs function and I reckon what youare telling me to do is to modify the scan so it only takes place every 30 mounts of the partitionn. That's how it was configured in my Dapper. Do you mean the configuration changed when I installed from anew Edgy Eft? How is this possible? Any idea?

Oh! and thanks for your help!

---

