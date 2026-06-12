---
title: "Comparing 2 folders removing the files that are not there twice...."
date: 2013-01-18
forum: General Help
---

### Post by thusgaard on 2013-01-18
Hi

I have 2 folders containing files for a special timelapse video. 
They have been shot with two cameras and named the same way.

All the pictures are amed like: 2013-01-11-07:58:17.jpg

My problem is that one folder has slightly more pictures than the other. (camera error) 
So I want to compare folder 1 to folder 2, but only at file name level. 
And remove the pictures that aren't represented in both folders (copying them to a new folder) 

Can this be done and how?

J;-)

---

### Post by fdrake on 2013-01-18
the diff command should do it:
```

ls ./folder1 > file1
ls ./folder2 > file2
diff -s file1 file2

```

edited: incomplete command

---

### Post by thusgaard on 2013-01-18
> **fdrake said:**
> the diff command should do it:
```

ls ./folder1
ls ./folder2
diff -s file1 file2

```

Will that remove anything or just show the difference?

Dosn't this only work on one file. I have 2300+ files in both directories.

---

### Post by Vaphell on 2013-01-18
are these directories flat or have subdirs in them?

---

### Post by thusgaard on 2013-01-18
> **Vaphell said:**
> are these directories flat or have subdirs in them?

No subdirs, they are completely flat

---

### Post by thusgaard on 2013-01-18
> **fdrake said:**
> the diff command should do it:
```

ls ./folder1 > file1
ls ./folder2 > file2
diff -s file1 file2

```

edited: incomplete command

Is there a way to 

move the files in the diff list.
Say is I do like this: 

```
diff -s file1 file2 > difffile
```

---

### Post by fdrake on 2013-01-19
i am sure someone will come up with a more elegant code , but this is what I could get at the moment as fast as I could.

```
diff -qr ~/a ~/b | while read line ;
do  folder="$( echo $line | cut -d ":" -f 1| cut -d " " -f 3)"; 
file="$( echo $line | cut -d " " -f 4)"; 
path="$folder/$file"; 
cp $path ~/c ; 
done
```
copy and paste into the termianl one line at the time:

"~/a" and "~/b" are the folders to be compared
"~/c" ius the folder where you want to copy the file not in common


Note : 
1-you have to change the path and the name of the folders based on your folders;
2- I used the copy command not the move "mv". Just to make sure you don't loose any data. Try it first then change "cp $path ~/c ; " with "mv $path ~/c ; " (or even better an IF condition that deletes the file only if the copy commands is succesfull)_
[SIZE="4"][COLOR="Red"]_** BE CAREFULL! "mv" COMMAND DOES NOT FORGIVE!!! :twisted:**_[/COLOR][/SIZE]

---

### Post by steeldriver on 2013-01-19
couldn't you just do something like

```
$ for file in dir2/*; do [ -f "dir1/${file##*/}" ] || cp "$file" newdir/; done
``````
$ ls dir1
file1  file2  file3  file4  file5
$ ls dir2
file1  file2  file3  file4  file5  file6
$ 
$ for file in dir2/*; do [ -f "dir1/${file##*/}" ] || echo cp "$file" newdir/; done
cp dir2/file6 newdir/
```

---

### Post by fdrake on 2013-01-19
> **steeldriver said:**
> couldn't you just do something like

```
$ for file in dir2/*; do [ -f "dir1/${file##*/}" ] || cp "$file" newdir/; done
``````
$ ls dir1
file1  file2  file3  file4  file5
$ ls dir2
file1  file2  file3  file4  file5  file6
$ 
$ for file in dir2/*; do [ -f "dir1/${file##*/}" ] || echo cp "$file" newdir/; done
cp dir2/file6 newdir/
```

I do not think the code copies the files present in dir1 AND not in dir2 . You copy only the files present in dir2 and AND in dir1.


can you posyt the content of new dir?

---

### Post by thusgaard on 2013-01-20
This worked for me: 

```
$ cd folder1/
$ for file in `ls -1` ; do [ -f ../folder2/${file} ] || mv  $file /somefolder/ ; done

$ cd ../folder2/
$ for file in `ls -1` ; do [ -f ../folder1/${file} ] || mv  $file /somefolder/ ; done 

```


Thanks for all your help. 

J;-)

---

### Post by Vaphell on 2013-01-21
any space will blow it up

```
for file in [COLOR="Red"]`ls -1`[/COLOR]; #bad
for file in [COLOR="Blue"]*[/COLOR]; #good


[ -f ../folder2/[COLOR="Blue"]"[/COLOR]${file}[COLOR="Blue"]"[/COLOR] ] || mv  [COLOR="Blue"]"[/COLOR]$file[COLOR="Blue"]"[/COLOR] /somefolder/
```

---

