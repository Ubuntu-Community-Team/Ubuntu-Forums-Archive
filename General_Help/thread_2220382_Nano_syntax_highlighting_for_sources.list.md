---
title: "Nano syntax highlighting for sources.list"
date: 2014-04-27
forum: General Help
---

### Post by cogset on 2014-04-27
This will be a dumb question for most of you,however:if I open in nano the file sources.list,it's displayed in color,which I assume is because of some sort of syntax highlighting going on-however,if I copy the same unmodified file to another location,the highlighting is still there,but not after renaming the same (still unmodified) file.
Why the highlighting is gone after renaming *sources.list* to,say,*sources1.list* ? Is there a way to turn it on again in nano ?

---

### Post by Doug S on 2014-04-27
I think you will find that /etc/nanorc has an include line (one of many) to include "/usr/share/nano/debian.nanorc".
And that file defines the sources.list color scheme. You could add sources1.list to that file.
Or, I think just define it on the command line with the -Y option (which I did not try, see "man nano").

---

### Post by cogset on 2014-04-28
"Mistery" solved,thank you very much.

---

