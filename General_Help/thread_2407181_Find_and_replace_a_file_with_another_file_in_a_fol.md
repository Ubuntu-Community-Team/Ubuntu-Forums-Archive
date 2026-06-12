---
title: "Find and replace a file with another file in a folder and subfolder"
date: 2018-11-30
forum: General Help
---

### Post by cazz on 2018-11-30
Hi
I have some file name index.php and I like to replace them with another file (Another index.php)

So I like to search in a folder and every subfolder to replace the file

I do use this command to remove files

```
find . -name "*.db" -type f -delete
```


and I guess I can use -exec and cp but then I'm not sure anymore.



/Update


I did find it myself :)

```
find /foldertosearch/ -name 'index.php' -exec cp /foldertothenewfile/index.php {}   \;
```

---

