---
title: "Problem with backup file."
date: 2015-07-13
forum: General Help
---

### Post by dtree46 on 2015-07-13
OS is Ubuntu 15.04.
I made mistakes with my backup file and do not know how to correct them.
Attached is how the files look.
I wanted to make them unreadable.
Now, they can not even be opened.

Any help appreciated.
dlw

Correction: These are directories, not files.

---

### Post by deadflowr on 2015-07-13
Perhaps some history on what method of backing up and (I'm guessing) what method for encryption(?) you tried to use.
(or whatever method you used to try to make them unreadable)

---

### Post by dtree46 on 2015-07-13
Thanks for replying.

Backing up was simple copy to an external 250gb hard drive.
I changed to 'read only' in permissions for both owner and group.
After that, I'm not sure.
I did it a few days ago and just found out there was a problem this morning.

---

### Post by papibe on 2015-07-13
Hi dtree46.

Is the drive formatted in a Linux filesystem? Is is an NTFS drive?

Regards.

---

### Post by dtree46 on 2015-07-13
Linux ext4

---

### Post by papibe on 2015-07-13
Thanks.

It may be a problem with the directory where the file is. Go one level up, and make sure the directory where the file is have similar to this:
```
Owner: Me
Access: Create and delete files
Group access: access files
Others access: access files

```
Let us know how that goes.
Regards.

---

### Post by dtree46 on 2015-07-13
That was it.
Thank you... Thank you... Thank you.

dlw

---

