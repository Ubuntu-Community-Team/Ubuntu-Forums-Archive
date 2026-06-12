---
title: "Fatal error when accessing man pages"
date: 2008-02-24
forum: General Help
---

### Post by RayDeCampo on 2008-02-24
I recently installed 7.10 and I am getting the following error when trying to run man:

troff: fatal error: can't open ` -mandoc': No such file or directory

I'd appreciate any pointers.

Thanks,
Ray

---

### Post by Bubba64 on 2008-02-24
I'm  personally not familiar with this application, but I Goggled mandoc and came across this forum link that has another link within it that seemed to answer another persons similar problems hope this helps. If you have already looked at this info sorry to have wasted your time
[http://ubuntuforums.org/showthread.php?t=206214](http://ubuntuforums.org/showthread.php?t=206214)

---

### Post by RayDeCampo on 2008-02-24
OK, I discovered the issue.  I had set the IFS environment variable in order to deal with some files with spaces in their names and included only the newline character.  This must have caused issues with the commands executed by man.  Sorry for the bother.

---

