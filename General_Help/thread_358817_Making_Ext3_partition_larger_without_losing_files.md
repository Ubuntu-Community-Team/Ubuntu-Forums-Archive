---
title: "Making Ext3 partition larger without losing files"
date: 2007-02-11
forum: General Help
---

### Post by Fisherofman on 2007-02-11
I'm dual-booting Ubuntu and Windows XP
I have 215 GB for Windows-NTFS
13 GB for Ubuntu-Ext3
and 40 GB of Unallocated to add to Ubuntu

Would it be easier to add the 40 GB Unallocated or turn it into a blank Ext3 first?

Can you tell me how to do this?

I have Qtpart, Gparted, and a Gparted Live CD (On Ubuntu)
and Acronis Disk Director Suite and Partition Magic 8.0 (On Windows)

Thank you. I've looked at the Howto Forge tutorial but I didn't really understand.
I'm really new to Ubuntu.

Thank you.

---

### Post by meng on 2007-02-11
I would recommend the Gparted LiveCD.
You can use it to resize your partition, which is pretty safe (but backup of critical data should be done anyway).
Otherwise, think about a separate home partition, this is a great opportunity!
[www.psychocats.net/ubuntu/separatehome](www.psychocats.net/ubuntu/separatehome)

---

### Post by Fisherofman on 2007-02-11
This worked great, thank you!

---

