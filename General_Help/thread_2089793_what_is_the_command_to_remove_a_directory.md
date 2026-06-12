---
title: "what is the command to remove a directory ?"
date: 2012-11-30
forum: General Help
---

### Post by winzip on 2012-11-30
what is the command to remove a directory ?

the directory has many sub-folders and many files inside sub-folders .

I want complete deletion of  directory.

whats the command ?

rm -r  directoryname   does not remove directory .

---

### Post by drmrgd on 2012-11-30
That should work.  What is the error you're getting.  Also, can you confirm you have permissions on the parent directory under which that directory is located?

---

### Post by wojox on 2012-11-30
```
rm -rf dirName
rmdir dirName
```

---

### Post by wojox on 2012-11-30
> **drmrgd said:**
> Also, can you confirm you have permissions on the parent directory under which that directory is located?

And that. :)

---

### Post by shaktiman1234 on 2012-11-30
try ```
rm -rf YourDirectory
```

---

### Post by dcottingham on 2012-11-30
That second line "rmdir /dirName" is not necessary (the first line has already removed it) and not correct (the directory is not necessarily in /).

---

### Post by zombifier25 on 2012-11-30
> **wojox said:**
> ```
rm -rf dirName
rmdir /dirName
```

You forgot a dot there, it's supposed to be
```
rmdir ./dirName
```
But, you can just do
```
rmdir dirName
```

Then again, like dcottingham said, that line is not necessary.

---

### Post by wojox on 2012-11-30
> **dcottingham said:**
> That second line "rmdir /dirName" is not necessary (the first line has already removed it) and not correct (the directory is not necessarily in /).

> **zombifier25 said:**
> You forgot a dot there, it's supposed to be
```
rmdir ./dirName
```
But, you can just do
```
rmdir dirName
```

Then again, like dcottingham said, that line is not necessary.

:) Thanks.

---

### Post by jon zendatta on 2012-11-30
```
rm -R nameofdirectory
```:KS

---

