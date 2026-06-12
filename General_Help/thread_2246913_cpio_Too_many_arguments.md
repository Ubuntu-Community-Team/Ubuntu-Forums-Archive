---
title: "cpio: Too many arguments"
date: 2014-10-04
forum: General Help
---

### Post by O9aIevckc0 on 2014-10-04
[FONT=arial]   	 	 	 	[/FONT][FONT=arial]   [/FONT][FONT=arial]I have been trying for awhile to get the --append or -A option to work but it always fails with cpio: Too many arguments  I have been googling and looking at man pages to no avail and was hoping someone could show me some usage examples  e.g.   ls | cpio -Aov /home/test/test.cpio  thanks in advance  [/FONT] [FONT=arial]  [/FONT]

---

### Post by steeldriver on 2014-10-04
Can you post the complete command you are using please? "too many arguments" usually means too many *filename* arguments (i.e. exceeding the maximum length on the command line) e.g. when you're using shell globs (wildcards) to copy multiple files - depending what you're trying to do, you may be able to work around the limitation using a loop or xargs

---

### Post by O9aIevckc0 on 2014-10-04
updated post

---

### Post by O9aIevckc0 on 2014-10-05
got it working  it should be used like this it seems

   ls | cpio -Aov -F */home/test/test.cpio*   

problem solved

---

