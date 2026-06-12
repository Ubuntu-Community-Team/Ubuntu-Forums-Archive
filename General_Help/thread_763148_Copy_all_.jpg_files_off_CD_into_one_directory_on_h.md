---
title: "Copy all .jpg files off CD into one directory on hdd"
date: 2008-04-22
forum: General Help
---

### Post by Dr_Snapid on 2008-04-22
I have a CD with JPG images on it, spread over many directories.

This command finds them:

find /media/cdrom0/ -name *.jpg

How do I automatically copy those files to a single folder on my hard disk?

Can I use the results of find to make a cp command?

something like 
find /media/cdrom0/web-content/Posters/ -name *.jpg | cp /destination

I dont know how to combine the commands, can anyone help?

---

### Post by logos34 on 2008-04-22
what about 

cp /media/cdrom0/web-content/Posters/*.jpg /user/home/somefolder

?

---

### Post by sdennie on 2008-04-22
You can use the results of a command as an argument to another using backticks.  So:

```

cp `find /media/cdrom0/ -name "*.jpg"` ~/somewhere

```

---

### Post by Dr_Snapid on 2008-04-22
> **vor said:**
> You can use the results of a command as an argument to another using backticks.  So:

```

cp `find /media/cdrom0/ -name "*.jpg"` ~/somewhere

```

That worked perfectly! Thanks so much.

---

### Post by Dr_Snapid on 2008-04-22
Oh dear.... some of the image folders have spaces in their names. So the output of find is broken and cp looks for folders which arent there causing the copy to fail. How would I make find's output wrap the output in quotes so the spaces dont stuff up the cp command?

Hope that makes sense.

---

### Post by Jose Catre-Vandis on 2010-05-08
Old topic, but just to clear it up

To search folders that may have spaces in their names, just put double quotes around the search folder, so change
```
cp `find /media/cdrom0/ -name "*.jpg"` ~/somewhere
```to
```
cp `find "/media/cdrom0/" -name "*.jpg"` ~/somewhere
```

but this only works on the first line directory

To do everything you need to switch things around

```

find /media/cdrom0 -name "*.jpg" -type f -exec cp {} ~/somewhere \;

```

---

