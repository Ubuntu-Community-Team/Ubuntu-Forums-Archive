---
title: "Shell script help"
date: 2008-02-29
forum: General Help
---

### Post by nonaguy on 2008-02-29
We are switching over to an Ubuntu environment, and we could use a little help with a simple script. It is a DOS script for using imagemagick:

for /R "I:\Atiz   Imaging\%var%" %%f IN (*.jpg) DO mogrify -compress lzw -format tif "%%f"

 What would be a good shell script to get this command to run in Ubuntu? 
Thank you.

---

### Post by WarMonkey on 2008-02-29
What does the script do? (so that maybe someone who only knows the linux terminal can help)

---

### Post by nonaguy on 2008-03-03
Oh sorry, forgot to add that this was an automated command for imagemagick. This uses the mogrify command to convert a type of image file to another, such as jpeg to tiff.

---

### Post by nonaguy on 2008-03-03
It basically moves to the directory, such as I:Atiz Imageing, calls on all jpegs found in the file, and converts them all to tiffs.

---

### Post by yota on 2008-03-03
Hi,
there is more that one option to do what you need in bash, my two favorite picks are these:
```

ls -1 /path/to/images/*.jpg|while read file
do
   convert $file [options] converted-$file
done

```
or
```

find /path/to/images/ -name '*.jpg' -exec convert {} [options] converted-{} \;

```

the first one is something like this:
redirect (pipe | is the redirect output symbol) the output of ls (-1 means a file per line) to a while loop using "file" as the variable name. The do-done block is executed for every instance of file.

the second is just one command: find. It's quite powerful (and complicated too) see "man find" for details.

in both [options] has to be replaced with opportune options and obiouvsly the command has to be adjusted to your needs.

Hope this helps!

---

### Post by nonaguy on 2008-03-03
Thanks a lot for the help. Here is the command we are using and it works just fine:

ls -1 /path_to_image/*.jpg|sed -e 's/\.[^.]*$//'|while read file
do
	convert $file.jpg {-options} $file.tif
done

---

