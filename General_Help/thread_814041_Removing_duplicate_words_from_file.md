---
title: "Removing duplicate words from file?"
date: 2008-05-31
forum: General Help
---

### Post by razta on 2008-05-31
Hello,
I want to merge file1 with file2, remove and duplicate words and then make file3 with the contents of file1 and file2 without the duplicates.

ie.

File1:
A
B
C
D

File2:
A
B
E
F

File3:
A
B
C
D
E
F

I know you can merge files with the "paste" command, however dont know how to remove the duplicates.

Any help apretiated, thanks in advance.

---

### Post by latna on 2008-05-31
Try this:

```
cat file1 file2 | sort | uniq
```

This will print to the screen. When you're satisfied with the output, you can run this to send the output to file3:

```
cat file1 file2 | sort | uniq > file3
```

---

### Post by HalPomeranz on 2008-05-31
Or just:

```

sort -u file1 file2 >file3

```

---

