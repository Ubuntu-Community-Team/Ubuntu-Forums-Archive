---
title: "Drives not listed in /dev/disk/by-uuid/"
date: 2014-04-24
forum: General Help
---

### Post by Moptop650 on 2014-04-24
Hi all,

I have 5 drives attached to my system. One boot drive with a single ext4 partition, /dev/vda and /dev/vda1. This is listed as /dev/disk/by-uuid/58df4ccc-195b-42ab-a557-93e34c06e6d8.

The other 4 drives have a single, unformatted partition. These 4 are listed under /dev/disk/by-partuuid/.

My question is - why are the additional 4 drives not listed in /dev/disk/by-uuid/ ? Before I added a gpt label and added partitions they were not listed, either. I asked about this in #ubuntu and it was mentioned that ubuntu should automatically list all disks in /dev/disk/by-uuid/.

---

### Post by deadflowr on 2014-04-24
I would think it is because they were unformatted.

---

### Post by jamesisin on 2014-04-24
Do they appear if you enter *sudo blkid* in your terminal?

---

### Post by Moptop650 on 2014-04-24
> **deadflowr said:**
> I would think it is because they were unformatted.

Formatting them made them appear.

Thank you!

---

### Post by coldcritter64 on 2014-04-24
> **Moptop650 said:**
> Formatting them made them appear.

Thank you!

Please mark this as solved, using the thread tools drop down menu at the top of your browser page. 
There is a guide linked in my sig, if needed. Cheers.

---

