---
title: "How can I batch convert images to b/w while preserving the folder structure"
date: 2013-05-10
forum: General Help
---

### Post by Chelidze on 2013-05-10
[COLOR=#333333][FONT=Ubuntu Beta]I want to batch process images but I have a very specific task that I want to do[/FONT][/COLOR]

[LIST=1]
[*]I do not want to change image type
[*]I want to make them black and white
[*]I want it to create/preserve images and sub folder structure
[/LIST]

 what I mean by 3

what I want is this for example main folder "F1" contains 4 different sub folders "2003" "2004" "2005" and "2006" and all of this sub folders Constantine 100-120 files 
 so what I want is the new black and white files have the same structure as they where I do not care if it will overwrite or create a new folder all I care is them to be black and white and  be in the same folders as they were for example if williams 2003.png was in "2003" I want the new file to be in "2003" as well



[COLOR=#333333][FONT=Ubuntu Beta]I did this in Photoshop but it did not preserve folders and sub folder content it just threw every converted file in one directory.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]My only hope is Linux :D[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Thank you in advance![/FONT][/COLOR]

---

### Post by agillator on 2013-05-10
Look at ImageMagik's convert utility. If you are dealing with images I suspect you really want 'grayscale', not 'pure black and white'. The general form of the command would be 'convert <input> -colorspace Gray <output>. Of course it can be a whole lot more complicated if you wish, and batch processing is also possible. See the ImageMagick web site for more detailed instructions and example commands. You might have to do each directory separately, I'm not sure of that, but I do know you can batch process and entire directory and put the results anywhere you wish.

---

### Post by Chelidze on 2013-05-10
Here is the solution 

```
[FONT=Ubuntu Mono]for img in $(find . -iname '*.png'); do echo -n "Converting $img"; convert -colorspace GRAY $img $img && echo ' [Done]'; done[/FONT]
```

[http://askubuntu.com/a/293713/42591](http://askubuntu.com/a/293713/42591)


thank you **[COLOR=#000000][agillator]("http://ubuntuforums.org/member.php?u=1420584") I will give that a shot as well[/COLOR]**

---

### Post by Vaphell on 2013-05-10
```
#!/bin/bash

# source and destination dirs
srcdir="$HOME/source"  
destdir="$HOME/grayscale"

while read -rd $'\0' f
do
  echo "$f"
  fdir=${f%/*}
  mkdir -p "${fdir/#$srcdir/$destdir}"
  convert "$f" -set colorspace Gray -separate -average "${f/#$srcdir/$destdir}"
done < <( find "$srcdir" -regextype posix-extended -iregex '.*(png|bmp|jpe?g|tga|gif|tiff)$' -print0 )
```

your solution sort of sucks because it will fail in case of space-filled filenames (never do this: *for x in <output of some command>*) and it does only PNGs
Also it's not too safe to perform irreversible operations, it's too easy to damage/destroy original data.

---

### Post by Chelidze on 2013-05-10
> **Vaphell said:**
> ```
#!/bin/bash

# source and destination dirs
srcdir="$HOME/source"  
destdir="$HOME/grayscale"

while read -rd $'\0' f
do
  echo "$f"
  fdir=${f%/*}
  mkdir -p "${fdir/#$srcdir/$destdir}"
  convert "$f" -set colorspace Gray -separate -average "${f/#$srcdir/$destdir}"
done < <( find "$srcdir" -regextype posix-extended -iregex '.*(png|bmp|jpe?g|tga|gif|tiff)$' -print0 )
```

your solution sort of sucks because it will fail in case of space-filled filenames and it does only PNGs
Also it's not too safe to perform irreversible operations, it's too easy to damage/destroy original data.


 Honestly I have no idea if that is a god solution or a bad one I am not that good in linux 

I the solution I provided is not mine I linked the askubuntu page where that person helped me solve my problem and my I wanted to convert png files you can see there but if you tell me how to use your commend that will be a blast

---

### Post by sisco311 on 2013-05-10
Please check out BashPitfalls 001 (link in my signature). That command will fail if the files/directories have white spaces in their names.

You could use the -execdir action of the GNU/find command:
```
find ./path/to/dir -iname '*.png' -type f -execdir sh -c 'convert -colorspace GRAY $1 $1' _ {} \;
```
If you don't want to overwrite the original files, then try something like:
```
find ./path/to/dir -iname '*.png' -type f -execdir sh -c 'convert -colorspace GRAY $1 ${1%.???}.bw.png' _ {} \;
```

---

### Post by Chelidze on 2013-05-10
> **sisco311 said:**
> Please check out BashPitfalls 001 (link in my signature). That command will fail if the files/directories have white spaces in their names.

You could use the -execdir action of the GNU/find command:
```
find ./path/to/dir -iname '*.png' -type f -execdir sh -c 'convert -colorspace GRAY $1 $1' _ {} \;
```
If you don't want to overwrite the original files, then try something like:
```
find ./path/to/dir -iname '*.png' -type f -execdir sh -c 'convert -colorspace GRAY $1 ${1%.???}.bw.png' _ {} \;
```


wow you people are like mad scientists, you do waowowa and write some commends :) and the result is awesome one question your second commend will it create a saperate directory or in the original directory after the process will be done I will have the original file and the black and white file ??

---

### Post by Vaphell on 2013-05-10
if i read it correctly it will create a bw copy next to the original file
my script does separate dir with recreated structure, at least in theory (worked fine on my test files).

you simply save the code as a text file named as you wish
and then run it with *bash file*
or if you made the file executable with *chmod +x file* :  *./file*

---

### Post by Chelidze on 2013-05-10
> **Vaphell said:**
> if i read it correctly it will create a copy next to the original file
my script does separate dir with recreated structure, at least in theory.

I really do not want to bother you with a question like this, but I am relatively new ubuntu user 

should I "cd" in the maine directory and then past you commend in the terminal 
This full thing I am asking because I never seen such a commend befor :) it is tall commends that I have used were alwates long not tall 

#!/bin/bash# source and destination dirssrcdir="$HOME/source"  destdir="$HOME/grayscale"while read -rd $'\0' fdo  echo "$f"  fdir=${f%/*}  mkdir -p "${fdir/#$srcdir/$destdir}"  convert "$f" -set colorspace Gray -separate -average "${f/#$srcdir/$destdir}"done < <( find "$srcdir" -regextype posix-extended -iregex '.*(png|bmp|jpe?g|tga|gif|tiff)$' -print0 )

---

### Post by Vaphell on 2013-05-10
i updated my earlier post but i'll repeat myself
the code is a script, you need to save the code as a text file, just paste it into text editor and save
and then run the script
*bash name_you_have_chosen*
obviously change srcdir and destdir to suit your needs

---

### Post by Chelidze on 2013-05-10
> **Vaphell said:**
> i updated my earlier post but i'll repeat myself
the code is a script, you need to save the code as a text file, just paste it into text editor and save
and then run the script
*bash name_you_have_chosen*
obviously change srcdir and destdir to suit your needs

 now you most defensibly think I am an idiot but this is the first time I am using a script 

if my folder that I want to convert is here 

'/home/levan/Desktop/F1'

and 

I want to out put it to here /home

what do I write
 
```
srcdir= I write '/home/levan/Desktop/F1' this ??
```

```
destdir= and here I will write this ~ ??
```

---

### Post by Vaphell on 2013-05-10
eg
srcdir=$HOME/Desktop/F1
destdir=$HOME/F1_grayscale
$HOME and ~ are pretty much the same fyi, i suggest adding something to dest ~ to contain results, because the script would get your main dir spammed otherwise (~ would be an equivalent of F1, which means untold amount of subdirs created right there)

---

### Post by Chelidze on 2013-05-10
> **Vaphell said:**
> eg
srcdir=$HOME/Desktop/F1
destdir=$HOME/F1_grayscale
$HOME and ~ are pretty much the same fyi, i suggest adding something to dest ~ to contain results, because the script would get your main dir spammed otherwise (~ would be an equivalent of F1, which means untold amount of subdirs created right there)

 I wanted to do a test before I wold do the real deal so I run this commend and this is what I got 

```
bash '/home/levan/Pictures/Wallpapers/test' /home/levan/Pictures/Wallpapers/test: line 13: unexpected EOF while looking for matching `"'
/home/levan/Pictures/Wallpapers/test: line 14: syntax error: unexpected end of file



```

this is what I wrote 

```
srcdir=home/levan/Pictures/Wallpapers
destdir=home/levan/Pictures/Wallpapers/grayscale"
```

---

### Post by Vaphell on 2013-05-10
something is not right with the file, eg missing ) after -print0?
output of *cat /home/levan/Pictures/Wallpapers/test * ?

and don't put destination dir inside source to avoid feedback loop, you would risk converted files being found as input for another conversion depending on in what order find scans subdirs (1. find finds file X, grayscale version is created in dest subdir, 2. finds gets to discover dest subdir and scans it, 3. file X_grayscale is passed for another conversion but to dest/dest)
That might or might not happen if you run script once, but in case of repeating the script you would get another layer of dest each time (dest, dest/dest, dest/dest/dest, ...)

ok:
/home/levan/Pictures/Wallpapers
/home/levan/Pictures/Wallpapers_grayscale

ambiguous/feedback loop:
/home/levan/Pictures/Wallpapers
/home/levan/Pictures/Wallpapers/grayscale

---

### Post by Chelidze on 2013-05-10
> **Vaphell said:**
> something is not right with the file, eg missing ) after -print0?
output of *cat /home/levan/Pictures/Wallpapers/test * ?

and don't put destination dir inside source, you would risk converted files being found as input for conversion

ok:
/home/levan/Pictures/Wallpapers
/home/levan/Pictures/Wallpapers_grayscale
ambiguous:
/home/levan/Pictures/Wallpapers
/home/levan/Pictures/Wallpapers/grayscale


 Wow it worked :) awesome 

I had " things messed up 

```
#!/bin/bash

# source and destination dirs
srcdir='/home/levan/Pictures/Wallpapers'
destdir='/home/levan/Pictures/Wallpapers/grayscale'


while read -rd $'\0' f
do
  echo "$f"
  fdir=${f%/*}
  mkdir -p "${fdir/#$srcdir/$destdir}"
  convert "$f" -set colorspace Gray -separate -average "${f/#$srcdir/$destdir}"
done < <( find "$srcdir" -regextype posix-extended -iregex '.*(png|bmp|jpe?g|tga|gif|tiff)$' -print0 )
```

did this and it worked awesome 

thank you now I know -ish how to work with bash files 

thanks to you thank you again

---

### Post by Vaphell on 2013-05-10
really put the dest outside src, if you would run the script again you would get Wallpapers/grayscale/grayscale (original grayscale is treated as an input and gets its own subdir in itself), another run another layer

---

### Post by Chelidze on 2013-05-10
> **Vaphell said:**
> really put the dest outside src, if you would run the script again you would get Wallpapers/grayscale/grayscale (original grayscale is treated as an input and gets its own subdir in itself), another run another layer

ooo ok thanks again

---

