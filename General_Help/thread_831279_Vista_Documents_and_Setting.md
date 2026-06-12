---
title: "Vista Documents and Setting"
date: 2008-06-16
forum: General Help
---

### Post by fcigoi on 2008-06-16
Since I have installed Ubuntu 8.04, when I try to access my documents on the Vista NTFS partition, it all seems fine until I enter the documents and settings directory which appears empty.
Obviously it's not...
Am I the only one having this problem ? Any ideas why it happens ? Any remedies ?

---

### Post by KeSha on 2008-06-16
and at least, from the Windows Vista copy the folders and files from the "documents and settings" to another directory. for example to the D:\ local disc. and they must be shown in linux

---

### Post by fcigoi on 2008-06-16
Ok I can do that no problem. If from Vista I copy the files from Documents and Settings to another directory, then I can go back to Ubuntu and see the files in the new directory. But the same files in Documents and Settings are absolutely invisible from Ubuntu...that's what I don't understand

---

### Post by ad_267 on 2008-06-16
Isn't the "Documents and Settings" directory in Vista now called "Users"? Maybe that's causing some confusion.

---

### Post by Zorael on 2008-06-16
I seem to remember it being "Users", too. And that "Documents and Settings" is now just a symlink towards it.

---

### Post by ad_267 on 2008-06-16
Yup that would explain it then. Maybe Linux doesn't support the new symbolic links in ntfs. So point yourself to "Users," not "Documents and Settings." That's probably just there for backwards compatibility with some software.

---

### Post by cariboo on 2008-06-16
On my vista installation there is absolutely nothing in Documents and Settings, even looking at it from vista. I think it is more cruft left over for backwards compatability.

Jim

---

