---
title: "BatchFile"
date: 2007-06-16
forum: General Help
---

### Post by The Wisedude on 2007-06-16
Well this is how it goes, On my windows OS, I was coding Java, and, I needed a .bat file to run the actually Java files, So I'm wondering, How would i run a .Bat file in Linux (Ubuntu)

---

### Post by dreadlord_chris on 2007-06-17
> **The Wisedude said:**
> Well this is how it goes, On my windows OS, I was coding Java, and, I needed a .bat file to run the actually Java files, So I'm wondering, How would i run a .Bat file in Linux (Ubuntu)

They are called script files in *nix

Here's a BASH scripting guide:
[http://www.museum.state.il.us/ismdepts/library/linuxguides/abs-guide/](http://www.museum.state.il.us/ismdepts/library/linuxguides/abs-guide/)

---

### Post by Old *ix Geek on 2007-06-17
In *nix they're called shell scripts, and you run them by making them executable.  Unlike windoze there is no concept of file extensions (i.e., .bat, .exe, etc.).  To make a file executable, use **chmod** to alter its permissions.  For example, if you want to make file "javastuff" readable and executable by all users, but only give root write permissions, do this at a prompt: **chmod 755 javastuff**.  Now when you list its permissions you'll see rwxr-xr-x.

---

