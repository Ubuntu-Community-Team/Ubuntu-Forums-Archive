---
title: "Adding drives to Raid 5"
date: 2006-10-09
forum: General Help
---

### Post by pwrstick on 2006-10-09
Hello,

I'll be setting up a Raid in the future using mdadm and a spare linux box. Expanding storage would be nice, and I'm wondering if anyone knows if its possible to set up a raid that you can simply add a drive to after installing it, so as I buy more hds I can just plug them in.

Thanks

---

### Post by pwrstick on 2007-01-20
In case anyone else finds this thread:  it's not possible to add drives to a MDADM RAID apparently, but supposedly Raidtools can do it (haven't tried it myself).  The documentation for MDADM does say that you can replace the drives in your RAID with larger drives, and once they're all bigger drives you can *grow into* those drives.  In other words if you wanted more space you could replace your 200GB drives with 500GB drives, and then expand into the extra 300GB of space on each drive.

---

