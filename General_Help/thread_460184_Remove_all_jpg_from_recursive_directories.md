---
title: "Remove all jpg from recursive directories"
date: 2007-05-31
forum: General Help
---

### Post by tekguy on 2007-05-31
I have a parent folder called music that I want to remove all of the album art from. What I can not figure out is how to remove just the jpg files. I have multiple subfolders. I got as far as:

```
ls -R /media/Storage/Music/ | grep jpg
```

This will allow me to list all of the jpg files in all of my subfolders. I tried to pass that by adding an additional | followed by rm *.jpg

```
ls -R /media/Storage/Music/ | grep jpg | rm *.jpg
```

I get an error that it can not remove '*.jpg': No such file or directory. So how do I pass the output from grep to rm?

---

### Post by jpk on 2007-05-31
Hi, 

The first problem is that

```

ls -R /media/Storage/Music/ | grep jpg

```

produces a list of files only, and it's missing the path information (the directories where the files are). Use *find* instead of.

The second thing is the way you call *rm.* Not sure you can send the list of files to *rm* via sdtin. The files must be given as arguments. 

The easiest way is to use a for-loop, like this:
```

for i in $(find /media/Storage/Music/ -name *.jpg); do rm $i; done

```

Sincerely
Jarik

---

### Post by tekguy on 2007-05-31
Okay, I see.

I have one problem when running this command. Every place there is a space in the folder structure is being passed to rm. So instead of moving the file to the whole path it is breaking it apart and not removing the file.

Example:

rm: cannot remove `/media/Storage/Music/Van': No such file or directory
rm: cannot remove `Halen/Women': No such file or directory
rm: cannot remove `and': No such file or directory
rm: cannot remove `Children': No such file or directory
rm: cannot remove `First/AlbumArtSmall.jpg': No such file or directory
rm: cannot remove `/media/Storage/Music/Van': No such file or directory
rm: cannot remove `Halen/Women': No such file or directory
rm: cannot remove `and': No such file or directory
rm: cannot remove `Children': No such file or directory
rm: cannot remove `First/Folder.jpg': No such file or directory

---

### Post by jpk on 2007-05-31
Right, so don't use spaces in filenames ;)

Well, here is another ugly solution:
```

for i in $(find /media/Storage/Music/ -name *.jpg |awk '{ gsub (" ","(space)"); print $0;}'); do rm "${i/(space)/ }"; done

```

It grabs the files and replaces all spaces with "(space)" string to avoid for-loop breaking the stings in two. Then the "(space)" is replaced with space char again, when it's substituted in rm. 

If anyone has a better way to do this, please let me know...

---

### Post by reclusivemonkey on 2007-06-01
Or you could just use find with the "-exec" flag...

---

### Post by stoomart on 2007-06-07
The suggested command didn't work for me, the ouput contained the (space) and said the file doesn't exist.

> **reclusivemonkey said:**
> Or you could just use find with the "-exec" flag...

I don't think -exec is going to do the trick. I think you meant to use the example above -exec listed in the find man page which worked for me:


*** Caution, this command recursively deletes all .jpg starting in the current directory without prompting. ***

find . -name *.jpg -type f -print0 | xargs -0 /bin/rm

---

### Post by xarmian on 2007-06-07
you guys are going a little more complicated than is necessary.. really it is just as simple as:

find . -name *.jpg -exec rm -f {} \;

that on a single line executed in the directory you want to be the "root" of your recursive removal should take care of it.. you can add some more arguments to make it isolate only files instead of trying to delete directories, but the rm -f command wont delete directories anyway so it doesn't matter for this use.. and if a directory is named "xyxy.jpg" that's kinda odd anyway..

-Dave

---

### Post by stoomart on 2007-06-07
good call, shorter and safer.

---

### Post by reclusivemonkey on 2007-06-07
> **stoomart said:**
> The suggested command didn't work for me, the ouput contained the (space) and said the file doesn't exist.



I don't think -exec is going to do the trick. I think you meant to use the example above -exec listed in the find man page which worked for me:


*** Caution, this command recursively deletes all .jpg starting in the current directory without prompting. ***

find . -name *.jpg -type f -print0 | xargs -0 /bin/rm

Exec *will* do the trick. Remember this is Unix; there is more than one way of doing things.

---

### Post by stoomart on 2007-06-07
Yep, my bad.

---

