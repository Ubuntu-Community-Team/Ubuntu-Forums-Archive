---
title: "SHA1 checksum different"
date: 2008-04-01
forum: General Help
---

### Post by akks on 2008-04-01
Hi all,
i am a Ubuntu user but m asking this just for help.
A friend of mine downloaded the iso image of Fedora core 8 through a torrent. With it came a file that specified the SHA1 sum of the .iso image. After the download completed,  we calculated the checksum of the .iso image. using the sha1sum command  and compared it with the one in the file. both the checksums were different. So what should we assume? the file was not downloaded completely? or some part is corrupt?

 But we burnt the image on the dvd and tried to boot from the dvd. It booted from the dvd. but we did not install from the dvd. we will be doing that over the weekend. Please can you'll suggest something if anything was wrong?

---

### Post by conscious on 2008-04-01
The mismatch of the checksums means that either some part(s) of the file is corrupt, or some part(s) are missing. Successful boot from DVD means that some part of the file (in the beginning) is correct.

So you will probably run into trouble if you try to install from this DVD (not guaranteed, because corrupted files may be the ones you don't need). I'd recommend you double-checked the checksums, and, if still different, downloaded the iso image again.

---

