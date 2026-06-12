---
title: "Load libraries in non-standard locations ?"
date: 2007-03-22
forum: General Help
---

### Post by Bachstelze on 2007-03-22
If I want to run a binary that needs a lib and looks for it in /usr/lib, is there a way to run it when the lib is somewhere else besides using LD_PRELOAD ?

---

### Post by mcduck on 2007-03-22
You could create a symling from the lib to /usr/lib, with 'sudo ln -s /path /to/yourlibrary /usr/lib/yourlibrary'

---

### Post by streeto on 2007-03-22
Normally, excutables will look for libraries at the path defined by LD_LIBRARY_PATH environment variable. Isn't it the case? I have never seen an executable load libraries with a fixed path. SOmeone please correct me if I am wrong.

---

