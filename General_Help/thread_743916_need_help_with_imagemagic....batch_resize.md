---
title: "need help with imagemagic....batch resize"
date: 2008-04-03
forum: General Help
---

### Post by zeltak on 2008-04-03
Hi all

I am moding a icon theme (will post it once finished) to my liking. I have a Q for the command line gurus. I have edited the icon theme for the 128 size. the 128 folder has 6 directories with pngs in them. i want to use image magic to resize the whole directory to 64x64 size while keeping the folder structure, is it possible?

thx alot in advance

Zeltak

---

### Post by vanadium on 2008-04-03
It is surely possible. Use the find command to find all files in the directory tree. With the "-exec" option, you can run the imagemagick convert command automatically on each file in the directory tree:

find <start of directory tree> -name "<filemask>" -execdir convert "{}" <convert options> \;

{} will be replaced with the filenames found, the "" is there to handle spaces in file names correctly. The command you issue after the- execdir option is terminated with \;

---

### Post by zeltak on 2008-04-03
Hi

Thx for the quick answer!

i am still very new to using the command line so i have a few more questions if thats ok:

from what i understand i issued this command with no sucess:

find /media/thd/128x128 -name "<png>" -execdir mogrify -resize 16x16 "{}"  \;

1)the path to the png files inside the dirs is :  /media/thd/128x128 
is that part ok?

2)what is -name "<filemask>"
is it the file type? i wrote as you see above png

3) i tested this command on one file and it worked (mogrify -resize 16x16) can i use this instead of convert? (mogrify replaces the files themself).

thank you for your patience and sorry for my  CLI ignorance

Zeltak

---

### Post by ibuclaw on 2008-04-03
Try opening up and terminal and type in this:

```

sh
for i in /media/thd/128x128/*.png; do
convert "$i" -resize 16x16 "$i-16"
done
exit

```

convert is part of the imagemagick suite of programs, it converts anything into anything (even txt into pdf) and can apply effects to files too.
Type this in realtime by the way.

Enter in the line and hit enter, then enter in the next line, etc.

I wasn't sure whether or not you wanted the files to overwrite the existing ones, so I added **-16** to the end of them so you know which ones are converted, and which ones are original.

[EDIT]
An alternate way would be to rename the existing files first
```

sh
for i in /media/thd/128x128/*.png; do
mv "$i" "$i-128"
convert "$i-128" -resize 16x16 "$i"
done
exit

```

Or if you aren't bothered about whether or not you want to keep the original, you can use mogrify.
```

sh
for i in /media/thd/128x128/*.png; do
mogrify -resize 16x16 "$i"
done
exit

```

This printed screen is an example of what you can do. I didn't go beyond what you needed, so I just made one file 256x256, one file 16x16 and renamed the original to ".png-48"
The 16x16 images are really blurred though... Is there any reason why you need them in this small size?
It's just that standard size for today's computer needs are usually around 48x48 mark minimum. 
[[IMG]http://img182.imageshack.us/img182/8980/screenshotqg8.th.png[/IMG]](http://img182.imageshack.us/my.php?image=screenshotqg8.png)



Regards
Iain

---

### Post by zeltak on 2008-04-03
Hi

Thanks so much for you info and patience. it works great! (i use the last example with mogrify).

If you dont mind one small question. is there a way to use it recursivley? the reason for that is the icons are in sub folders (apps,places etc...) and i have to run this for each folder under the 128x128 one. can it work for all sub folders? 
also can i put this in a text file and batch it (IE run with ./ or double click it?)

thanks again for all your explanations, its much appreciated!!


Zeltak

---

### Post by vanadium on 2008-04-03
That is why I proposed the find command. The construct "for ... do" works in the current directory only. The find command should look like

find /media/thd/128x128 -name "*.png" -execdir convert "{}"  -resize 16x16 "{}.resized.png" \;

or using mogrify

find /media/thd/128x128 -name "*.png" -execdir mogrify -resize 16x16 "{}" \;

This assumes that "/media/thd/128x128" is your top directory. You could also first make the top directory your current directory, and use "." (current dir) as the directory specifier:

cd /media/thd/128x128
find . -name "*.png" -execdir mogrify -resize 16x16 "{}" \;

---

### Post by zeltak on 2008-04-03
Amazing!

thank you both, you guys saved me hours!!


Zeltak

---

