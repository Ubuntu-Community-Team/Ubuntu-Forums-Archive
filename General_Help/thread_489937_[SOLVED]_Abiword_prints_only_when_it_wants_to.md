---
title: "[SOLVED] Abiword prints only when it wants to"
date: 2007-07-01
forum: General Help
---

### Post by Super TWiT on 2007-07-01
I have compiled abiword from source and used the version from the repositories, however Abiword sometimes prints and sometimes it doesn't.  Compiling it from source fixed this in Drapper.  The error it outputs in the terminal is this:

 GnomePrint-CRITICAL **: gnome_print_filter_flush: assertion `GNOME_IS_PRINT_FILTER (f)' failed

---

### Post by Super TWiT on 2007-08-07
I finally was able to fix this by deleting every entry with Abiword in it.  I believe that was because I compiled it to begin with instead of using the pre-compiled binary.  I guess I didn't remove all the entries with Abiword in it.

---

