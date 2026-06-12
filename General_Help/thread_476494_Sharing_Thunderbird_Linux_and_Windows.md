---
title: "Sharing Thunderbird: Linux and Windows"
date: 2007-06-17
forum: General Help
---

### Post by Howard Kaikow on 2007-06-17
Installed Thunderbir in Ubuntu 7.04 last night.
Thunderbird version is 1.5.0.12.
I have 2.0.0.0 in Windows, with 2.0.0.4 waiting to be installed.

Can I safely share, between linux and windows, THunderbird profile and mailboxes using these different versions?

If not, when can we expect te .deb file for 2.0.0.0 or 2.0.0.4 of Thunderbird?

---

### Post by scrooge_74 on 2007-06-17
I have manage to do that, what you need to set is to point both versions of thunderbird to point to the same folder.

I did that by making the ntfs partition read/write and telling the linux version to use that directory as the place to look for mails, profiles etc.  So when i open thunderbird in any of the two OS everything works correctly.

---

### Post by Howard Kaikow on 2007-06-17
> **scrooge_74 said:**
> I have manage to do that, what you need to set is to point both versions of thunderbird to point to the same folder.

I did that by making the ntfs partition read/write and telling the linux version to use that directory as the place to look for mails, profiles etc.  So when i open thunderbird in any of the two OS everything works correctly.

Thanx, let me clarify.

My concern is using version 1.5.0.12 in Linux and version 2.x in Windows.

---

### Post by scrooge_74 on 2007-06-17
As far as I know that should not be a problem because your emails are stored as files and the folders you have the mails in are just folders in the disk.  I used to have 6.06 on one partition and 6.10 in another (the thunderbird versions are different between them) and the data in a separate /home partition.  And I had no trouble doing this.

From my experience things should not be problematic, at the most when you start thunderbird it is going to make a quick check for compatibilities and thats all.

---

