---
title: "seaching folders under /media/foldername for pdf files with specific text using Recol"
date: 2014-06-08
forum: General Help
---

### Post by cigtoxdoc on 2014-06-08
I have having a problem with syntax for searches for PDF documents with specific text using Recoll 1.16.2 + Xapian 1.2.8.  The folder I want to search is /media/foldername.  Foldername contains numerous subfolders all containing searchable PDF documents.  If I do not restrict the search to /media/foldername, recoll picks out Evolution e-mails with pdf attachments containing the search term, sugar.  It does not pickup anything under /media/foldername, even though foldername is permanently mounted.

How do I get around this problem.  OS is Ubuntu 12.04 64-bit.

Thank you,

John

---

### Post by TheFu on 2014-06-09
Stupid question - did you tell recoll  to index those folders and rerun the indexing?  Is there enough storage for the indexes?
Have you considered moving the "permanently mounted" storage to be outside the /media/ area so that tools don't think it is temporary storage?

---

### Post by cigtoxdoc on 2014-06-17
Thank you four your reply.  Recol works fine with permanently mounted storage (permanent mounted needed SpiderOak backup).  I just had to figure out how to tell recol where my documents were.

John

---

