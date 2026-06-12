---
title: "Help with updates Ubuntu 14.04"
date: 2014-06-16
forum: General Help
---

### Post by rickm1945 on 2014-06-16
I have a inverted red triangle at the top of my screen. I clicked it and attempted to install and download updates. I got this error: ```
W:Failed to fetch http://ppa.launchpad.net/mariospr/mariospr-ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/mariospr/mariospr-ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
``` How to I resolve this?

---

### Post by Bucky Ball on 2014-06-16
Open your Software Updater and click 'Setting' in the bottom left corner. In the 'Other Software' tab look for the PPA lines containing 'mariospr' or 'mariospr-ppa'. Untick or delete them.

The server the PPA is on may be down or it may be redundant and you've forgetten you added it.

---

### Post by deadflowr on 2014-06-16
Open Software and Updates
go to other software and  disable(uncheck) that repo.
I don't see any packages, currently, in that repo
(for any version)

Edit: partial ninja'd
(both methods will get you to the same window (software sources))

---

### Post by rickm1945 on 2014-06-16
Thank you Bucky Ball, the problem is fixed.

---

