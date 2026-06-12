---
title: "how to grep recursively for a pattern and open all files that match"
date: 2015-02-18
forum: General Help
---

### Post by dilbert_one on 2015-02-18
hello dear ubuntu-experts


hope you are all right and all goes well 


how to grep recursively for a pattern and open all files that match


these commands do the grep ```


  find . | xargs grep "texthere" *

  grep -r "texthere" .

  grep -r "a target="_blank"" 

  find ./ -type f | xargs grep "foo"


```
but do not open  the file

---

### Post by steeldriver on 2015-02-18
Open? in what application? You could try something like

```

grep -lrZ 'texthere' . | xargs -0 gedit

```
for text files, or
```

grep -lrZ 'texthere' . | xargs -0 -n1 xdg-open

```

I'd probably add -I to the grep as well to prevent it searching binary files.

---

### Post by aromo2 on 2015-02-18
You may not want to open all the files that match.  What would happen if there are just too many?  Instead, I would do:
```
cd / ; grep -rl "foo" . 2>/dev/null
```
and then open the file(s) manually

---

### Post by slickymaster on 2015-02-18
Since it's a support request, I'm moving this one to the **General Help** sub-forum.

---

### Post by haplorrhine on 2015-02-18
> **aromo2 said:**
> You may not want to open all the files that match.  What would happen if there are just too many?
I think they want to "recursively" keep grepping until the list is narrowed down.

I would suggest writing a bash script if newlines were spared while assigning stdout to a variable; they aren't.:(

---

### Post by dilbert_one on 2015-02-18
hello - many many thanks for the great hints. 

you all saved my day

have a great day...too. 

regards

---

### Post by haplorrhine on 2015-02-19
I wanted to try writing my first unique bash script, so I wrote a find + recursive grepper.  As it turns out, you can translate the white space back into newlines quite easily with | tr " " "\n"
I assign to list the output of a subshell $(...) that echos the list, translates the whitespace, then greps it.

```
#! /bin/bash

echo "Enter initial search term, then enter the directory to search."
echo
read term
read dire
list=$(find $dire -iregex .*$term.*)
echo $list | tr " " "\n"
echo
echo "Enter next term, or \"end\" to stop."
read term
echo
until [[ $term == "end" ]];
do[INDENT=2]if [[ $term == "undo" ]]
then list=$list2
echo "Enter alternate term."
echo
[/INDENT]
[INDENT] else list2=$list
list=$(echo $list | tr " " "\n" | grep $term)
echo $list | tr " " "\n"
echo
echo "Enter next term, or \"undo\" or \"end\"."
echo
fi
read term
echo
[/INDENT]
done
```

All you'll have to do is append some commands that open the pathnames listed in $list.  To try the script as is, just save it into a text file, set the file readable/executable (chmod =0555 or =0777), and then run it by entering the path/to/file as a command line.
Note the I used -iregex, the case insensitive version of -regex.

- - - - -

edited:
I liked this script of mine, and decided to add an undo option into the script.

---

