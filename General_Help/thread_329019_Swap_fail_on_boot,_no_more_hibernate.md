---
title: "Swap fail on boot, no more hibernate"
date: 2006-12-31
forum: General Help
---

### Post by Jeff Gavett on 2006-12-31
Resolved thanks to [https://launchpad.net/distros/ubuntu/+bug/66637](https://launchpad.net/distros/ubuntu/+bug/66637)

I've recently realized, only through hibernate stopping working, and through when ubuntu does a scan on boot, that my swap file fails.

I'm kind of panicked about screwing up my hard drive, so I'll give you some info that I've noticed could be helpful to the experts in letting me know what's up. The system was originally Dapper, then upgraded to Edgy.

free -m gives me
```

                    total       used       free     shared    buffers     cached
Mem:          1011        987         23          0        616        200
-/+ buffers/cache:     171        840
Swap:            0          0          0

```

fdisk -l gives me
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       11870    54388057+  83  Linux
/dev/sda3           11871       12161     2337457+   5  Extended
/dev/sda5           11871       12161     2337426   82  Linux swap / Solaris

```

Thanks!

---

### Post by kolesarm on 2007-02-10
Yes, I had the same problem - swap failed to activate after upgrade from Dapper to Edgy - Didn't notice for months:)

Thanks for the link, it seems to work now

---

