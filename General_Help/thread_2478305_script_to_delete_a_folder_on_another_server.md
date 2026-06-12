---
title: "script to delete a folder on another server"
date: 2022-08-22
forum: General Help
---

### Post by pac00zilla on 2022-08-22
Hello friends


the idea would be to create a script to delete a folder on this server and copy another folder with the same name in place of the one that was deleted, the folder where it copies I already managed to do it using the scp command only the first part that I have no idea of how to make


Does anyone have a similar script that I can use as an example?

---

### Post by ActionParsnip on 2022-08-22
```

ssh user@server rm -r /path/to/folder

```
Will delete the folder you name

---

