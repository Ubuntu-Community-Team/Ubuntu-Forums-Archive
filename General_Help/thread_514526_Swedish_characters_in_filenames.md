---
title: "Swedish characters in filenames"
date: 2007-07-31
forum: General Help
---

### Post by Fredrik_b on 2007-07-31
I have some problem with Swedish characters in Ubuntu.

Files and catalogs that has been created using windows is not displayed with the characters Å, Ä or Ö. instead they appears as an &#65533;.

I have gathered that it mostly is due to different character encodings, but how do I fix this?

---

### Post by Fredrik_b on 2007-08-01
tried this command: convmv --notest -f ISO-8859-1 -t UTF-8 -r  *

but that only resulted that &#65533;. was replaced with ‚

Why does Desty not have support fore some thing as basic as non US characters that wasent created by Ubuntu?

---

