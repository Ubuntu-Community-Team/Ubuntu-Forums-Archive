---
title: "Bash Scripts"
date: 2015-07-14
forum: General Help
---

### Post by motar2 on 2015-07-14
I am trying to get a bash script to work. I will like to create a contact sheet of photographs, which are store on folders name with the date the pics were taken, i.e. 20111009 etc..
But I only want one picture per folder and the folder name and number of files.

There are about 12 years worth of pictures in about 330+   folders.
The files names are standard digital photo names with the date and no odd characters or spaces.

This is what I have so far.


  ```
 find . -iname "*.jpg" -o -iname "*.JPG" |
    while IFS= read -r img; do

    name=$(basename "$img")
    path=$(dirname "$img")
    ext="${name/#*./}";

     convert "$img" -thumbnail 400x400 "${name/%.*/thumb.$ext}";

done

done

```

This works quite well but what I need is to get just one picture from each folder with the name of the folder and the number of pictures in each folder.

I have hacked a script from a chap call John Hobbs, which has the script at 
[HTML]https://github.com/jmhobbs/helper-scripts/blob/e0441fe4abd962f5a84cc13fc3954b1bf31279f3/digiCamProc.sh.[/HTML]

The script is great for normal contact sheets but I cannot figure how to process only one pic for folder.

Hope some bash guru can shed some light on this.

---

### Post by sudodus on 2015-07-14
Did you consider using one of the existing photo organizers? Please have a thorough look at ***Shotwell*** and ***Digikam*** too see if these programs can do the job for you.

Using ***tags*** makes it easier to find the relevant picture you are looking for.

---

### Post by motar2 on 2015-07-14
The reason that I want a script is because I want to share the photographs with my family and friends, was thinking of making a DVD with folder chapters etc.
For which the Folder contact sheet would work quite well.

---

### Post by sudodus on 2015-07-14
Another alternative that should work in most computers is a pdf file. [B][I]Make a presentation with LibreOffice Impress, and export it as a pdf file.
[/I][/B]
***A third alternative is to upload it to the internet cloud***. We all know that there are several free services, that are more or less open, for example Google Drive or Facebook. But if you want to keep it private, or to have a hands-on feeling, this is not an option.

-o-

The following 'one-liner' will pick the first file in finds in each sub-directory (that contains jpg or JPG files) and with some modification you can change it to not only list the file but do something with it, for example create a thumbnail picture. Is that what you want (so that you need not pick each file manually)?

```
for i in $(find . -type d); do ls -1 $i/*.{jpg,JPG} 2>/dev/null|head -n1;done
```

This one displays the selected pictures with an outer loop (if you have the file viewer eog)
```
for j in $(for i in $(find . -type d); do ls -1 $i/*.{jpg,JPG} 2>/dev/null|head -n1|sort;done);do eog $j;done
```

And this one displays them after sorting which may or may not be what you want
```
for j in $(for i in $(find . -type d); do ls -1 $i/*.{jpg,JPG} 2>/dev/null|head -n1;done|sort);do eog $j;done
```

---

### Post by motar2 on 2015-07-16
> **sudodus said:**
> Another alternative that should work in most computers is a pdf file. [B][I]Make a presentation with LibreOffice Impress, and export it as a pdf file.
[/I][/B]
***A third alternative is to upload it to the internet cloud***. We all know that there are several free services, that are more or less open, for example Google Drive or Facebook. But if you want to keep it private, or to have a hands-on feeling, this is not an option.

-o-

The following 'one-liner' will pick the first file in finds in each sub-directory (that contains jpg or JPG files) and with some modification you can change it to not only list the file but do something with it, for example create a thumbnail picture. Is that what you want (so that you need not pick each file manually)?

```
for i in $(find . -type d); do ls -1 $i/*.{jpg,JPG} 2>/dev/null|head -n1;done
```

This one displays the selected pictures with an outer loop (if you have the file viewer eog)
```
for j in $(for i in $(find . -type d); do ls -1 $i/*.{jpg,JPG} 2>/dev/null|head -n1|sort;done);do eog $j;done
```

And this one displays them after sorting which may or may not be what you want
```
for j in $(for i in $(find . -type d); do ls -1 $i/*.{jpg,JPG} 2>/dev/null|head -n1;done|sort);do eog $j;done
```

Hi sudodus,
Thanks for your input, these one-liners are great and have taught me a lot about bash scripting.
This is really my beginning with bash so was very helpful.
Finally I managed to work out a system that copies one file per folder to a temp dir, renames the images by appending the folder name and then, runs the contact sheet creation script.
Quite happy with the results.
All the best.

---

### Post by sudodus on 2015-07-16
Congratulations :KS

I'm glad I could help, and I'm glad that you have made your own bash script that is doing what you want.

---

