---
title: "permission denied despite file is  -rwxrwxrwx."
date: 2016-03-28
forum: General Help
---

### Post by dieter-erich on 2016-03-28
Hi,
    I wrote a short bash script and wanted to make it executable with "chmod a+x filename". However, whatever I do, even when trying to run it as root I get "permission denied". The file attributes are  -rwxrwxwxr. So what is wrong? I also tried to change the directory's permissions via "chmod -R a+xwr directory, but no avail. What is wrong?
Thanks, D-E

---

### Post by spjackson on 2016-03-28
It sounds like the script is on a partition or device that is mounted with the noexec option. See for example [http://ubuntuforums.org/showthread.php?t=2214490](http://ubuntuforums.org/showthread.php?t=2214490) for some discussion of this.

---

### Post by dieter-erich on 2016-03-29
Thanks, that was it!

---

