---
title: "Help!  My tarball isn't fully extracting, with no errors"
date: 2018-10-04
forum: General Help
---

### Post by redneckdiver on 2018-10-04
I needed to expand /boot last night, and decided to just do a fresh 18.04 install.  So I backed up my home directory as a tarball on another system.  I did a test extraction to /dev/null to test the tar integrity and got no errors.  I just tried restoring it, and it's only extracting 5gb out of 75 gb, with no reported errors.  If I list the archive contents, it's obvious that for some reason the data is all in the tar file, but not all the file metadata.  Has anyone ever ran into this?  Anyone have a fix?  I'd be happy to just extract each file to a random name.

---

### Post by TheFu on 2018-10-04
Welcome to the forums.

tar was designed for use when 50MB was considered huge.  Using it for anything larger than a few GB is a poor choice. 

Better backup/archival choices include validation capabilities, for example. May want to consider using something other than tar going forward.

Perhaps if you posted the EXACT command used to create the tar and the EXACT command being attempted to recover it, someone could help?

---

### Post by coffeecat on 2018-10-04
Support, not chat.

*Thread moved to **General Help**.*

---

