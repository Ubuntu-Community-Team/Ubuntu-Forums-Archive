---
title: "Cannot Delete and my drive is full!"
date: 2007-04-08
forum: General Help
---

### Post by William Lethal on 2007-04-08
Hi

I was using reconstructor to make a live cd and my harddrive became full because it was copying off a disc. This caused reconstuctor to stop and I had to close it. When I went into file manager and tried to delete the 2 gb of files, it said "Access Denied" and for another it said "Read-only file system."

How can I delete these files?

Thanks
William:KS

---

### Post by hardyn on 2007-04-08
they likely belong to root...

sooo... either navigate to them using the CLI (command line interface) and use sudo rm <filename>, or sudo rm -r <directory>
or using CLI 'gksudo nautilus' and nativate to them graphically and delete them.

good luck.

---

