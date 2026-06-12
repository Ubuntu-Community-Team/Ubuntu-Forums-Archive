---
title: "Password on folder"
date: 2006-11-25
forum: General Help
---

### Post by arya6000 on 2006-11-25
Is there anyway I can put a password on some folders?

---

### Post by kabuto_san on 2006-11-25
I think you can use the USER file/folder permission...

chown -R youruser.yourgroup files_and_folders

bye

---

### Post by StormNet on 2006-11-25
Are you trying to make it so that only you can read them, or do you need certain people to be able to read them as well?

---

### Post by xopher on 2006-11-25
I think the guy really wants to have a password promted when trying to open the folder :) Which would be a nice, still rather useless feature - because of chown etc.

---

### Post by gschoper on 2006-11-25
If you want that type of protection, you may want to consider [TrueCrypt](http://www.truecrypt.org/). Search the forums for a HowTo.

gschoper

---

