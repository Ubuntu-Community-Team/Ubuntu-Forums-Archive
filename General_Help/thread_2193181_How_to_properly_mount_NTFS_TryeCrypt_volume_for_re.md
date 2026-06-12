---
title: "How to properly mount NTFS TryeCrypt volume for read AND write?"
date: 2013-12-11
forum: General Help
---

### Post by gregory12 on 2013-12-11
When I mount it right now I have just write access.
I tried this ntfs config tool from the app centre to give it write, but it seems like it doesn't work for TC volumes?

So, how to make it so Ubuntu can read as well to it?

---

### Post by gregory12 on 2013-12-12
no one?

---

### Post by Cavsfan on 2013-12-12
Myself I do not advise writing from a Linux OS to a NTFS drive period. I had done a bit of that a few years ago and ended up having to re-install windows 7 and I've never had to do that before in my life.
Windows keeps track of what gets written to the hard drive and it doesn't like not being in control. There is a user journal file that gets updated with every change within windows so it does not see updates done outside windows.
It is called **C:\$Extend\$UsnJrnl:$J:$DATA** in WIndows. Not sure if that is all that is affected.

If you do choose to write to/from a windows drive, you are taking chances. That has been my experience. I read from the windows drive and copy files but never do I save a file or update a file from outside of windows.
That's my 2 cents. You can do what you want.

---

