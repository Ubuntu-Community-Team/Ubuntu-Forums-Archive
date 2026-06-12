---
title: "qparted...."
date: 2007-12-06
forum: General Help
---

### Post by ElEdwards on 2007-12-06
I just used my qparted-livecd to make some changes in partition sizes on my laptop's 40-gig hdd and afterward found some issues I don't know how to resolve.

What I wanted to do: add another partition for WinXP to use.
My layout before making changes:
- C:\ for XP  - 15gig
- Ubuntu /home  - 15gig
- Ubuntu /  - 10gig

What I accomplished:
- C:\ for XP  - 10gig
- **D:\ for XP  - 5gig**
- no changes to the Ubuntu partitions


Here's what I did:
1- booted XP and did a defrag
2- rebooted to XP and did another degrag, just to be sure
3- booted to the qparted-livecd
4- reduced the size of the C:\ XP partition
5- added the D:\partition
6- Exited and rebooted

I rebooted to XP because I knew the first thing it would want to do was check the disk, which it did.  After XP finished the disk check, XP started normally and all was good....or so I thought :( .....

Here's the weird part:
- In Windows Explorer, I have the C: and D: drives and I can also see my two Ubuntu partitions... but I also now have an E: drive and an F: drive.  Both of these are 0-bytes in size and are of the type- "RAW".
They show up in Windows Explorer but NOT in the Drive diagram in Disk Management.  If I click on either one, I get an error dialog that says they aren't available.

I rebooted with the qparted-livecd and these two "extra" drives don't show up there either.

Everything works great in both XP, including the new D: partition, and Ubuntu... but I'd like to get rid of this E: and F: drive.

Has anyone else seen anything like this?
Thanks! :)

---

