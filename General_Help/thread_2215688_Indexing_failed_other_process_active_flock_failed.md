---
title: "Indexing failed: other process active? flock failed"
date: 2014-04-07
forum: General Help
---

### Post by Robbyx on 2014-04-07
Indexing failed: other process active? flock failed

In Recoll I get the error message when I choose to update the index. Does anyone recognise what is likely to be causing the file lock failure?

I looked at /home/rob/.recoll/xapiandb and there is a file there callend flintlock. Is that the cause? I have not tried deleting it.


I haven't found a log that would help find the cause.

---

### Post by Robbyx on 2014-04-07
I just tried renaming flintlock to flintlock.old and I still get the error message, so I renamed it back again.

---

### Post by medoc92 on 2014-04-09
Hi,

Have you checked if you have a recollindex process running ? If you have selected real time updating, an indexer is running permanently, and the "Update index" action will fail (because it just tries to start another one). And yes, the problem should be detected and explained in this case!

Edit: the GUI is supposed to manage this properly. What version are you running ?

Do you have a recollindex process running?

---

