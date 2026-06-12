---
title: "[SOLVED] what can I use to do make new partitions?"
date: 2008-04-11
forum: General Help
---

### Post by tropdoug on 2008-04-11
Hi guys I have been using gutsy gibbon for a few weeks now, and getting to really like it. I want to repartition my ntfs windows drive so that I can store linux docs and music etc on it, as I eventually want to destroy all traces of windows, (that will be a party!)

So I have two HD's, both 80gb. The first is entirely windows XP, the second is entirely Ubuntu. What I am thinking is partitioning the windows one so that I can free up another 50gb as ext3 for sole use of ubuntu. This would give me enough space to transfer all my files from an external 300gb drive to this new partition, and then re format the external drive as ext3 for backup purposes. As I am starting into large scale public presentation work, I have a need for a large capacity drive to store slide and video presentations. 

I am not sure what programs might be able to do this, any ideas? 

Thanks

---

### Post by iandotcom on 2008-04-11
Use gparted..

You'll need to boot from a live cd, and its found in System > Administration > Partition Editor. From there, you can create, resize and delete partitions on attached drives.

Hope this helps,

Ian =)

---

