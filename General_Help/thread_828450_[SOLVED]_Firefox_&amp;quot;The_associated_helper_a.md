---
title: "[SOLVED] Firefox: &amp;quot;The associated helper application does not exist&amp;quot;?"
date: 2008-06-13
forum: General Help
---

### Post by rainwalker on 2008-06-13
Whenever I try to open something via the "Open With..." dialog, I get this error:
> /tmp/Songbird_0.6_linux-i686.tar-1.gz could not be opened, because the associated helper application does not exist. Change the association in your preferences.
This just started happening, any suggestions?
I'm using the latest version of Firefox available in the Hardy repos.

---

### Post by geraldm on 2008-06-13
firefox has helper applications available for files with sensible suffixes that indicate how to handle them.  It could work for a text file, maybe even for file.tar.gz but file.tar-1.gz is not a suffix that it knows how to handle.

You could try to handle it manually, then rename the file to a proper suffix.

Gerald

---

### Post by rainwalker on 2008-06-13
> **geraldm said:**
> firefox has helper applications available for files with sensible suffixes that indicate how to handle them.  It could work for a text file, maybe even for file.tar.gz but file.tar-1.gz is not a suffix that it knows how to handle.

You could try to handle it manually, then rename the file to a proper suffix.

Gerald

Ah! I didn't even notice that! Thank you :)

---

