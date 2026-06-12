---
title: "Owner of the file not being displayed properly in LINUX Terminal"
date: 2019-05-18
forum: General Help
---

### Post by takeatoll on 2019-05-18
So here is my problem- I want the terminal to display the user name that created a particular file, so when I traverse all the way to that file and type in the command 'ls -l filename.docx' or even 'ls -la /path/to/file', it shows the output as: **staff 1344 May 18 11:03 (filename).docx. **So I don't understand why does it display 'staff 1344' instead of using my actual user name. How am I supposed to obtain the actual username in this case (provided I logged in from my admin account)? Any help would be really appreciated.

---

### Post by yancek on 2019-05-18
.docx is a Microsoft windows Word document extension.   Are you accessing it on an ntfs filesystem?  I don't use windows but the link below discusses this situation and apparently this has to be changed in your mount options (if you are accessing it on an ntfs partition).  Scroll down the page a bit and there is a brief explanation.

[https://superuser.com/questions/872733/why-does-ms-word-save-docx-and-pdf-files-with-executable-permissions-when-run](https://superuser.com/questions/872733/why-does-ms-word-save-docx-and-pdf-files-with-executable-permissions-when-run)

---

### Post by Impavidus on 2019-05-18
The output of ls -l shows type (as in regularfile, directory, ...), permissions, number of hardlinks, owner, group, size (in bytes), modification time and date, name. So the line of output in your post is incomplete, but it looks like staff is the group to which the file belongs, not the user who owns it.

BTW, 1344 bytes is pretty small for a docx file.

---

### Post by Holger_Gehrke on 2019-05-18
The output of 'ls -l' should have seven columns (permissions, hard link count, owner, group, size, mtime and name), you're only showing us the last four (yes, 'staff' is a predefined group, gid 50; the '1344' should be the file size). If that's all the output you get you have a bigger problem than getting user names instead of 'real' names. When a user is set up he is given a user name which **must** be unique. The 'real' name doesn't need to be (so yes, you can have a dozen users with 'real' name 'John Smith', but their user names have to differ) and is completely voluntary and for informational purposes only. The system actually uses neither name, all users also get a number (id) which is what is used by the system internally.

Holger

---

