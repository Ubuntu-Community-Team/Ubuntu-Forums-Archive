---
title: "Mounted NTFS volume shows no files"
date: 2007-03-04
forum: General Help
---

### Post by wej1971 on 2007-03-04
This is a weird one - I've had an NTFS volume mounted fine over the last couple of weeks, and all of a sudden it's showing no files when I open the volume, despite the fact (as far as I know) I haven't changed anything.

It's mounted using the following command in /etc/fstab: -

/dev/sda1       /media/windows  ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1

Any ideas what could suddenly prevent this working?

---

### Post by caldevil on 2007-03-04
I don't know the cause but I guess your ntfs partition is not mounted right now. You can mount it again using "sudo mount /media/windows" terminal command.

---

