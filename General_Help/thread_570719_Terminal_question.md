---
title: "Terminal question"
date: 2007-10-08
forum: General Help
---

### Post by Auria on 2007-10-08
Hi,

this is probably simple for you Unix gurus, but there's something i'd like to do and can't figure out. How can i copy a folder and all its content, a bit like "cp" would, but excluding certain files depending on their name? What i precisely want to is copy all files but those starting with "."

thanks!

---

### Post by mojoman on 2007-10-08
```
cd SOURCEDIRECTORY
cp .* /TARGETDIRECTORY/
```

You'll get a message saying
```
cp: omitting directory `.'
cp: omitting directory `..'
```
which means that it did not copy the current directory nor its parent directory. However, it will copy all hidden files, which, I believe is what you wanted, yes?

EDIT: Note, if there are (hidden) subdirectories that you want included you'll have to use the -r option with cp

---

### Post by Auria on 2007-10-08
> **mojoman said:**
> ```
cd SOURCEDIRECTORY
cp .* /TARGETDIRECTORY/
```

You'll get a message saying
```
cp: omitting directory `.'
cp: omitting directory `..'
```
which means that it did not copy the current directory nor its parent directory. However, it will copy all hidden files, which, I believe is what you wanted, yes?

EDIT: Note, if there are (hidden) subdirectories that you want included you'll have to use the -r option with cp

no, i want the opposite :lolflag: copying everything BUT files beginning with "." :D and there are multiple subdirectories

---

### Post by mojoman on 2007-10-09
> **Auria said:**
> no, i want the opposite :lolflag: copying everything BUT files beginning with "." :D and there are multiple subdirectories

I'm sorry. I'm an idiot and should read more carefully before I post. :oops:

Anyway, do it with a short script then. Create a file doing 
```

touch cpscript
```

Open it with you favorite editor and write in the following
```

for i in [!.*]; do
cp /PATH_TO_SOURCE_DIRECTORY/* PATH_TO_TARGET_DIRECTORY/
done
```

(cp -r PATH_TO_SOURCE_DIRECTORY/* if you want it to be recursive)

Make the script executable
```

chmod +x cpscript
```

Now, all you need to do is execute the script 

```
./cpscript
```

Voila, all files that *does not* start with . is copied.

Now, is that what you wanted? ):P

/mojoman

---

### Post by Auria on 2007-10-09
Hi, thanks for answering

upon trying to run this script, i get

> 
usage: cp [-R [-H | -L | -P]] [-f | -i | -n] [-pv] src target
       cp [-R [-H | -L | -P]] [-f | -i | -n] [-pv] src1 ... srcN directory


:-k

---

### Post by mojoman on 2007-10-09
That's weird. I tried it before posting and it worked fine. Could you instead try 

```
for i in [!.*]; do
cp -r /* PATH_TO_TARGET_DIRECTORY/
done
```

Of course, PATH_TO_TARGET_DIRECTORY should be wherever you want the new files. Also, if you do it like this, you'll have to execute the script from the source directory but, like I said, I tried it and it worked for me.

---

### Post by anaconda on 2007-10-09
> **Auria said:**
> Hi,

this is probably simple for you Unix gurus, but there's something i'd like to do and can't figure out. How can i copy a folder and all its content, a bit like "cp" would, but excluding certain files depending on their name? What i precisely want to is copy all files but those starting with "."

thanks!

cp * /path/to/target

would copy all files which wont start with "." from current directory to the target directory

---

### Post by anaconda on 2007-10-09
> **mojoman said:**
> That's weird. I tried it before posting and it worked fine. Could you instead try 

```
for i in [!.*]; do
cp -r /* PATH_TO_TARGET_DIRECTORY/
done
```

Of course, PATH_TO_TARGET_DIRECTORY should be wherever you want the new files. Also, if you do it like this, you'll have to execute the script from the source directory but, like I said, I tried it and it worked for me.

if you copy from /*
then that would copy everything starting from / to the target directory.. 

I dont think he wants to copy everything from /etc, /boot, /usr, /home etc.. So better to omit the "/" 

And I think the cp -r * will copy files that start with . from the subdirectories.. not from the current directory though..

---

### Post by Auria on 2007-10-09
> **anaconda said:**
> 
And I think the cp -r * will copy files that start with . from the subdirectories.. not from the current directory though..

yes that's what it did, so i can't really use it... the script with for has pretty much the same problem

BTW: a script that recursively deletes all files starting with . would work too...

---

### Post by Auria on 2007-10-09
I think i found an unefficient but working solution ;)

tar cj --exclude '.*' -f Archive.tar.bz2 datafolder

and then i can move it and expand it again :-P
testing right now...

EDIT: Works!

---

### Post by eph1973 on 2007-10-09
Go to the directory you wish to start the copying from.  Let's say it's /home/(user)/music, which can be abbreviated with ~ and your target directory is ~/musicbackup
```
 cd ~/music
```From there type:
```
cp -R * ~/musicbackup
```Remember that if you are making copies somewhere where the directory needs superuser privileges in order to write so it, you will need to prefix that with 'sudo'.

Edit:  Your solution looks like it would work well, although you could of written
```
cp -R * ./thisdirectory thatdirectory; rm -R thatdirectory/.*
```To go ahead and copy everything then go back and remove the files that start with the "."

---

### Post by mojoman on 2007-10-09
> **anaconda said:**
> if you copy from /*
then that would copy everything starting from / to the target directory.. 

I dont think he wants to copy everything from /etc, /boot, /usr, /home etc.. So better to omit the "/" 

And I think the cp -r * will copy files that start with . from the subdirectories.. not from the current directory though..

Oops! That was a / too much (which can be quite fatal...) :oops: I meant it to be
```

for i in [!.*]; do
cp -r * PATH_TO_TARGET_DIRECTORY/
done

```

---

