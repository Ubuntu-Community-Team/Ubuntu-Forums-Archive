---
title: "[SOLVED] 7zip pieces"
date: 2007-07-21
forum: General Help
---

### Post by Labouts on 2007-07-21
Ok, so I have a zip archive in about 72 pieces like 7z.001 7z.002 7z.003 ect

I haven't been able to find how to deal with this on Ubuntu, I remember with windows you would just open the first file but that isn't working and I haven't found any other topics on, some help please?

---

### Post by drekon_v1 on 2007-07-21
Starting with the first volume and progressively moving upwards:
```

7z x file.7z.001 -o{DESTINATION}
7z x file.7z.002 -o{DESTINATION}

```
and so forth

---

### Post by Labouts on 2007-07-22
Thanks but that made 72 empty dictionaries, is there something wrong with the files or did I mess up?

---

### Post by bodhi.zazen on 2007-07-22
See this thread : [http://ubuntuforums.org/showthread.php?t=476048](http://ubuntuforums.org/showthread.php?t=476048)

You can do this in one command :

Put all the pieces in a single directory, say zip
 cd into the directory

the ```
for i in ./* ; do cat "$i" >> ../new_zip; done
```

This will create a new archive one directory higher "new_zip", unzip that one ;)

---

### Post by Labouts on 2007-07-22
O.O Never would have thought of that, thanks it worked :)

---

### Post by vanadium on 2007-07-22
```

cat * > ../new_zip.zip

```
will also work to binary combine the files.

---

### Post by mikewhatever on 2007-07-22
Hopefully, the gui for 7z is on the way.

---

### Post by bodhi.zazen on 2007-07-22
> **vanadium said:**
> ```

cat * > ../new_zip.zip

```
will also work to binary combine the files.

Well, almost ... you need two >> or you will overwrite new_zip, so ...

```
cat * **>>** ../new_zip.zip
```

definitely not as geeky though :twisted:

> **mikewhatever said:**
> Hopefully, the gui for 7z is on the way.

Mike, have you tried xarchiver ? 

> Xarchiver, a lightweight GTK2 only frontend to 7zip,arj,bzip2,gzip,iso,rar,lha,deb,rpm,tar and zip

The problem is the linux zip does not yet handle splitting the archive ... so you need to combine them first ;)

---

