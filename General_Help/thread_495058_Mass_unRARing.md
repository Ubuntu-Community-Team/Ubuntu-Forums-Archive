---
title: "Mass unRARing"
date: 2007-07-07
forum: General Help
---

### Post by Sikarian on 2007-07-07
I'm trying to find a way to mass unRAR recursively in a directory.

Example, lets say I've got a folder called A-F.  inside of that folder is more, A, B, C ,D ,E ,F folders.  Each of them have 20-30 .rar files inside of them.

Is there anyway I can tell tar to just go through and extract each rar to it's own folder  (example, ubutunu1.rar extracted to folder  ubuntu1)?

---

### Post by milton1 on 2007-07-07
try this: ```
 unrar -r <filename> 
```

Edit: This assumes you have the unrar package installed

---

### Post by phidia on 2007-07-07
I think this would be a good use for a shell script. you would call the unpacker and then make a new directory (mkdir) and move the unpacked file to it. I'm no great scripter though but there are resources out there [http://linuxgazette.net/133/cherian.html](http://linuxgazette.net/133/cherian.html)  [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

I can't think of another way to do what you want.

---

### Post by Sikarian on 2007-07-07
That doesn't work :(  It just spits out the help report.

I tried say unrar x -r   (x being Extract files with full path) and I get No files to extract.

Same with trying unrar e    Extract files to current directory.

---

### Post by Sikarian on 2007-07-08
Anyone good at writing scripts mind real quickly jotting something up?  I'm absolutely terrible at this kinda stuff :(

---

### Post by Lakefall on 2007-07-08
Well, for a start this should unrar every rar in the directory you are in:
```
for name in *.rar; do unrar x $name; done
```
Note that you may press enter instead of writing ";" if you want to.

If you want to create directories where you extract to do something like this instead:
```
for name in *.rar; do mkdir $name-dir; cd $name-dir; unrar x $name; cd ..; done
```
or
```
for name in *.rar; do mkdir $name-dir; (cd $name-dir; unrar x $name); done
```

If you want to be recursive, try something like this:
```
for name in `find . -iname \*.rar`; do unrar x $name; done
```
or
```
for name in $(find . -iname \*.rar); do unrar x $name; done
```
This extracts the rars in the current directory though...

Of course you can combine these:
```
for name in $(find . -iname \*.rar); do mkdir $name-dir; (cd $name-dir; unrar x $name); done
```
If you want to actually extract the rars below the directories they are in, this starts to get a bit complicated. We would need to take the $name variable and cut out everything after the last / to figure out the directory we want to extract to, go there to extract and then cut out everything before the last / to get the file name to give to unrar (and remember to return), I think.

I didn't actually test these. :-)

---

### Post by Lakefall on 2007-07-08
No wait.. the obvious solution is to have two for loops:
```
for directory in $(find . -type d)
do (cd $directory
for file in *.rar
do mkdir $file-dir
(cd $file-dir
unrar x $file)
done)
done
```
Didn't test this either.

---

### Post by Lakefall on 2007-07-08
> **Lakefall said:**
> ```
(cd $file-dir
unrar x $file)
```
Oops.. that should be ```
unrar x ../$file
```

---

### Post by r0ck80y on 2007-07-08
This will work if your rar filenames don't have spaces in them..you know...bash cannot read spaces!!

---

### Post by Lakefall on 2007-07-09
> **r0ck80y said:**
> This will work if your rar filenames don't have spaces in them..you know...bash cannot read spaces!!
Yes it can, they are just normally considered to be delimiters.

I guess this fixes that:
```
for directory in $(find . -type d)
do (cd "$directory"
for file in *.rar
do mkdir "$file.dir"
(cd "$file.dir"
unrar x "../$file")
done)
done
```

---

### Post by vanadium on 2007-07-09
find <wheretostart> -name '*.rar' -execdir unrar {} \;

Something like this. This will find all your rar's below the directory where the search starts. The command after the option -execdir will be repeated for each found file. The {} stands for the found file name.

---

### Post by Lakefall on 2007-07-09
This version should fail with less errors if things go wrong (disk fills up or something):
```
for directory in $(find . -type d)
do (cd "$directory"
for file in *.rar
do if mkdir "$file.dir"
then (cd "$file.dir"
unrar x "../$file")
else echo "Creation of $directory/$file.dir failed! Aborting."
break 2
fi
done)
done
```

This last version tries to **delete** the rar files as it goes along, but not delete if they don't extract right. Note that this *depends on* unrar exiting with status 0 only if the files got extracted fine. *I do not know if it actually does that!*
```
for directory in $(find . -type d)
do (cd "$directory"
for file in *.rar
do if mkdir "$file.dir"
then (cd "$file.dir"
if unrar x "../$file"
then rm "../$file"
else echo "Not removing $directory/$file."
fi)
else echo "Creation of $directory/$file.dir failed! Aborting."
break 2
fi
done)
done
```

In a related note, if you want to turn this into a proper shell script, you should probably replace "break 2" with "exit 1".

---

### Post by Lakefall on 2007-07-09
> **vanadium said:**
> find <wheretostart> -name '*.rar' -execdir unrar {} \;

Something like this. This will find all your rar's below the directory where the search starts. The command after the option -execdir will be repeated for each found file. The {} stands for the found file name.
Maybe I should read man find one of these days. ;-) Anyhow that should be "unrar x {} \;" and that doesn't create the file specific subdirectories.

---

### Post by Lakefall on 2007-07-09
> **Lakefall said:**
> ```
break 2
```
I just realized the subshell breaks that break. Oh well...

---

