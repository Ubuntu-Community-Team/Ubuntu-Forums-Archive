---
title: "Help ! &quot;Symbol Lookup Error&quot;"
date: 2007-10-07
forum: General Help
---

### Post by Naatan on 2007-10-07
I can't boot ubuntu anymore :( When I boot in safe mode to debug and try to vim something I get the following error:

symbol lookup error /us/lib/gtk-x11-2.0.so.0 undefined symbol g_hash_table_ref

I can't do anything right now as without vim I can't change any settings.. genious.

The only thing I can think of that might have caused this was the installation of xserver-xgl but I removed it again and it still gives the error.

Can anyone please help?

---

### Post by Naatan on 2007-10-07
Come on! Anyone?!!

---

### Post by Naatan on 2007-10-07
Still not solved =\

---

### Post by bettlebrox on 2007-10-07
Sounds like a partition wasn't mounted. What does the command mount show?

---

### Post by Naatan on 2007-10-07
It's not that, trust me.

The file "/us/lib/gtk-x11-2.0.so.0" symlinks to another file with a similar name

/us/lib/gtk-x11-2.0.so.0.800 or something.. I can't remember exactly and I can't check right now.

I have deleted the file it links to and reinstalled all packages with gtk in their name with apt-get, this re-creates the file but it still gives the same error..

---

### Post by bettlebrox on 2007-10-07
Is that the exact error message or a typo?

**/us**/lib/gtk-x11-2.0.so.0

---

