---
title: "mdadm and lvm questions"
date: 2008-06-29
forum: General Help
---

### Post by headlessb on 2008-06-29
Hi, I have a question about mdadm and an lvm setup. Here's how I've setup my system. This is only for storage outside of my main drive system. I've got 4 drives right now, each 1T in size and I've got two mirrored raids going. So it's as if I only have two drives instead of 4. Then on top of that, I have LVM being run to make my two drives seem as one. Now here's where the question comes in. What I'm wanting to do is to remove two of the four drives(the drives that are being mirrored to....not the main drives) and replace them with two other Terabyte drives so I can have a backup of my data on an off site location. My only concern is being able to access the data if something happens. I think mdadm will automatically check for raided drives, so I don't have a problem there, I just want to know how I can remove the raid mirrors from the system yet keep the mdadm mirrors intact. Would I have to simulate a fail in mdadm? Also, when it pertains to LVM, how would I go about accessing the data? Does anyone know? I'm going to continue to check the tuts on this. If anyone has any knowledge that could be helpful, let me know. Thanks a bunch!

---

