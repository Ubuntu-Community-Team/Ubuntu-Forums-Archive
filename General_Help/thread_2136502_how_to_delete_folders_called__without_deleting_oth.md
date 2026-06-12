---
title: "how to delete folders called * without deleting other folders?"
date: 2013-04-17
forum: General Help
---

### Post by sohlinux on 2013-04-17
this may look unusual but I have a lot of folders called * , I want to recursively delete them all but if I use rm -rf * command it deletes all the other folders too

for example

 [~]# mkdir 001
 [~]# cd 001
 [~/001]# mkdir *
 [~/001]# mkdir 001
 [~/001]# ls
./  ../  */  001/
 [~/001]# rm -rf *
 [~/001]# ls
./  ../

how can I only delete the folders called *? and I need to do it recursively.

thanks

---

### Post by sandyd on 2013-04-17
> **sohlinux said:**
> this may look unusual but I have a lot of folders called * , I want to recursively delete them all but if I use rm -rf * command it deletes all the other folders too

for example

 [~]# mkdir 001
 [~]# cd 001
 [~/001]# mkdir *
 [~/001]# mkdir 001
 [~/001]# ls
./  ../  */  001/
 [~/001]# rm -rf *
 [~/001]# ls
./  ../

how can I only delete the folders called *? and I need to do it recursively.

thanks
escape using double quotes
i.e. like
```

rm -rf "*"
```

---

### Post by sohlinux on 2013-04-18
> **sandyd said:**
> escape using double quotes
i.e. like
```

rm -rf "*"
```

thanks

---

