---
title: "Software raid1 rebuild"
date: 2006-10-31
forum: General Help
---

### Post by csiemantel on 2006-10-31
I had a software raid1 configured in dapper that I used for backup storage.  My drive with the dapper install died so I put in a new drive and installed Edgy on it.  My question is how do I recover/reinstall/rebuild the array I had configured on Dapper for my new Edgy install?

I know how to create a brand new mirror, but that involves formatting the drives which would lose all my data.

---

### Post by matthewstory on 2006-10-31
[http://xtronics.com/reference/SATA-RAID-debian-for-2.6.html](http://xtronics.com/reference/SATA-RAID-debian-for-2.6.html)

you don't need to upgrade the kernel, just use the image you have.  This howto basically goes into detail about how to create a degraded raid and then add devices to it.  It works on Debian, and should work on Ubuntu as well.

---

### Post by matthewstory on 2006-10-31
one more thing, he uses wajig in his how to, no need for that, use aptitude instead.

---

