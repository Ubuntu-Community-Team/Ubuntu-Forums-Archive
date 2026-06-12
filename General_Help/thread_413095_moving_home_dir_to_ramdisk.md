---
title: "moving home dir to ramdisk"
date: 2007-04-18
forum: General Help
---

### Post by fergus4 on 2007-04-18
I want to prevent users from writing to disk in anyway..cookies bookmarks, downloads etc.

I thought if I moved the users directory to Ram all would be erased on reboot. Is this possible or is there another way to achieve this. 

I essesntially want to lock out the system so no changes can be made and nothing can be written to disk.

---

### Post by dcstar on 2007-04-19
> **fergus4 said:**
> I want to prevent users from writing to disk in anyway..cookies bookmarks, downloads etc.

I thought if I moved the users directory to Ram all would be erased on reboot. Is this possible or is there another way to achieve this. 

I essesntially want to lock out the system so no changes can be made and nothing can be written to disk.

You should be able to make a system where the user accounts cannot log on to a terminal (with the default shell as "false") and have zero disk quota.

---

