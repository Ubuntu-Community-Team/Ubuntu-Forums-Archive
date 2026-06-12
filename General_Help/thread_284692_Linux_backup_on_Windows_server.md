---
title: "Linux backup on Windows server"
date: 2006-10-26
forum: General Help
---

### Post by jlmb on 2006-10-26
Hi, 
I need to backup, actually just mirror, my entire ~ directory on a Windows server (NTFS) mounted smb share. Obviously, rsync and similar programs can't store permissions on this ntfs partition so it's discarded as an option. I don't want to build a huge tar nor lots of small ones.

I remember reading about a program similar to rsync that stored all the permissions on a file...I've been searching for it but I just can't find it.

Anyways, I'm open to suggestions. 


thanks in advance.

---

### Post by dcstar on 2006-10-26
> **jlmb said:**
> Hi, 
I need to backup, actually just mirror, my entire ~ directory on a Windows server (NTFS) mounted smb share. Obviously, rsync and similar programs can't store permissions on this ntfs partition so it's discarded as an option. I don't want to build a huge tar nor lots of small ones.

I remember reading about a program similar to rsync that stored all the permissions on a file...I've been searching for it but I just can't find it.

Anyways, I'm open to suggestions. 


thanks in advance.

Be warned that some "legal" Linux file names can cause big problems on a Windows file system if you just do a straight copy.

I once made the mistake of copying some files which had special "reserved" Windows character strings which took a long time to clean up.

---

