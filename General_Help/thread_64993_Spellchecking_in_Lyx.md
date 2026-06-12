---
title: "Spellchecking in Lyx"
date: 2005-09-12
forum: General Help
---

### Post by alastair lewis on 2005-09-12
I am completly sold on Lyx as a document processor. However, if I try to Spellcheck I get the error "Lyx has failed to start ispell". This problem is mentioned in the user guide but I have been unable to sort it out. Can anyone help?

---

### Post by arnieboy on 2005-09-13
[QUOTE=alastair lewis]I am completly sold on Lyx as a document processor. However, if I try to Spellcheck I get the error "Lyx has failed to start ispell". This problem is mentioned in the user guide but I have been unable to sort it out. Can anyone help?[/QUOTE]
do the following and try again:
```
sudo apt-get install ispell liblingua-ispell-perl
```

---

### Post by alastair lewis on 2005-09-13
Thanks for that. I had downloaded the dictionaries but couldn't work out where to put them. It's all becoming clear.

After a bit of fiddling I have managed to build my dictionary and we are off and away.

---

