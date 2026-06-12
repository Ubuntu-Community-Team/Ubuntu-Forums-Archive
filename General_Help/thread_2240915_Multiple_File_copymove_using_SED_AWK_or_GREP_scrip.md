---
title: "Multiple File copy/move using SED AWK or GREP script using text file as list"
date: 2014-08-23
forum: General Help
---

### Post by Heinrich_Evers on 2014-08-23
Does anyone know of a console command that I can use to search a text file that has nothing but filenames in it, then take the names from the text file and perform a multi-file copy from one directory to another?

all of the files that will be in this text file are in one folder but what I'd like to do is only copy the files that are listed in the text file to the new directory.

I'm trying to sort out a ton of stuff that was saved into a single folder for a period of 3 years so manually going through it and multi-selecting stuff would take days.

I have the list in a text file of the stuff that needs to be copied or moved and I have a few text files created for these lists.

I'd do it  by file extension; however, there are files with the same extension that I don't want to move so it has to be done by the exact filename.


Any suggestions?

---

### Post by nerdtron on 2014-08-23
Put an example of what you want to do.

---

### Post by sotiris2 on 2014-08-23
Is the list in the 'format' of one filename per line? Are all filenames in the same list to be copied to the same directory?

EDIT: filename per LINE not file :p

---

### Post by sotiris2 on 2014-08-23
Well presuming one filename per line in the list I made the following script. Don't use it if the list is not formatted like that. 

```
#!/bin/bash -x
while read 
do
    mv ./"$REPLY" "$2"
done < $1
[code]

Its made to be invoked from the same folder as the files (as I understand the list contains only the file's name not the full path) and you do
[code]script list targetdirectory
```

---

### Post by Heinrich_Evers on 2014-08-24
Yes the list is one filename per line.

Thank you for the help, I'll try it out when I get some free time from my schoolwork. The file list only contains the filenames, no location as it is indeed in the same folder as the files. So let me get this right, the read command will be followed by the text file that contains the filenames and will then move them into the $REPLY folder which I would change to be the file path that I want to move the files to?

---

### Post by sotiris2 on 2014-08-24
No you will save this to a file and make it executable. You will put it in the folder with the files and run with two arguments. #1 will be the list and number two the directory you want things to go to. $REPLY holds the name of a file read from your list so that it is passed to the mv command.

---

### Post by steeldriver on 2014-08-24
If this is just a "one-off" you don't really need to save it as a script imho - a one-liner like

[NB I have left an [COLOR=#808080]echo[/COLOR] in each of these commands so as written they just print out what they would do, without actually doing it - so that you can verify it's what you really want first. Remove the echo once you're confident nothing is going to screw up / get overwritten.]

```

while read -r file; do [COLOR=#808080]echo[/COLOR] mv -vt path/to/newdir/ "$file"; done < filelist.txt

```

or even

```

cat filelist.txt | xargs -I{} [COLOR=#808080]echo[/COLOR] mv -vt path/to/newdir/ "{}"

```

should do the trick. The 'v' (verbose) argument is optional - just gives you visual feedback of the moves.

---

### Post by Heinrich_Evers on 2014-09-07
> **steeldriver said:**
> If this is just a "one-off" you don't really need to save it as a script imho - a one-liner like

[NB I have left an [COLOR=#808080]echo[/COLOR] in each of these commands so as written they just print out what they would do, without actually doing it - so that you can verify it's what you really want first. Remove the echo once you're confident nothing is going to screw up / get overwritten.]

```

while read -r file; do [COLOR=#808080]echo[/COLOR] mv -vt path/to/newdir/ "$file"; done < filelist.txt

```

or even

```

cat filelist.txt | xargs -I{} [COLOR=#808080]echo[/COLOR] mv -vt path/to/newdir/ "{}"

```



should do the trick. The 'v' (verbose) argument is optional - just gives you visual feedback of the moves.


Thank you! You've been extremly helpful man.

---

### Post by SeijiSensei on 2014-09-07
I'd just use rsync with --include-from pointing to the list of filenames.

```
sudo rsync -av --include-from=/path/to/filelist /path/to/destination/directory
```

---

