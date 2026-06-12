---
title: "file overwritten on ext4"
date: 2013-02-06
forum: General Help
---

### Post by popperoga on 2013-02-06
Hello, I start a new thread already knowing the solution, hoping that it will help someone having a similar problem.

I have overwritten a file with an empty one and managed to recover it with the following steps (use a terminal to carry out these operations):
[LIST=1]
[*]Do not remove the file overwritten. Just turn off the computer.
[*]Boot the computer with a live distribution. Once you have an operating linux OS, install "extundelete" (if not already present in your distribution).
[*]As root ```
sudo su
``` mount in a temporary directory the partition containing the file to be recovered, e.g.```
mkdir ~/tmp
mount /dev/sda1 ~/tmp
```
[*]Remove the overwritten file, then unmount the partition.
[*]Connect an external drive and navigate to it.
[*]now you can recover the file, e.g. ```
extundelete /dev/sda1  --restore-file /path/to/file
``` [COLOR="Red"]Note that /path/to/file is the original path of the file in the /dev/sda1 partition![/COLOR]
[/LIST]

That's it! Hope you will succeed :KS

---

