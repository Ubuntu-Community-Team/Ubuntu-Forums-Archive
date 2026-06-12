---
title: "OpenBox help.."
date: 2006-12-06
forum: General Help
---

### Post by Somenoob on 2006-12-06
When i launch this program **Applications>Other>ObConf** for adding new themes to the OpenBox WN, I receive the following error message:

```
obconf: error while loading shared libraries: libobrender.so.1: cannot open shared object file: No such file or directory
```

Thanks in advance...

---

### Post by timbosa on 2006-12-09
Have a look here
[http://ubuntuforums.org/showpost.php?p=1515986&postcount=2](http://ubuntuforums.org/showpost.php?p=1515986&postcount=2)

```
sudo ln libobparser.so.0.4.0 libobparser.so.1
sudo ln libobrender.so.0.4.0 libobrender.so.1
```Fixed this problem for me

---

### Post by K.Mandla on 2006-12-09
Yup, that's something unique to Edgy. I think there are packages awaiting approval that were supposed to fix that error. But it's been a looong time.

---

### Post by patrick295767 on 2006-12-09
U can also find the libs in the dapper deb !!

Ahhhhhh edgy ..... !!!

---

### Post by Somenoob on 2006-12-10
Problem solved :D 

Now i can finally use my favourite window manager. Sad to see all these errors or uncomfortable changes in Edgy.

---

