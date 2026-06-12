---
title: "command line help"
date: 2006-12-29
forum: General Help
---

### Post by sadjack on 2006-12-29
Hi

I have a number of files and folders that I have copied to my system. There are a few files that reside in each folder that I want to delete. Rather than going from folder to folder and deleting the files is there a command or short script that would look through the folders and delete files with certain extensions only. The files that I want to delete have windows .doc and .db file extensions. I want to leave the folders and all other file extensions in place.

Any help / suggestions gratefully received as I don't want to spend possibly hours going through each folder and its sub folders!

Cheers

---

### Post by mojoman on 2006-12-29
> **sadjack said:**
> Hi

I have a number of files and folders that I have copied to my system. There are a few files that reside in each folder that I want to delete. Rather than going from folder to folder and deleting the files is there a command or short script that would look through the folders and delete files with certain extensions only. The files that I want to delete have windows .doc and .db file extensions. I want to leave the folders and all other file extensions in place.

Any help / suggestions gratefully received as I don't want to spend possibly hours going through each folder and its sub folders!

Cheers

Files are deleted with the command rm (stands for remove). for example ```
sudo rm windows.doc
``` would remove the file windows.doc in the folder you are standing in. The command ```
sudo rm *.doc
``` will remove all files in that folder that ends in ".doc". If you use > sudo rm -r *.doc you will delete all files ending with ".doc" in the folder you are standing as well as all of its subfolders.

BE VERY CAREFUL WHEN DELETING FILES WITH WILDCARD!!

Also, I strongly recommend that you use ```
rm -ir *.doc
```, the -i option will promt you if the file is to be removed. Read up on the manual ```
man rm
``` because one little slip with a wildcard will send you to a world of worries. I kid you not.

Take it easy out there ;) 
/Mojoman

EDIT: Another tip is to use the command find. Have a look at the manual (man find), with this command you can search -with the subfolders- for the files, e.g. *.doc. If you then use rm instead of find the documents that find located will be deletad BUT if I'm not mistaken find is by default recursive (though I might be mistaken about this, it should say in the man pages).

---

### Post by sadjack on 2006-12-29
Thanks Mojoman.

I've tried your suggestion both as user and as sudo. It deletes the file in the folder that I am in but for some reason does not go through all the others like you and the man pages suggests it should.

---

### Post by mojoman on 2006-12-29
> **sadjack said:**
> Thanks Mojoman.

I've tried your suggestion both as user and as sudo. It deletes the file in the folder that I am in but for some reason does not go through all the others like you and the man pages suggests it should.

hmm, well, there is always the f-option, e.g. > sudo rm -rfi *.doc where f stands for force. Perhaps some brute force will do the trick? ;) 

Once again, be careful. I strongly advice that you use the find command to see what will be deleted before using rm recursivly with a wildcard.

Happy hunting ;) 
/Mojoman

---

### Post by sadjack on 2006-12-29
Thanks again but nothing seems to be working. 

Mojoman, I see that your a dapper user, I'm using edgy, anything changed between the two that you know of. I would not have thought so as the commands are pretty much core linux, the recursive or the wildcard don't seem to be working on my system.

---

### Post by raul_ on 2006-12-29
Are the other folders subfolders or separate folders?

---

### Post by sadjack on 2006-12-29
Each folder is a separate folder inside the first one. Many of these separate folders have folders inside as well.

Is there a difference?

---

### Post by mojoman on 2006-12-29
> **sadjack said:**
> Each folder is a separate folder inside the first one. Many of these separate folders have folders inside as well.

Is there a difference?

If folder A contains folder B this means that B is a subfolder to A, i.e. B is located in A.

As far as the command line goes, there shouldn't be any difference between dapper and edgy. 

I'm sorry to say that I'm out of ideas on this one, at least for now. Anyone else have a solution?

/Mojoman

---

### Post by raul_ on 2006-12-29
the man page is pretty explicit:

 -r, -R, --recursive
              remove directories and their contents recursively

maybe that doesn't work with wildcards, only directories...i've tested and it also doesn't work with me

---

### Post by mojoman on 2006-12-29
One more thing, it's a long shot but it's for free ;)  Log in as root and try it again, instead of using sudo. Should be the same thing but why not, eh?

/Mojoman

---

### Post by sadjack on 2006-12-29
I've just done a ls -Ral and I get a full listing of each directory and its contents. So the system can go through them, its just the syntax that will get the rm command to work.

The files were copied from CD. I've checked permissions and they seem to be OK. I can delete files one by one both from the command line and via gnome.

This is going to be a really simple issue, I'll be kicking myself......

---

### Post by sadjack on 2006-12-29
Just tried logging in as root. Same result.

Bah humbug...

---

### Post by TheWizzard on 2006-12-29
normally i'm a big fan of doing as much as possible using the command line. but the combination sudo + rm + wildcard scares me. 

why not use the GUI "find files/folders" and then select all files you want to delete? this works in kde.

---

### Post by sadjack on 2006-12-30
AND IT WORKS WITH GNOME!!!!! Yeeeeaaaaaahhhhhh.

I would have really liked to have learned how to do this at the command line but the tip from thewizzard worked well, thanks.

But any command line guru's out there who know how to do it please post here!

---

### Post by TheWizzard on 2006-12-31
> **sadjack said:**
> Thanks Mojoman.

I've tried your suggestion both as user and as sudo. It deletes the file in the folder that I am in but for some reason does not go through all the others like you and the man pages suggests it should.

recursive only removes the files in subdirectories of the directory you're in. 
```
sudo rm -r *.doc
```
should work.

---

### Post by sadjack on 2006-12-31
Yep it should, and does with directories but not with files on my system.

Thanks tho.

---

### Post by koenn on 2006-12-31
list files with extension .doc in tesdir1 + subdirs :
```
ix:~$ find ./testdir1 -name "*.doc" -exec ls {} \;
./testdir1/testdir2/file2.doc
./testdir1/file1.doc
```

remove those files 
```
nix:~$ find ./testdir1 -name "*.doc" -exec rm -i {} \;
rm: remove regular empty file `./testdir1/testdir2/file2.doc'? y
rm: remove regular empty file `./testdir1/file1.doc'? y
```

the -i switch to rm makes it ask for confirmation; without it, it would just delete; 

rm -r is apparently only to remove directories (+ their contents), not individual files within them, that is maybe why the combination -r and *.doc doesn't work
>  -r, -R, --recursive
              remove directories and their contents recursively

---

### Post by sadjack on 2006-12-31
koenn

On first look all I can say is "WOW". 8) 

Thanks I'm testing now.  :D

---

### Post by sadjack on 2006-12-31
koenn

I bow to your knowledge of the command line. It worked like a dream. Its now added to my list of really useful commands! 8)  8)  8)

---

### Post by koenn on 2006-12-31
glad it worked for you.

---

### Post by marc_zw on 2008-04-11
If you want to remove a folder and all subsequent files and sub folders, use:

sudo rm -R /path to folder/folder name

I havent tried it with wildcards but if it you removing an entire folder and everything in it, this shouldnt be a problem.

---

