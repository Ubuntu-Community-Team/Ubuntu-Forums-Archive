---
title: "Messed up my home partition - Gparted: &quot;Unknown&quot; filesystem - Can I recover files?"
date: 2013-04-04
forum: General Help
---

### Post by NicoleCtrl on 2013-04-04
I was resizing my home partition in Gparted (something I had no idea would take over an hour) and my netbook overheated, which it tends to do, and turned off mid-operation. When I turned it back on later the partition was not accessible and Gparted lists it as "Unknown" filesystem. I know it is an ext4 filesystem but I am not able to access my files or fix the problem. If I could just save the files to a USB flash drive I wouldn't mind formatting the whole disk and starting over. Is there a way to do this? I have Parted Magic on a USB drive and was looking around for a tool to help me but so far I'm unsure of what to try next.

Any help greatly appreciated!

---

### Post by ibjsb4 on 2013-04-04
You can try TestDisk

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Irihapeti on 2013-04-04
+1

TestDisk is already installed in Parted Magic.

---

### Post by NicoleCtrl on 2013-04-04
Hmm, thank you. I'm having trouble figuring out how to use TestDisk to fix this. There is a way to set the filesystem type for partitions but I don't see "ext4" anywhere in the list, and even if the option exists somewhere I'm unsure if it would be wise to try it without having a reasonable expectation in advance that it wouldn't further damage things. Does anyone know what I should try specifically and if it has a reasonable chance of working?

---

### Post by NicoleCtrl on 2013-04-06
^ Bump. Anyone, please?

---

### Post by NicoleCtrl on 2013-04-08
^ Bump

---

### Post by ibjsb4 on 2013-04-08
My own experience with testdisk was quite painless.  The few (3 times) I use it, it was just a matter of booting it up.  And testdisk then spit out what it seen and what it could save, all automatic for me.  I know of manual restore methods with testdisk only because I have seen them discussed in the forum, but someone else will have to inform you about this.

I am just relaying my experience to you, in hope it can help you with a more informed decision.  Good luck

---

