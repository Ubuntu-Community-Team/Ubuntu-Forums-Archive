---
title: "[SOLVED] Gedit Dictionary"
date: 2007-06-16
forum: General Help
---

### Post by oomingmak on 2007-06-16
Where does Gedit store the User Dictionary and can it be edited?

I accidentally clicked add new word on a wrong spelling and now this incorrect spelling keeps getting suggested as a correct replacement. I'd like to remove this word from my user dictionary, but I can't find where it's stored.

---

### Post by PaulFr on 2007-06-16
For me, I found the personal dictionary in a simple text file called **.aspell.en.pws** in my home directory. I assume the .en refers to English, so it may be different for each language. Perhaps a **ls -la .aspell.*.pws** in your home directory should find all such files.

---

### Post by oomingmak on 2007-06-16
Thanks!

I found it and managed to remove the mis-spelled word.

---

