---
title: "Azureus help, file name change."
date: 2007-10-20
forum: General Help
---

### Post by Nathan Otis on 2007-10-20
Hello all,

I have been following instructions found in the forums to get Azureus to update properly and I believe I'm one step away from perfection! The updater gave me instructions to rename a file, but I didn't pay attention  well enough and now I'm stuck.

In the folder: opt/azureus, I have two files. One called "azureus", the other called "azureus.new". I need to rename then so the current one is ".old" and the ".new" one is "azureus".

Help!
Thanks!
Nathan!

*edit: I can't do this the "normal" way because I don't "own" the folder these files are in

---

### Post by Cybergod on 2007-10-20
Open a terminal (Applications -> Accessories -> Terminal).  
Type "cd /opt" without the quotes.  Now type "sudo mv azureus azureus.old" and "sudo mv azureus.new azureus" without the quotes.

---

### Post by Nathan Otis on 2007-10-20
Thanks so much for the answer. I did exactly as you said and the name change worked flawlessly. When I try to start Azureus, however, even though the Azureus update TOLD ME to make this change, I get the following error message:

**COULD NOT LAUNCH APPLICATION**
Failed to execute child process "/opt/azureus/azureus"
(Permission denied)

I am able to switch the files back with a little edit of the instructions you gave and Azureus works again. Is this something simple that I'm missing (as it almost always is...?)

Thank you.
n.

---

