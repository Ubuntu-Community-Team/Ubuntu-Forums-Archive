---
title: "MDADM RAID consistency-policy pros cons Help!"
date: 2023-03-17
forum: General Help
---

### Post by libertyspike138 on 2023-03-17
Hello, I have been using ZFS where available for years so I'm not extremely familiar with MDADM but I do have 3 machines using it and have a question regarding it. By default 2 of these machines have a consistency-policy set to resync where the other is set to bitmap. I have read the manpage and see how to change it but I'm wondering what the pros and cons of each are? Thanks!

---

### Post by TheFu on 2023-03-18
Every month, I have mdadm do a consistency check on my RAID1 arrays.  Don't remember where I read that was a best practice, just that it was. /usr/share/mdadm/checkarray is the command.  I don't check what type of policy the array has.

I also run weekly SMART short tests and monthly SMART long tests across all non-laptop disks.  I don't keep anything important on laptops. They are never the "system of record" for anything.

---

