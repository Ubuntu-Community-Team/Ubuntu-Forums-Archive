---
title: "ntfs-3g Problems"
date: 2007-05-31
forum: General Help
---

### Post by Valdrone on 2007-05-31
Alright, so I mounted my windows partition with ntfs-3g, and everything worked fine and writable while on Linux.

Then, I booted to windows. A few programs buggered saying weird things about access permissions. Eventually what cued me to frustration was the fact that my SVN wouldn't update because it didn't have permission to access C:\WINNT\Temp\report.tmp. There's nothing about that file in support, or even on the internet!

In fact, C:\WINNT doesn't even exist! I can't even access it by command line. Nor does it exist when I look at it on linux. Now, my first reaction was to look at C:\Windows\Temp instead. But the file wasn't found in there, either!

So, are there any ways to revert changes, or just fix windows permissions that were changed by ntfs-3g?

---

### Post by Valdrone on 2007-05-31
Gah, never mind. It was a serverside problem.

---

