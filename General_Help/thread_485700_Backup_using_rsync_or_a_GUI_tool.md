---
title: "Backup using rsync or a GUI tool"
date: 2007-06-27
forum: General Help
---

### Post by Ozor Mox on 2007-06-27
At the moment I do my backups in a *really* old-fashioned way, by logging changes to a text file and updating the backup on my external hard drive every so often.

Obviously, this sucks, and I'd like to use a tool. I hear rsync is good, but can anyone enlighten me as to what I'd need to enter in to the command line to move all changes from my hard drive to my external hard drive? My guess is something like this...

```
rsync /home/me media/ext1
```

...to copy everything from my home folder to my external drive (which appears as something like ext1 when plugged in I think).

How close am I? Or alternatively, is there a GUI tool I could use?

---

### Post by vanadium on 2007-06-27
You are quite close. You only need to add three options: "-a -v --del"

rsync -av --del /home/me media/ext1

the -v is not essential: tells the program to be more vebose. First run the command without the --del option to test whether all goes well. The --del option will make sure that files in the target that do not anymore exist in the source, are deleted. It is a potentially dangerous option: if you mistakenly swap target and source, and your target is still empty, then all your source files would get deleted.

---

### Post by nick_h on 2007-06-27
The grsync package provides a GUI front-end to rsync.

---

### Post by orb9220 on 2007-06-27
Also you need to exclude any folders that you wish not to backup.

Example: I remapped my ntfs from /media to /orb/Drives/  so they no longer showed on the desktop and forgot about them. You can guess what would happen when I tried to backup. I also had a movies folder where I had about 20 gigs of iso's.

Live and Learn.

---

