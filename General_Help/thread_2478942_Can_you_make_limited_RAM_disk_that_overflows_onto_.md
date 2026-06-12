---
title: "Can you make limited RAM disk that overflows onto the hard drive?"
date: 2022-09-09
forum: General Help
---

### Post by Paddy Landau on 2022-09-09
I'm thinking of doing a little something for efficiency, where I have a small amount of data being written and read a lot during a task. So, lots of I/O, but the total amount of data is small.

Is it possible to create a virtual disk that exists on both RAM and the hard drive, where the RAM is prioritised?

Let me explain by an example:

[LIST]
[*]For efficiency, I want to create a virtual RAM disk of 0.5 Gb. That's easy enough to do with tmpfs.
[*]But, there is a risk that occasionally 0.5 Gb won't suffice, and the data will exceed this limit.
[*]In that case, I don't want the task to fail, but instead let the virtual RAM disk overflow onto the hard drive, so the RAM holds 0.5 Gb and the hard drive holds the excess.
[*]Obviously, on a reboot or power failure, all data in the virtual disk would be lost. That is acceptable.
[/LIST]
Knowing Linux, this would be possible, but is it reasonably easy to do? Does a utility that supports this already exist? My google-fu isn't managing to find an answer.

---

### Post by TheFu on 2022-09-09
ZFS has the ability to define a disk cache - make that on NVMe hardware and let slower storage be where the data really resides.

Back in the 1990s, the company where I worked had an n-tier application.  To improve performance, we'd have the DBA pin the DB into RAM at startup, since nearly all access was reads.  The RAM use was read-only. Writes still had to go to disk.  I'm not a DBA, so it was only for very high-end clients where we did this. I don't know the specific details.

These days, I'd use ZFS.

---

### Post by HermanAB on 2022-09-09
All decent file systems have a cache.  The ext4 default cache write time is 5 seconds, but it can be adjusted up to hundreds of years if you so wish.  My favorite file system is XFS though.

---

### Post by Paddy Landau on 2022-09-09
> **TheFu said:**
> ZFS…
If I understand you correctly, you are recommending that I format my drive as ZFS, right? At the moment, it's ext4.
> **HermanAB said:**
> All decent file systems have a cache.
This is true.
> **HermanAB said:**
> The ext4 default cache write time is 5 seconds, but it can be adjusted up to hundreds of years if you so wish.  My favorite file system is XFS though.
Thanks.

---

### Post by TheFu on 2022-09-09
> **Paddy Landau said:**
> If I understand you correctly, you are recommending that I format my drive as ZFS, right? At the moment, it's ext4.

This is true.

Thanks.

Only the data partition. Then you'll want to tell ZFS which devices to use for cache.
I would not recommend using ZFS for the OS, just for data.

---

### Post by HermanAB on 2022-09-09
BTW, make sure your UPS works reliably before you increase cache use.

---

### Post by dragonfly41 on 2022-09-09
As part of my development plans I have started an account with Jelastic.
The nice part is that you can configure Pay As You Go.
That is, the Ubuntu 20.04 cloudlet with whatever RAM you choose can be shut down.
I have spent very little in setting up PaaS Ubuntu 20.04 cloudlet for experiments. I plan to leverage the CLI to supplement its dashboard.
My broad idea is that you open an account, and setup a script to startup PaaS, push data from desktop via SSH or FileZilla to the service (with extended RAM setup) and then pull down the results to your desktop and finally shut down your cloudlet.
Basically an external work horse at very little cost. Look at Change Network Topology after you create a Ubuntu environment.

---

### Post by HermanAB on 2022-09-10
Here is something on adjusting the ext4 cache: [https://superuser.com/questions/479379/how-long-can-file-system-writes-be-cached-with-ext4#479384](https://superuser.com/questions/479379/how-long-can-file-system-writes-be-cached-with-ext4#479384)

---

### Post by Paddy Landau on 2022-09-10
Thank you, all, for your extra details!

---

