---
title: "Help with rm.  Summary available?"
date: 2007-11-26
forum: General Help
---

### Post by cknight on 2007-11-26
I'm trying to find a command that will let me delete files from the command line and tell me what its about to do in a summary.  Looking at the man page of 'rm' it shows one option, interactive, which is almost what I want.  'rm -i' will ask me for each and every file if I want to delete it.  

What I'm looking for is something which will display all files/directories that will be deleted and ask me to confirm once for everything (rather than once per file/directory).  Doesn't look like rm is up to that task.  Any other utilities I might use for this?

e.g. This is what i'm looking for
```
$>delete_command ~/temp/*
The following files will be deleted...
~/temp/one
~/temp/two
~/temp/three
Do you wish to delete the above 3 files (Yes/No)?
```

Thanks!

---

### Post by 1337455 10534 on 2007-11-26
Try running rm with the -v tag, for verbose. If you are looking for some very secure and complete (but slightly dangerous) file shredder script, you can PM me for it, since I got in trouble last time I posted it.
Word to the wise, stay away from rm and shred if possible.

---

### Post by hikaricore on 2007-11-26
I don't really see how you answered the question so much as complained about your script getting you in trouble..

---

### Post by mali2297 on 2007-11-26
Check first with 
```

ls ~/temp/*

```
If you want to remove all files listed, then do
```

rm ~/temp/*

```

---

### Post by cknight on 2007-11-26
> **mali2297 said:**
> Check first with 
```

ls ~/temp/*

```
If you want to remove all files listed, then do
```

rm ~/temp/*

```


Yep, more or less what I'm looking for, but with a single command to do both with an 'Are you sure?' prompt in-between.

---

### Post by nick_h on 2007-11-26
Try rm with the -i option:
```
rm -i ~/temp/*
```
this will prompt before removing each file.

---

### Post by Anonii on 2007-11-26
> **cknight said:**
> Yep, more or less what I'm looking for, but with a single command to do both with an 'Are you sure?' prompt in-between.
```

#!/bin/bash
#Amazingly powerful script. Fear my 10 minutes bash knowledge.

echo The following files will be deleted:
echo
ls -1 --color $1
echo
echo -n "Do you wish to delete the above"
if [ $(ls -1 $1 | wc -l ) == "1" ]
then
	echo " file [Y/N] ?"
else
	echo " $(ls -1 $1 | wc -l ) files [Y/N] ?"
fi
echo
read -e DEC
if [ $DEC == "Y" -o $DEC == "y" ]
then 
        echo
	rm -v $1/*
        echo
        echo "I'm done here!"
else
	echo
	echo "Excuse me, then, master."
	echo 
fi


```

(I get no responsibility, etc. etc.)

Just a small teaser of it's ultimate power:

> 
$ ./script ball/
The following files will be deleted:

mya
sdkd.c
sdkdk

Do you wish to delete the above 3 files [Y/N] ?

Y
removed `ball//mya'
removed `ball//sdkd.c'
removed `ball//sdkdk'

I'm done here!


(If you keep it, just put it in your /usr/bin, rename it and **chmod +x** it. Then you won't have to type ./script every time.)

Now, if you want it to also remove directories.. That needs more lines of "code".

---

### Post by 1337455 10534 on 2007-11-26
> 
I don't really see how you answered the question so much as complained about your script getting you in trouble..

True, but I did try. Honestly, rm -v was the most information I've needed about deleting a file...

---

### Post by mali2297 on 2007-11-27
> **Anonii said:**
> 
#!/bin/bash
#Amazingly powerful script. Fear my 10 minutes bash knowledge.


:shock: 


.. amazing.

---

### Post by Rinzwind on 2007-11-27
> **mali2297 said:**
> Check first with 
```

ls ~/temp/*

```
If you want to remove all files listed, then do
```

rm ~/temp/*

```

In case between the ls and the rm a file has been created it would be deleted without being shown. 

The output from 
ls
should be piped into a text-file and the 
rm 
should be done with the filenames inside the textfile.

Anonii: rm -v $1/* this would also remove any other files inside that directory created after the ls(?)

---

### Post by Anonii on 2007-11-27
> **Rinzwind said:**
> In case between the ls and the rm a file has been created it would be deleted without being shown. 

The output from 
ls
should be piped into a text-file and the 
rm 
should be done with the filenames inside the textfile.

**Anonii: rm -v $1/* this would also remove any other files inside that directory created after the ls(?)**

$1 in Bash is the first parameter that the user passes. For example, in "rm -v foo", $1 is "-v". Something like argv[1] in C.

So well, since the script is used like this: **./script directory**, it will do the following action:_ rm -v directory/*_ (or well, that's what my tries showed me.)

(My posts come with no warranty too.)

---

