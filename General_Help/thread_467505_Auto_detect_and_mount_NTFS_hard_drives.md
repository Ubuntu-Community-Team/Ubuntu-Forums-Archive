---
title: "Auto detect and mount NTFS hard drives"
date: 2007-06-07
forum: General Help
---

### Post by nzgreven on 2007-06-07
I'm trying to create an XUbuntu computer for scanning hard drives out of windows computers with clam antivirus.  Is there any way to get it to automatically detect when a new NTFS formatted hard drive is connected and mount it?

When I run automatix, it mounted the hard drives I had connected at the time, but when I connected a different NTFS drive, it didn't automatically mount it.

---

### Post by cookies on 2007-06-07
If you get ntfs-3g, (if you do, well then I dunno) It allows "Enable Read/Write Support for External and Internal Devices".

So try 

```

sudo apt-get install ntfs-3g

```

Make sure that you have the correct Repository enabled. *I forget which it is*

Then go to Applications > Utilities > NTFS Configuration tool. I think after you enable external/internal, drives, they auto-mount, but I'm not sure.

---

