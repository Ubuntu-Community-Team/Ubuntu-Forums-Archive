---
title: "mv files based on first 5 characters and mkdir based on the complete filename before"
date: 2014-11-06
forum: General Help
---

### Post by rjrjrj9er on 2014-11-06
Hi,

I have been trying to work out how to move 1000's of files into folders based on wildcards to no avail.

Also make the folder if not already created.

example..

move 2ABHM15BZ_002.jpg --> to  ./2ABHM15BZ/
move 2ABHM15BZ_010.jpg --> to  ./2ABHM15BZ/

move TGBHM18BZ_002.jpg --> to ./TGBHM18BZ/
move TGBHM18BZ_002.jpg --> to ./TGBHM18BZ/

-RJ

---

### Post by ringstaart on 2014-11-06
Here's a not very elegant way to make this work. It will work as long as you have only the files you want to sort in the directory, and nothing else, and all the identifiers are 9 characters long. If that's not true, tell me and I'll fix it.

I'm assuming that you have basic terminal experience. Run the following from the directory with the files:

```
for i in $( ls | cut -c-9 ); do
mkdir $i
mv $i* $i/
done
```

This will throw some errors, because it will try to create directories that already exist, and tries to move directories into themselves, but it should work.

You might want to back up the folder first, if that isn't too much trouble, because it's kind of ugly. If you can't back it up, do a test run on a few of the files copied over somewhere else.

---

### Post by rjrjrj9er on 2014-11-06
Hi,

It works perfect, but as you mentioned it works for 9 characters long. I see that in the cut option the 9 I can change that for each but if it is 8 or 6 or 3 characters only before the _ it will create a folder or the first 9 characters.

Can I also add something after the _ like [COLOR=#000000]move TGBHM18BZ_002.jpg --> to ./TGBHM18BZ_JPEGS/

[/COLOR]I tried 

mkdir '$i_JPEGS' 
mv $i '$i_JPEGS/'

but that did not work. 

Thanks,
Rich

---

### Post by rjrjrj9er on 2014-11-06
Hi, I worked out the _JPEGS option I used "$i"_JPEGS instead of the '$i_JPEGS"...

---

### Post by rjrjrj9er on 2014-11-06
also if it could ls *.jpg and then do a cut as I will have TIFFs as well and it should mv them to appropriate TIFF and JPG folders.

-R

---

### Post by Vaphell on 2014-11-06
[B]never use stuff like this

for i in $( ls | cut -c-9 )
[/B]
1. running *for* on command outputs is wrong and brittle, just see what happens if there is space in the name
2. ls is unreliable

```
for f in *_*.{jpg,tiff}
do
    ext=${f##*.}
    d="${f%_*}_${ext^^}S"
    mkdir -p "$d"
    mv "$f" "$d"
done
```

---

### Post by matt_symes on 2014-11-06
Hi

I would be tempted to use bash parameter expansion to do this.

```
for i in *; do  [[ -f "$i" ]] && { j=${i%_*}; [[ ! -e "$j" ]] && mkdir "$j"; mv "$i" "$j"; } done;
```

An explanation of the above command line.

```
for i in *;
``` 

will list all the files in a directory safely using globbing. 

```
[[ -f "$i" ]]
```

will check if the directory entry is a file and not a directory, symlink or other special file.

```
j=${i%_*}
```

This will extact everything before the _ into the variable j. ie if i == 2ABHM15BZ_002.jpg then j == 2ABHM15BZ.

```
[[ ! -e "$j" ]] && mkdir "$j"
```

This will test if the directory exists and if not it will make it.

```
mv "$i" "$j"
```

This will move the file into the directory.

You can edit the one liner until it does what you need but, be aware, it's untested so **test it first, **however it should work; maybe with a bit of tweaking for your use case.

**EDIT:**

Beaten to it :)

Kind regards

---

### Post by rjrjrj9er on 2014-11-06
Hi Vaphell, I am receiving this error

line 4: ${f%_*}_${ext^^}S: bad substitution

-R

---

### Post by Vaphell on 2014-11-06
are you using bash to run the script?

put **#!/bin/bash **in the very first line and don't override that default by calling the script with explicit sh (sh script)

---

### Post by rjrjrj9er on 2014-11-06
Yes.

---

### Post by Vaphell on 2014-11-06
copypaste from terminal plz


```
#!/bin/bash

# create test files
touch {omg,wtf,bbq}_00{1,2}.{jpg,tiff}

for f in *_*.{jpg,tiff}
do
    ext=${f##*.}
    d="${f%_*}_${ext^^}S"
    mkdir -p "$d"
    mv "$f" "$d"
done

# show results
tree
```

```
$ ./sort_crap.sh 
.
&#9500;&#9472;&#9472; bbq_JPGS
&#9474;** &#9500;&#9472;&#9472; bbq_001.jpg
&#9474;** &#9492;&#9472;&#9472; bbq_002.jpg
&#9500;&#9472;&#9472; bbq_TIFFS
&#9474;** &#9500;&#9472;&#9472; bbq_001.tiff
&#9474;** &#9492;&#9472;&#9472; bbq_002.tiff
&#9500;&#9472;&#9472; omg_JPGS
&#9474;** &#9500;&#9472;&#9472; omg_001.jpg
&#9474;** &#9492;&#9472;&#9472; omg_002.jpg
&#9500;&#9472;&#9472; omg_TIFFS
&#9474;** &#9500;&#9472;&#9472; omg_001.tiff
&#9474;** &#9492;&#9472;&#9472; omg_002.tiff
&#9500;&#9472;&#9472; sort_crap.sh
&#9500;&#9472;&#9472; wtf_JPGS
&#9474;** &#9500;&#9472;&#9472; wtf_001.jpg
&#9474;** &#9492;&#9472;&#9472; wtf_002.jpg
&#9492;&#9472;&#9472; wtf_TIFFS
    &#9500;&#9472;&#9472; wtf_001.tiff
    &#9492;&#9472;&#9472; wtf_002.tiff
```

---

### Post by rjrjrj9er on 2014-11-06
#!/bin/bash


for f in *_*.{jpg,tiff}
do
    ext=${f##*.}
    d="${f%_*}_${ext^^}S"
    mkdir -p "$d"
    mv "$f" "$d"
done

---

### Post by rjrjrj9er on 2014-11-06
blah4.sh: line 9: ${f%_*}_${ext^^}S: bad substitution
blah4.sh: line 12: tree: command not found

---

### Post by Vaphell on 2014-11-06
how do you call your script, by *./blah4.sh*?

*sudo apt-get install tree* (it's a nonstandard command that's not necessary but i used it here to visualize the results)
also use [noparse]```

```[/noparse] tags

---

### Post by rjrjrj9er on 2014-11-06
I've called it via 

./blah4.sh
sh blah4.sh
bash blah4.sh

---

### Post by Vaphell on 2014-11-06
*./blah4.sh* and *bash blah4.sh* should work :/
hm, what's your bash version then, *bash --version*

i think your shell complains about ${var^^} expansion which is var in ALL-CAPS
verify by echoing some var with ^^, eg *echo ${HOME^^}*

---

