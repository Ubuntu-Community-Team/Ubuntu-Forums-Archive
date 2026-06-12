---
title: "File Server filesystem / LVM / ZFS"
date: 2014-02-04
forum: General Help
---

### Post by william15 on 2014-02-04
I am about to port my file server from Windows 7 to Ubuntu (probably Gnome DE, have been using Xubuntu for about 1.5 years) and I have hit a cross roads at how to manage the storage.

Just to be difficult, I have an 80gb SSD that will be used for /home and /, 1x 2TB WD green, 1x 3TB WD red and 2x 1.5TB WD greens.

The file server will serve as a media center as well as serving the media files to 3 different users (home server) as well as regular computer use.

In total I have about 2TB in total of files.

All I really want is one large pool of storage that backs itself up and perhaps offers some kind of redundancy.

I have been looking at ZFS, LVM (perhaps with EXT4) and perhaps JFS or maybe even a RAID array but I just need some advice over what can be done.

I was wondering if I could use the 2 1.5TB to create a 3TB logical volume which could then be implemented in a RAID 1 type system with the 3TB WD red and perhaps partition the 2TB into 2x 1TB to give me a total of 4TB usuable storage with a 4TB mirror?

Any advice would be very well received and greatly appreciated. Please and thank you!

---

### Post by william15 on 2014-02-04
I think the ideal solution is to create two logical volumes out of the 2 1.5TB drives plus half of the 2TB giving me a 4TB logical volume and then creating another 4TB volume out of the 3TB red and remaining 1TB from the 2TB green, and then just creating a mirror.


Can this be done? and if so which is the ideal filesystem?

---

