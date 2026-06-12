---
title: "Zip question"
date: 2007-10-21
forum: General Help
---

### Post by Pipotchi on 2007-10-21
Hi all,

Very simple question here. I have a folder of many individual files in it. I would like to zip them individually (i.e. creating a .zip file for every file in the directory). I have look at the zip manual (man zip) and I have not found what I wanted. Is there a command that does that automatically or I have to create a script to do that? If so, can someone help me create a simple script please? Thank you

---

### Post by spin2cool on 2007-10-21
Here's a bash example that assumes a couple of things:
you have a folder full of files with the same extension (xyz.jpg) that you want to put into zips with the same name (xyz.zip)

> for i in *.jpg;do zip `basename $i .jpg`.zip $i;

---

### Post by Pipotchi on 2007-10-21
Thanks for the script. However, I am not familiar with bash and I get this error:

raphael@raphael-desktop:~/Photos$ bash zip.sh 
zip.sh: line 3: syntax error: unexpected end of file

Is there anything I need to add in order to close the code, something similar to End Sub in VB? Thank you.

---

### Post by spin2cool on 2007-10-21
sorry - there's a typo.  try this:

for i in *.jpg;do zip `basename $i .jpg`.zip $i;done

You need the "done" to close the for loop.  Also, fwiw, you can just paste this command into a terminal.  No need to to put it into a file unless you're planning on adding lines and making it a more complicated script.

---

### Post by bodhi.zazen on 2007-10-21
One comment, you should quote $i to protect it in the event of white space, like a space in the name of a file

my picture.jpg

```
for i in *.jpg;do zip `basename "$i".jpg.zip "$i";done
```

*also watch the space in the command between $i and .jpg and .jpg and .zip unless you want spaces in the output ...

---

