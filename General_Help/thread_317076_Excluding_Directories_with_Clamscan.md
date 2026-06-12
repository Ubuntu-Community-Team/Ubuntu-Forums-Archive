---
title: "Excluding Directories with Clamscan"
date: 2006-12-11
forum: General Help
---

### Post by SuperMike on 2006-12-11
What's the proper way to do regex paths for --exclude-dir switch with Clamscan?

Here's some choices (minus other switches in the command line, of course):

clamscan --exclude-dir='/proc|/sys|/dev|/mnt'

clamscan --exclude-dir=/proc|/sys|/dev|/mnt

clamscan --exclude-dir=\/proc\|\/sys\|\/dev\|\/mnt

clamscan --exclude-dir=/\/proc\|\/sys\|\/dev\|\/mnt/

clamscan --exclude-dir=proc|sys|dev|mnt

etc. (I'm sure you can come up with more options.)

Unfortunately, the Clam AV docs on the web don't make sense of this, nor does the man file, nor do any forum postings searched through Google.

](*,)

---

### Post by SuperMike on 2006-12-11
After some experimentation, I found it was:

clamscan --exclude-dir=/proc|/sys|/dev|/mnt

---

