---
title: "replacing a file with a copy"
date: 2019-10-14
forum: General Help
---

### Post by Skaperen on 2019-10-14
i wrote a script that replaces a file with a copy made by first making a temporary name in the target's parent directory and copying that source to the temporary file with that name.  then it forcibly moves the temporary file to the target name.  can any options or option combinations in the [COLOR=#0000cd][FONT=courier new]**cp**[/FONT][/COLOR] command do this?  i know [COLOR=#0000cd][FONT=courier new]**rsync**[/FONT][/COLOR] does this by default.

---

### Post by HermanAB on 2019-10-15
Honestly, I cannot comprehend what exactly you want to do, but do read 'man cp', since it has several advanced features that were added relatively recently, in the last 20 odd years, which may be able to do what you want.

---

### Post by Skaperen on 2019-10-15
i did read the man page.  i saw 3 advanced modes of copy, but was unable to determine if any of them do what i wanted.  what i formerly would do in C i now days do in Python3.  with a few exceptions, it can do what i typically need to do.

---

### Post by Skaperen on 2019-10-15
i want to avoid copying by trying to open the existing file and truncating it first, as cp does, at least by default.  there are 2 problems.  i typically keep a lot of my files in permission mode "-r--r--r" to prevent accidental writing and this command works around that.  the other is there is a short period of time while the file is empty or short which is avoided by this method.

---

