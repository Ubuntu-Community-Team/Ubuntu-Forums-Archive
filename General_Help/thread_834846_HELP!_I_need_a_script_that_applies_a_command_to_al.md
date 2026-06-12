---
title: "HELP! I need a script that applies a command to all files in a directory"
date: 2008-06-19
forum: General Help
---

### Post by linkunderscore on 2008-06-19
and i have no idea where to start. The command I want to apply to an entire directory is this:

```
 convert blank.svg -fill '#262729' -fuzz 62%  -draw 'color 65,5 floodfill' blankfinal.png
```

Its designed to remove an annoying border that was placed on an icon set I like. 

So it needs to read all of the *.svg files and run the command and output them preferably in a different directory as *.png files. 


Where do I start?

---

### Post by oarion7 on 2008-06-19
Or you could just edit and then reinstall the icon set, couldn't you? Not sure.

---

### Post by linkunderscore on 2008-06-19
> **oarion7 said:**
> Or you could just edit and then reinstall the icon set, couldn't you? Not sure.

i am trying to batch edit over 60 images. I don't wanna do it by hand. I want to automate it.

---

### Post by johnl on 2008-06-19
You probably want to use a shell script, along the lines of (untested)

```

#!/bin/bash


indir=/where/to/find/files
outdir=/where/to/put/files

find "$indir" -type f -name "*.svg" -print |
while read file; do
	output=$(basename "$file" ".svg") 
	convert "$file" -fill '#262729' -fuzz 62%  -draw 'color 65,5 floodfill' "$outdir/$output.png"
done


```

---

### Post by linkunderscore on 2008-06-19
```
#!/bin/sh



for i in *
do
 
 convert $i -fill '#262729' -fuzz 62%  -draw 'color 65,5 floodfill' $i.png
 
done

```

That does what i need it to do BUT the output files retain the former extension 

IE

test.svg -> test.svg.png

---

### Post by johnl on 2008-06-19
Take a look at the "basename" command that I used in the above post :)

> echo $(basename "foo.svg" ".svg").png
foo.png

---

### Post by linkunderscore on 2008-06-19
wut

---

### Post by oarion7 on 2008-06-19
> **linkunderscore said:**
> i am trying to batch edit over 60 images. I don't wanna do it by hand. I want to automate it.

oh, ok, I reread your first post, I'd misunderstood

---

### Post by linkunderscore on 2008-06-19
sweet now im going to bed 

```
#!/bin/sh



for i in *
do
 
 convert $i -fill '#262729' -fuzz 62%  -draw 'color 65,5 floodfill' ~/Desktop/testfolder2/`basename $i .svg`.png

done




```

---

### Post by kaibob on 2008-06-20
Glad you got things working well. 

Just as a point of information, you can use the mogrify command to do the same thing, and it does not overwrite the original file if the image format is changed. 

For example, the following command sucessfully converted PNG files in my ~/screenshots directory to TIF format and placed them in my ~/images directory. 

```
mogrify -format tif -path /home/kaibob/images /home/kaibob/screenshots/*.png
```

Convert and mogrify perform most of the same conversions, so I assume (but have not checked) that the additional options you require would work.

---

