---
title: "A problem with permissions in 13.04 64 bit Ubuntu"
date: 2013-04-22
forum: General Help
---

### Post by Silverflyer on 2013-04-22
Hi, I have a weird problem and would appreciate any help getting it solved.  I copied to an external drive the music files from my mac mini running iTunes.  All are AIFF files, and most of them copied over just fine and play fine in Linux.  Some did not, and the reason was given that I do not have sufficient permissions to copy them.  There is nothing special about them, no DRM, just CD rips like all the rest.

Is there a way I can get around that and copy ALL my music files to my Linux computer?

---

### Post by Slim Odds on 2013-04-22
During the copy this is happening?

---

### Post by Silverflyer on 2013-04-22
copying the files over to my ubuntu from the external drive, yes.

---

### Post by Silverflyer on 2013-04-23
Here is an image of the error message I get when copying my music files to Ubuntu.

[IMG]http://img703.imageshack.us/img703/5932/54607941.png[/IMG]

---

### Post by Slim Odds on 2013-04-23
> **Silverflyer said:**
> Here is an image of the error message I get when copying my music files to Ubuntu.

[IMG]https://imageshack.us/a/img703/5932/54607941.png[/IMG]
A screen capture with "Show more details" expanded would be great.

---

### Post by Silverflyer on 2013-04-24
it is expanded.

---

### Post by Impavidus on 2013-04-25
How is the external drive formatted? FAT32, ntfs, ext4 (not sure whether those are supported on a mac). Or does there already exist a file in the target directory with the same name? If you don't have write permissions on the existing copy in your target directory it can't be opened for writing, although it can be forced by deleting and creating a new file.

---

