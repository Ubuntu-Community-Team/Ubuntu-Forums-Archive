---
title: "Renaming files in ubuntu according to time and date"
date: 2017-03-31
forum: General Help
---

### Post by Semn on 2017-03-31
Hi, I have some hundred thousand files that need to be renamed according to their time of generation. They are all png's, however some of them where made with seconds in betweem so the time seems the same.

Is there a way to rename all files from 1 to 9999999  according to the time (minutes and seconds) they were generated in the Ubuntu terminal?

Thanks

---

### Post by SeijiSensei on 2017-03-31
If you use 
```
ls -l --time-style='+%s'
```
the files will be listed with "Unix time," the number of seconds since midnight GMT on 1/1/70 like this:
```
-rw-rw-r-- 1 seiji seiji 1000 **1490968518** testfile
```
You could write a script that would grab that field and use it to rename the file.  Something like
```

mkdir newfiles
for f in *.png
do
     TIME=$(ls -l --time-style='+%s' $f | awk '{print $5}')
     cp $f newfiles/$TIME.png
done

```
The renamed files will be placed in the "newfiles" subdirectory under the current directory.  This assumes no two files were created at the identical second.

Please test this out in a separate directory with just a few files!

--time-style uses the time formats listed in "man date".

---

### Post by steeldriver on 2017-03-31
Do you want to name them **with **the time of generation (in practice, it would probably be the modification time)? or name them **in order of** time of generation?

---

### Post by Semn on 2017-04-01
In order of the time of generation. Trying Senseis method.

---

### Post by SeijiSensei on 2017-04-01
Oops, I must have miscounted fields.  You need to use '{print $6}' since the timestamp is the sixth field in the ls output.

---

