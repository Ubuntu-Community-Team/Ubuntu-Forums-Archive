---
title: "file visible on Nautilius but invisible in Terminal"
date: 2018-04-02
forum: General Help
---

### Post by saurian2 on 2018-04-02
Hello everyone,

I currently have an unusual experience. There are some files created by a software I'm working on in the tmp folder. Nautilius can see these files but in Terminal these files are not visible, nor available. I tried ll, ls, ll -a, ls -a, find and tried this with sudo user but files are not visible or available (I actually tried a rm command just in case the files are only hidden). These files seem to have 0 bytes. Anyone has any idea why is this happening?

I'm using Ubuntu 16.04 LTS.

Best regards,
Sorin

---

### Post by The Cog on 2018-04-02
Hmm, interesting. Do the files have anything unusual in their names? I have always thought that 'ls -al' is a good way to see **all** files. 

Is it possible that nautilus is misleading you - perhaps the files have been deleted and nautilus is showing the state from a little while ago? Are they still there if you choose to refresh the view in nautilus?

---

### Post by saurian2 on 2018-04-02
I closed and reopened Nautilus and the files are still there (I don't really know any other way to refresh nautilus). More than that, when a I run a certain piece of software new files are created. Files are named something like ex_ti***.tmp, where *** represents some random numeric characters. I don't know if it matters but these files have 0 bytes as size.

---

### Post by The Cog on 2018-04-02
I really have no ideas. Perhaps have a close look at the file properties in Nautilus to see if anything looks odd there, but I have a feeling you won't see anything unusual. Being 0 bytes doesn't mean that much.

If I have a good idea I'll come back, but I think I am just going to keep watching the thread hoping to learn something. Sorry.

---

