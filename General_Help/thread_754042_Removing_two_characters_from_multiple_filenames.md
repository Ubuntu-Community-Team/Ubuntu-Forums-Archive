---
title: "Removing two characters from multiple filenames"
date: 2008-04-13
forum: General Help
---

### Post by zorkerz on 2008-04-13
I have 1830 files that all have ';1' after their extension (ie 'README.TXT;1'. I would like to remove the ;1 from every filename so the extensions are recognized properly. 

Does anyone know a way to do this?

I have been trying to use purrr but have not figured out an appropriate template syntax.

---

### Post by Belboz99 on 2008-04-13
What you need is a script...


If you want to rename a file, the command is mv, short for move.   

I'm not that great with scripting these days though, it's been a few years since I've taken that course in college.

If you want to read up on it, there's a bunch of scripting how-to's on Google.    The keywords you want to search for are "bash scripting".   Bash is the Bourne Again Shell, IIRC.


Anyway, I wouldn't just pop this in your terminal, but the code would look something like this:


for EACH in *.1
do
*some command that moves the file to the same location but without the .1 on the file name*
done

It has to do with for loops, probably putting the current file name into a variable, cutting the .1 from the variable with the cut command, and then moving the file to the variable's name.

I might look into this some more if you need more help.

Here's the introductory how-to for bash scripting:

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)


Dan

---

### Post by ghostdog74 on 2008-04-13
```

#!/bin/bash
cd /your/path
for files in *";1"; do mv "$files" ${files/;1/} ; done

```

save as script.sh and run the script on the terminal
```

# chmod u+x script.sh
# ./script.sh

```

---

### Post by zorkerz on 2008-04-13
wow so i know so little about this. thanks for the responses.

all of the files are in /home/ninor/Desktop/risk/ and its subdirectories. How do i modify ghostdog74's script to look here. 

I don't even know how to run a script I have put it in a file but then what do i call it with in a terminal or can i just double click it?

Can i just copy the script into a terminal (im not sure it would be called a script anymore but would that work)?

---

### Post by .nedberg on 2008-04-13
Open up a terminal and issue:
```

cd /home/ninor/Desktop/risk/

```
then
```

for files in *";1"; do mv "$files" ${files/;1/} ; done

```

That way you don't get ste script, but it still works at all your files. Ghostdog solved it for you!

---

### Post by koenn on 2008-04-13
```
 
cd /home/ninor/Desktop/risk/
find . -name "*;1" |while read FILE ; do mv "$FILE" ${FILE/;1/} ; done

```

should work on subdirectories as well
test it first in a test directory with some fake files.

---

### Post by zorkerz on 2008-04-13
thankyou all I ended up following koen's instructions.

---

