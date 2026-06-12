---
title: "How does one create a script and run it?"
date: 2015-02-04
forum: General Help
---

### Post by andrewsc0 on 2015-02-04
If I could turn the following commands into a script that I can point at a directory of photos and run it would simplify my life a lot. The problem is I have no idea how writing a script is done and I could use some help. Thanks in advance


```

find . -name '*.NEF' | gawk 'BEGIN{ a=1 }{ printf "mv \"%s\" SubjectName_%04d.NEF\n", $0, a++ }' | bash
mkdir jpgs
mogrify -path Fullpath2/jpgs -format jpg *.NEF
cd Fullpath2/jpgs
mogrify -resize 2048x2048 *.jpg
mogrify *.jpg -gravity center -draw "image over 0,0 0,0 'Fullpath2/Watermark.tif'" *.jpg

```


(obviously SubjectName and Fullpath2 need to be replaced as needed.)

---

### Post by lukeiamyourfather on 2015-02-04
That ***is*** a script. Put it into a text file and save it. Add execute permission to the file. Run the file with "bash myscript" or whatever you call your script. If you want to simply call it directly and not have to specify that it's bash add this line to the top of the script file which identifies what kind of script it is.

```

#!/bin/bash
```

That line is called the shebang.

[http://en.wikipedia.org/wiki/Shebang_%28Unix%29](http://en.wikipedia.org/wiki/Shebang_%28Unix%29)

---

### Post by lukeiamyourfather on 2015-02-04
Forgot about the varibales. For the "Fullpath2" you can use something like $OUTPUT and just define that before you run the script. Same for "SubjectName" it could be $SUBJECT or something like that. Set them from the terminal the script will be run in like this.

```
export OUTPUT="/media/whatever"
export SUBJECT="kittens"
```

---

### Post by andrewsc0 on 2015-02-04
Oh wow I had no idea I was this close! Thanks!

So I have done what you said, I created a file I called imagescript.txt that is currently on my desktop. It contains 
```

#!/bin/bash

find . -name '*.NEF' | gawk 'BEGIN{ a=1 }{ printf "mv \"%s\" SubjectName_%04d.NEF\n", $0, a++ }' | bash
mkdir jpgs
mogrify -path Fullpath2/jpgs -format jpg *.NEF
cd Fullpath2/jpgs
mogrify -resize 2048x2048 *.jpg
mogrify *.jpg -gravity center -draw "image over 0,0 0,0 'Fullpath2/Watermark.tif'" *.jpg

```

I changed it to allow executing as a program, 

if I wanted to point it at a folder also on my desktop called say photos, how would I run it?
does the script have to be in the folder?

I'm not sure what to type beside imagescript.txt?

---

### Post by lukeiamyourfather on 2015-02-04
If it has the shebang and it's executable you would just type the path to the script and hit enter. Typically shell scripts are titled with a "sh" extension but it'll work regardless of what the file is titled. If there's no shebang or you want to manually specify what kind of script it is you need to call the shell first, for example bash scripts can be called like this.

```
bash ~/scripts/myscript
```

---

### Post by andrewsc0 on 2015-02-04
Ok so that didn't work...

I just renamed every NEF file on my computer and moved it to the home folder. (which undid a lot ,and I mean a lot, of editing) 

So...

---

### Post by lukeiamyourfather on 2015-02-04
The "find" command is looking for NEF files in the location that the script is run. That's what the period means, the period means ***this*** directory. You'll probably want to change that to something else specified by a variable. Or be very careful about where you run the script. Maybe add a sanity check if the script is run from a questionable location like the home folder.

Scripting aside you might want to make a backup of things in general if you haven't already. Someone could steal the computer, there could be a fire, or you could be simply testing a shell script that inadvertently does something naughty.

---

### Post by andrewsc0 on 2015-02-04
I do traditionally back up my files. To give you an idea of the volume of shots i take 1700 of the 4800 photos that just got renamed and all thrown into one folder together were taken this weekend. And another couple hundred have been taken since then.

Thanks for your help, but I have to reorganize these photos (and likely redo six or so hours of photo selection) before I consider trying this scripting thing again.. but now I'm thinking perhaps I'll just go line by line.  and maybe have a drink.

---

### Post by Holger_Gehrke on 2015-02-04
> **andrewsc0 said:**
> I do traditionally back up my files. To give you an idea of the volume of shots i take 1700 of the 4800 photos that just got renamed and all thrown into one folder together were taken this weekend. And another couple hundred have been taken since then.

Thanks for your help, but I have to reorganize these photos (and likely redo six or so hours of photo selection) before I consider trying this scripting thing again.. but now I'm thinking perhaps I'll just go line by line.  and maybe have a drink.

Ouch ! Should have spoken up sooner ... **ALWAYS** replace commands that can do damage with echo - or something else that's harmless - while developing scripts. In this case, obviously, the redirection into the bash should have been replaced with one into 'less'.

Here's my variant on your script, it uses command line parameters for the source directory, the subject name and the target directory and exits if source or target are not directories. Obviously this variant needs to be called from a shell, it's difficult to give multiple parameters to a script otherwise. Just as obviously you should carefully check it for any stupid mistakes I might have made ...

```

#!/bin/bash

# $1 - Start Path
# $2 - Subject Name
# $3 - Target path

source=$1
subject=$2
target=$3

if [ "$1" = "" ] ; then
    cat <<EOF
$0 moves NEF files from a source directory tree to a target directory, converts them to jpg and watermarks them.
It needs three parameters: the directory to start searching for NEF files, the subject name for renaming the files and the target directory.
EOF
    exit
fi

if [ !  -d "$source" ] ; then
   echo $source is not a directory
   exit
fi

if [ ! -d "$target"  ] ; then
   echo $target is not a directory; 
   exit
fi


# use process substitution to a file descriptor instead of the awk / bash combo
# just because and because I dislike awk
exec 9< <(find "$source" -iname '*.NEF')
nr=1;
while read file <&9 ; do
    mv "$file" "$target"/"${subject}_${nr}.NEF"
    nr=$((nr+1))
done

# is there a directory jpgs in the target dir ? if not, create it
test -d "$target/jpgs"||mkdir "$target/jpgs"

mogrify -path "$target/jpgs" -format jpg *.NEF
cd "$target/jpgs"
mogrify -resize 2048x2048 *.jpg

# The path to the watermark needs to be inserted here
mogrify *.jpg -gravity center -draw "image over 0,0 0,0 'Watermark.tif'" *.jpg

# return to the previous working directory
cd -

```

---

