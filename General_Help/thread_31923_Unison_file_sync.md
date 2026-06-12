---
title: "Unison file sync"
date: 2005-05-05
forum: General Help
---

### Post by markr on 2005-05-05
I am trying to use unison to syncronise my laptop documents with a USB HDD.  The initial sync works okay and all the files are copied to my USB HDD.

However, if I try to run it again (to ensure it is up to date), even though nothing as changed Unison is reporting that 'props' have changed for all files and directories.

I did some research and it appears that it is picking up the time as the change - googling suggested that I put times = true in my .prf file, but this has no affect.

Has anyone use Unison and know how to get around this problem?

Mark.

---

### Post by Alexander Kirillov on 2005-05-05
[QUOTE=markr]I am trying to use unison to syncronise my laptop documents with a USB HDD.  The initial sync works okay and all the files are copied to my USB HDD.

However, if I try to run it again (to ensure it is up to date), even though nothing as changed Unison is reporting that 'props' have changed for all files and directories.

I did some research and it appears that it is picking up the time as the change - googling suggested that I put times = true in my .prf file, but this has no affect.

Has anyone use Unison and know how to get around this problem?

Mark.[/QUOTE]
 What kind of filesystem does your USB HDD uses? If it is vfat (windows), then it has no support for permissions in Linux sense, so permissions may be different for files on you main HD and the USB one.

---

### Post by markr on 2005-05-05
I'm syncing from a vfat partition on my laptop to a vfat partition on my USB HDD.

---

### Post by Alexander Kirillov on 2005-05-05
[QUOTE=markr]I'm syncing from a vfat partition on my laptop to a vfat partition on my USB HDD.[/QUOTE]
 After synchronizing, check permissions of a file on your laptop and the same file on USB HDD. Are the permissions the same?

---

