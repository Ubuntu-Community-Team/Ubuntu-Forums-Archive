---
title: "Deleting locked files"
date: 2023-12-02
forum: General Help
---

### Post by trash1464 on 2023-12-02
I am trying to clean up old backup files on my FreeNAS server, there are thousands of them. Every file displays a lock icon overlaid on the file name therefore cannot be deleted. I have tried chown, chmod, sudo nothing works. Can you help?

---

### Post by trash1464 on 2023-12-02
Looks like problem fixed. The files in question were from a Windows backup and Ubuntu cannot manage them. The files were deleted successfully from a windows console.

---

### Post by yancek on 2023-12-03
Linux permissions are not understood or used on windows filesystems so chown and chmod will not work.  Is  windows installed on the server computer?  A possible likely scenario is that the windows system is in an unsafe state, hibernation, which is the default with newer windows versions.  Linux will not mount those partitions as there is a high likelihood of data loss while a system is hibernated.   If this is not the situation, anything else would involve more guessing.   Best to do things like that from windows.

---

### Post by trash1464 on 2023-12-03
You are correct about windows and I was able to delete 99.9% of those old backup files from another windows console. Apparently windows applies its own flavor of permissions when writing to the FreeNAS server which BTW runs on FreeBSD. That would have been useful in the original post had I included it, duh! Re. your server question, I do not and will not have a windows server, been there done that, never again! Thank you for your time!!

---

