---
title: "Renaming multiple image files...."
date: 2023-03-08
forum: General Help
---

### Post by Furycd001 on 2023-03-08
Hi Guys..

I have a folder that contains hundreds of images..

> 
adna-lola.jpg
adna-lola.jpg1
adna-lola.jpg2
adna-lola.jpg3
adna-lola.jpg4
adna-lola.jpg5
adna-lola.jpg6
adna-lola.jpg7
adna-lola.jpg8
anastasiya.jpg
anastasiya.jpg1
anastasiya.jpg2
anastasiya.jpg3
anastasiya.jpg4
anastasiya.jpg5
anastasiya.jpg6
anastasiya.jpg7
anastasiya.jpg8
heva.jpg
heva.jpg1
heva.jpg2
heva.jpg3
heva.jpg4


How do I move the numbers from after to before the filename? Like **adna-lola.jpg4**, should be **adna-lola4.jpg**, and so forth. I know I could sit & do it all manually, but I'd like to automate the process with bash if possible....

---

### Post by SeijiSensei on 2023-03-08
I'd try something like this:
```

for f in *
do
FILENUM=$(echo $f | sed 's/.*\.jpg//g' )    # result is trailing digit
FILENAME=$(echo $f | sed 's/\.jp.*$//g')    # result is filename without extension
NEWNAME="$FILENUM-$FILENAME.jpg"
mv $f $NEWNAME
done

```
Not fully tested so you might need to make some tweaks. Run this in the directory where the files are stored. Copy a bunch of the files into a test directory and run it there first.

Result should be 1-adna-lola.jpg, etc.

---

### Post by Furycd001 on 2023-03-09
Thank you so much :) That worked perfectly :)

---

### Post by TheFu on 2023-03-09
Another answer for this is to use **qmv**, which lets you use the editor of your choice to do stuff like this.  I know exactly how to do it in vim using the visual selection tool.

---

### Post by Holger_Gehrke on 2023-03-09
Or you could have used the 'rename' command:
```

rename 's/(.*).jpg(.*)/$1-$2.jpg/' *[0-9]

```
which would result in adna-lola.jpg4 becoming adna-lola-4.jpg ...
Holger

---

