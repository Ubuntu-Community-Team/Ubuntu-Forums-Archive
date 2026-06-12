---
title: "Using pandoc to bulk covert files"
date: 2020-04-10
forum: General Help
---

### Post by steveredshaw on 2020-04-10
I need to bulk convert markdown files to plain text, ie strip all markdown tags from the original files and just leave the plain text.

I can do this for single files;```
pandoc  -f markdown -t plain -o  inputfile.md  outputfile.txt
```
there is the issue of filenames containing spaces which is dealt with by enclosing the file name in single quotes, all good so far but I haven't been able to work out a way to use wildcards to apply this to several files, any suggestions please?

---

### Post by Holger_Gehrke on 2020-04-10
A for-loop is probably the best bet. Something like
```

for i in *md; do pandoc -f markdown -t plain -o "${i%.md}.txt" "$i";done

```
(the ${i%.md} removes the suffix '.md' from the value of i, then the suffix '.txt' gets attached). Double quotes are the right ones to use in these circumstances because we do want parameter substitution to work and it would not work in single quotes.

Holger

---

### Post by steveredshaw on 2020-04-10
;) Thank you so much, that worked a treat - well I'm sure you knew it would! It took less than 5 secs in a folder of 200 md files.

---

### Post by Holger_Gehrke on 2020-04-10
Actually, I didn't know. But I regularly do something very similar (ImageMagick 'convert -resize 168x126 input-file output-file' to produce thumbnail images) and just had to take a look at the manual for pandoc to adapt my usual one liner.

Holger

---

### Post by TheFu on 2020-04-10
```
#!/bin/bash

for i in *md 
do 
   cmd -i "$i" -o "${i%.md}.txt" 
done
```

is a common solution pattern. Worth keeping in any toolbox.  Note the *md line.  That used filename globbing where many people would be tempted to use LIST=`ls *md`.  Using ls is prone to problems. Always best to use bash/shell globbing.

Also, having a script create another script is a common pattern for those times when we aren't 100% certain of the results.
```
#!/bin/bash
for i in *md 
do 
   echo cmd -i \"$i\" -o \"${i%.md}.txt\" 
done
```
will output the commands which can be captured or redirected to another script file.

And having numerical counts can be handy.
```
for N in {01..24} ; do echo "# $N  "; done
```
See how the leading 0 forces 01, 02, 03, 04 .... output?

---

