---
title: "Tracker not indexing odf on content"
date: 2007-05-31
forum: General Help
---

### Post by markba on 2007-05-31
It seems that tracker does index odf-files, but only on filename, not on content. As a result, it is not possible to search on the content of the odf-file, only by filename.

When I save the same odf-file into pdf, it *is* indexed on content and I can search on that. Saving odf to doc does not help, same result as odf. You can actually see that the content is not indexed, because in tracker-search-tool, the context of the found string is empty. In case of the PDF (content indexing is working there), the context is shown.

As far as I know, tracker should or could index odf files out-of-the-box.

I'm using Feisty, tracker 0.5.4

---

### Post by markba on 2007-06-02
I found the solution my self: just installed packages o3read (for oo-documents) nd wv (for ms doc-documents). These packages are suggested by tracker, but not auto-installed. As for now, documentation is a bit lacking.

---

### Post by wyth on 2007-06-07
Can I ask where you found the list of suggested files?  I'm trying to get Tracker up and running.

---

