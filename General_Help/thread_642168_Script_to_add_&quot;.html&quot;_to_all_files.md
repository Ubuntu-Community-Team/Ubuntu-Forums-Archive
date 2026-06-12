---
title: "Script to add &quot;.html&quot; to all files"
date: 2007-12-16
forum: General Help
---

### Post by enchance on 2007-12-16
Can anyone show me the bash script which will take every file in a folder and insert the extension ".html" at the end? I don't know much bash but I do know it will involved piping the results of find to mv -fv. Any bash gurus out there?

---

### Post by graham-cracker on 2007-12-16
This should work, just change the DIR from /var/tmp/foo/ to whatever directory you want to use.

#!/bin/bash

DIR="/var/tmp/foo/"
EXT=".html"
FILES=`ls $DIR`

for FILE in $FILES; do
	mv "$DIR/$FILE" "$DIR/$FILE$EXT"
done

---

### Post by enchance on 2007-12-17
> **graham-cracker said:**
> This should work, just change the DIR from /var/tmp/foo/ to whatever directory you want to use.

#!/bin/bash

DIR="/var/tmp/foo/"
EXT=".html"
FILES=`ls $DIR`

for FILE in $FILES; do
	mv "$DIR/$FILE" "$DIR/$FILE$EXT"
done

Can I replace FILES=`ls $DIR`to FILES=`find...etc` instead? That way I can target the files to change.

---

### Post by tomchuk on 2007-12-17
```

find . -type f -exec mv '{}' '{}.html' \;
```

---

### Post by dagnabit dang doohickey on 2007-12-17
```
find *searchpattern* -type f -exec mv -v {} {}.EXT \;
```

Edit: Eh, its late and I'm slow. tomchuk already took care of it.

---

### Post by enchance on 2007-12-17
> **tomchuk said:**
> ```

find . -type f -exec mv '{}' '{}.html' \;
```

Is there any documentation on using the '{}' with -exec? Also, is -exec better than xargs or is it mainly a preference?

---

### Post by tomchuk on 2007-12-17
{} refers to the output line of file (the file name). Ths single quotes are to ensure that it works with files with funny characters (like spaces) in them. 

In some cases (including this one) xargs is slower that -exec because it spawns an extra process: find + (xargs + mv)*no_files  VS. find + (mv)*no_files. I've found that for large numbers of files, xargs can be faster for things like grepping (where there are too many files to do a shell expansion with grep foo *). Both -exec and xargs will perform some magic so that the number of commands executed is, in many cases, far less than the number of files.

This is how you'd do it with xargs:
```
find . -type f | xargs -I '{}' mv '{}' '{}.html'
```

---

### Post by enchance on 2007-12-17
> **tomchuk said:**
> 
This is how you'd do it with xargs:
```
find . -type f | xargs -I '{}' mv '{}' '{}.html'
```

Ooohhhh, such a wonderful line of bash code. I lav it! Thanks!

---

### Post by floke on 2007-12-17
Couldn't you do a mass rename with Thunar - or is that a stupid idea?

---

### Post by Envy Geek on 2007-12-17
You could also try:
```
rename 's/$/\.html/' *
```
Not a bash script but it works.

~Anthony

---

### Post by enchance on 2007-12-17
This post has been very helpful! But one more question, is it possible to change specific text inside a text file? I'm working with html files and they all have a link to a css file for their formatting. Can I write a bash code which will look inside all these html files and change the path to the css file through find?

So basically, I'm looking to change the src attribute for the css file in all of the html files. Do I use grep or something?

---

### Post by tomchuk on 2007-12-17
Sed will do it.
```
sed -i -e 's|/path/to/old/file\.css|/path/to/new/file.css|' *.html
```

Back up your files first - doing in-place substitutions with sed often has unintended consequences.

---

### Post by HermanAB on 2007-12-17
You can also do that with 'find'.  Find can recurse into directories and execute something on each match.  See the man page for details.

Cheers,

Herman

---

### Post by enchance on 2007-12-17
> **HermanAB said:**
> You can also do that with 'find'.  Find can recurse into directories and execute something on each match.  See the man page for details.
I'm more interested with using find. How do I write it for find? I've never heard of sed before.

---

