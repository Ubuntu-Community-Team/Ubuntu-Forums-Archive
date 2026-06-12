---
title: "Access downloaded file"
date: 2013-07-17
forum: General Help
---

### Post by SuzuBell on 2013-07-17
I downloaded two tar.gz files from Firefox. I can see them in Firefox Web Browser --> library --> downloads. On the right of each of them, there is an icon of a folder that when I hover over, it says "Open Containing Folder". When I doubleclick on that, it takes me to Home --> Downloads. There is nothing in that file though.

I have little experience with Ubuntu. How can I find where these files are located?

Thanks.

---

### Post by gleedadswell on 2013-07-17
That's very odd.  The steps you describe should have allowed you to get at those files.  Are you certain the download had completed?

If you are certain they completed downloading then try the old fashioned way via the command line:

1. Open a terminal (easiest way is CTRL-ALT-t).

2. do

```
cd Downloads
```

to go into the Downloads directory.

3. do

```
ls -a
```

to view all of the contents of the directory.  Are the files you are looking for in that list?

---

