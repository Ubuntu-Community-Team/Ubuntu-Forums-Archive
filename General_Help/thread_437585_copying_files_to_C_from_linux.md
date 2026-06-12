---
title: "copying files to C:? from linux?"
date: 2007-05-08
forum: General Help
---

### Post by donteatthefish on 2007-05-08
ok heres my problem, turns out i have to copy my D:\wubi\ folder to c:\wubi\ folder, now heres the problem... i cant boot any file system(so i install suse again and use that), and suse mounts the windows partitions(C,D, and M, yes, M) BUT heres the problem C,D, and M are all read only. and well they are only mounted and i cant switch it to write(yes, im loggied in as the root)

i have no flopy and do not wish to boot up in a DOS boot disk(i dont remember commands and its a waste of a cd if i burn dos to a cd)

is there anyway i can fix this?

more info: i got Vista and XP if that matters.(C: and D: are windows(same drive, different partitions) M is extra(separate drive))

---

### Post by jfinkels on 2007-05-08
> **donteatthefish said:**
> ok heres my problem, turns out i have to copy my D:\wubi\ folder to c:\wubi\ folder, now heres the problem... i cant boot any file system(so i install suse again and use that), and suse mounts the windows partitions(C,D, and M, yes, M) BUT heres the problem C,D, and M are all read only. and well they are only mounted and i cant switch it to write(yes, im loggied in as the root)

i have no flopy and do not wish to boot up in a DOS boot disk(i dont remember commands and its a waste of a cd if i burn dos to a cd)

is there anyway i can fix this?

more info: i got Vista and XP if that matters.(C: and D: are windows(same drive, different partitions) M is extra(separate drive))

You might have to install the ntfs-3g drivers to gain read and write access to the NTFS partition if you're booting into a Linux system.

See here for a howto for ntfs-3g: [http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g)

You might be able to do this from the Ubuntu Live CD. I'm not sure though. It's worth a shot.

---

### Post by donteatthefish on 2007-05-08
wow, fast reply, i will try this, thank you, and i know how most forums work, since this is my first post people will flame me.  for you helping me, I BOW DOWN TO YOU.

honestly, thank you.

---

### Post by jfinkels on 2007-05-08
> **donteatthefish said:**
> wow, fast reply, i will try this, thank you, and i know how most forums work, since this is my first post people will flame me.  for you helping me, I BOW DOWN TO YOU.

honestly, thank you.

Hahaha I don't know how they do things over in SuSE world, but here in the Ubuntu forums, we help each other :D

Click the link in my signature to read more about Ubuntu.

---

### Post by donteatthefish on 2007-05-09
wasn't talking about suse forms... so dont think anything bad about them.

---

### Post by jfinkels on 2007-05-09
> **donteatthefish said:**
> wasn't talking about suse forms... so dont think anything bad about them.

I'm just kidding anyway :D Let us know if you need help with anything else.

---

### Post by ago on 2007-05-09
ntfs-3g is already installed in wubi. From add/remove install ntfs configuration tool

---

### Post by donteatthefish on 2007-05-09
if you read my post you would relize that i cant boot into anything but suse. so i cant boot into wubi.

---

### Post by ago on 2007-05-09
You need to use suse to install ntfs-3g then you can follow the instructions on the wubiguide (the good old way...) since they should also apply to suse.

---

