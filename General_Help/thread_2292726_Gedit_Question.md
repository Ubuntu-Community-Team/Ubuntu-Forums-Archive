---
title: "Gedit Question"
date: 2015-08-30
forum: General Help
---

### Post by jhboards on 2015-08-30
Running Gedit 3.10.4 on 14.04 LTS. With Gedit running, in the drop down menu "open" here are 3 listings of the same file, "to do". 1 has the file name "to do" followed by a single ~ (Tilde?) another has file name "to do" followed by 2 ~~ Tildes and a 3rd has only the file name "to do" with no "~" appended.

As I understand it, the files with the "~" are back up files that were automatically created by Gedit. I have disabled this feature in Gedit.

My question is: how to I delete the the 2 "~" files in the drop down "open" box and keep them from appearing?

The file path for all three lead to my "to do" desktop short cut. I tried deleting the short cut, but the "~" files still show in the "open" drop down box.

How to I delete these?

---

### Post by kerry_s on 2015-08-31
security & privacy --> files & applications --> clear usage

---

### Post by CantankRus on 2015-08-31
**kerry_s** solution will remove recent files and applications from the dash as well as from "recent:///"

If you don't want this behaviour, you can just remove files in "recent:///" with...
```
echo > ~/.local/share/recently-used.xbel
```

If a recent file no longer exists it won't appear in the dash recent anyway.

---

### Post by jhboards on 2015-08-31
That did it, Thanks.

---

### Post by jhboards on 2015-08-31
> **kerry_s said:**
> security & privacy --> files & applications --> clear usage

Sorry, for go give credit to kerry_s.

---

