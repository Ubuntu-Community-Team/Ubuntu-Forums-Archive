---
title: "Setting up RAID 1 Boot drive after install"
date: 2006-10-19
forum: General Help
---

### Post by SuperJason on 2006-10-19
I have a working Ubuntu Server install on my server.  I have 4 drives, 2x160GB and 2x200GB.  I set up the 200GB drives in a RAID 1 configuration, and it works beautifully.

I have Ubuntu installed on one of the 160GB drives, and the other is unused.  I want to have some redundancy, so I would ideally like to set up the 160GB drives in a RAID 1 array.  Is there a good way after the fact?  I know I can set up a broken array, and possibly boot off of it, but I don't know how to copy the 160GB drive (the boot drive) to the 160GB array.  Is there a tool that can make an exact online copy of the entire drive, including all of the boot information?

Or is there a way to just mirror the first drive on the second, so that if the first fails, I can just replace it with the second?

Thanks!

---

