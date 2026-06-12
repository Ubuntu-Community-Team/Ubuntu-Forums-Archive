---
title: "Rename ogg files depending on stream type"
date: 2018-09-25
forum: General Help
---

### Post by alanwalterthomas on 2018-09-25
I have many .ogg files in nested directories that contain both vorbis and opus streams. I need to change the extension of all files that in fact contain opus data to .opus. I need to do that because Clementine doesn't recognize opus data if the file has a .ogg extension.

My cli-fu is not up to the task. I'd try with ffprobe and grep, but that doesn't work for some reason. I'd prefer a bash or zsh solution.

Thanks

---

### Post by HermanAB on 2018-09-25
There is a utility called 'file' that can identify file types.

---

### Post by alanwalterthomas on 2018-09-27
Thanks, the file utility (almost) does what I need.

I read a few select sections of a bash manual and put together the following code: (warning: total shell script amateur)

```

#!/bin/zsh
#This script should be run after downloading audio with mpsyt
#(in the folder to which the files were downloaded)
#Plan:
#Find all files that are webm, or mka (ignore m4a which is ALAC)
#Determine stream type
#Extract audio using ffmpeg
#Change Extension
find . -type f -iname "*.webm" -o -iname "*.mka" | while read line; do
    FILEBASENAME=${line%.*}
    EXTRACT=true
    CONVERT=false
    if file $line | grep "AAC"; then
        EXT=".aac"
    elif file $line | grep "Opus audio"; then
        EXT=".opus"
    elif file $line | grep "Audio file with ID3 version 2.3.0"; then
        EXT=".mp3"
    elif file $line | grep "Vorbis audio"; then
        EXT=".ogg"
    elif file $line | grep "WebM"; then
        EXT=".ogg"
    else
        EXTRACT=false
    fi
    if $EXTRACT; then
        ffmpeg -i "${line}" -hide_banner -loglevel fatal -acodec: copy -vn -y $FILEBASENAME$EXT
        echo $FILEBASENAME$EXT
        rm $line
    fi
done

```

It mostly does what I want it to do, except it won't work on all files at once. I run it, it works on several files. Run it again, it works on some more, but not all at once.
Why won't this script process all files in one go?

Also...
```

$ file myfile.webm
myfile.webm: WebM

```
will only return "WebM" if it's a webm instead of telling me what sort of stream it contains (e.g. opus, vorbis).

BTW, this is to process music downloaded from youtube by using mpsyt.

---

### Post by HermanAB on 2018-09-27
If a script errors out, then it can be hard to tell what is going wrong.  You have to check the return codes of every program that is invoked.  You should also put quotes around every variable, to handle unexpected funny characters.

The $? variable is set to the return code of the last executed command.

So after a grep, you do something like:
if [ "$?" -ne "0" ]; then
  echo "Error 1"
  exit 1
fi

Increment the number for each check, so you can see which one was caught.

---

### Post by alanwalterthomas on 2018-09-27
Thanks, I changed each $line to "$line", and added the test for an error with $?, but I'm still having problems.

My script isn't generating any errors, but I did notice this after I added this line within the 'else' block: 
```

echo "NoOp on ""${line}"
echo "$line"

```

The output is:
```

./Asrai - Your hands so cold.webm: WebM
./Asrai - Your hands so cold.ogg
NoOp on rai - Lost.webm
rai - Lost.webm
./Asrai - Something I Said.webm: WebM
./Asrai - Something I Said.ogg
NoOp on ai - Roses.webm
ai - Roses.webm

```

For some reason the shell is 'dropping' the first characters. The actual filenames begin with 'Asrai', not 'rai' or 'ai'.
I've checked that the first word of the filename is byte-for-byte identical, so I'm don't think I'm dealing with funny characters.
I've tried changing read to read -r but that didn't help.
A little more testing shows that the $line variable sometimes drops its first characters as soon as it's read (just after while read line).

Why might that be, and how to fix it?

---

### Post by alanwalterthomas on 2018-09-28
Found a solution:
Replace the ```
 find ... | while read -r line; do 
``` with
```

for line in **/*(.); do
FILEBASENAME=${line%.*}
ORIGINALEXT=${line##*.}
EXTRACT=false
if [ $ORIGINALEXT = "webm" ] || [ $ORIGINALEXT = "mka" ]; then
    EXTRACT=true
fi
...
```

Does what I need it to do, but I still don't know why the original method didn't work. I'd like to know.

---

### Post by HermanAB on 2018-09-28
In my experience the 'read' function has many weird 'features'.  They are not 'bugs', since they are all documented in the man page.

So, I avoid using it, or as someone said: It should not be lightly discarded.  It should be thrown.  With great force.

---

