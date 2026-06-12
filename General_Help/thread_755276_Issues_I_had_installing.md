---
title: "Issues I had installing"
date: 2008-04-14
forum: General Help
---

### Post by jbmckee on 2008-04-14
I am working with Wubi 8.04 rev 479 and ran into the following issues...

My system uses Raid 1 mirrored drives.  When I install using Wubi, Ubuntu cannot find the boot files when it tries to start.  If I disable the raid array in bios, it works.

Next problem...

I have two partitions, C and D.  Windows boot files are in C.  Data is kept in D.  When setting up using Wubi, I chose Drive D for installation.  However, when I try to start Ubuntu, it dumps me to BusyBox error.  If I change the installation to the C drive, it works fine.

---

### Post by ago on 2008-04-14
Might be that the raid is not supported
See if [https://wiki.ubuntu.com/WubiGuide#head-b53faf3bd2a3da641d3424708bc35406c355dfb1](https://wiki.ubuntu.com/WubiGuide#head-b53faf3bd2a3da641d3424708bc35406c355dfb1) helps with the second issue

---

### Post by jbmckee on 2008-04-14
Am I just stuck about the Raid being unsupported?  Is it Ubuntu that doesn't support it or Wubi?  Can I go ahead and make a new partition?

Is there a listing of what Raid configurations are supported?

(I am only experienced enough here to get myself into trouble. :) )

---

### Post by ago on 2008-04-15
Software raid (aka fakeraid) is not supported in Ubuntu.

---

