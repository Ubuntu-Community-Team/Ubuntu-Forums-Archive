---
title: "ownership management"
date: 2013-12-17
forum: General Help
---

### Post by muhammad.samsuri.c on 2013-12-17
how to set access of directory if user can do anything with the directory except delete those directory and files inside those directory?

---

### Post by varunendra on 2013-12-20
Welcome to the forums muhammad.samsuri.c !

If, by "anything" you mean editing of files too (that is, "write" permission), then I don't think it is possible. Granting a user the "write" permission (which is necessary to edit the file) means you are also granting the permission to 'delete' (which is logically a special case of "Editing" or "Writing").

Then again, I'm not sure what advanced Linux permissions are capable of doing, so I'm open for corrections. :)

---

