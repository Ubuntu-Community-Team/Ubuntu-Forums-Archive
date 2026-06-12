---
title: "Can't open a folder."
date: 2012-11-15
forum: General Help
---

### Post by Herbon on 2012-11-15
So a few days ago I ran the following.......

> find ./ -iname 'Otis Redding - Live on*'  -exec mv '{}' ./"Otis Redding Live on the Sunset Strip" \;


Thinking this would move all files named "Otis Redding - Live on Sunset strip" into a new folder named "Otis Redding - Live on Sunset strip".

The folder is there, but I cant open it, and files are gone.

1st question, does Linux have some Gods that was angered, any needs appeasement?? :(
2nd How do I fix this?? (more importantly where did I go wrong) :confused:

Again thanks

---

### Post by steeldriver on 2012-11-15
if the destination directory did not already exist, then it would just rename each file in turn rather than move them - so what you have now is likely not a directory it's just the last file that it 'found' but without an appropriate extension to let it launch

---

### Post by drmrgd on 2012-11-15
What you in essence did was not to find all of the files with that name 'Otis Redding - Live on*' and then move them not to a new folder called 'Otis Redding Live on the Sunset Strip' but to a new FILE with that name.  What you would have needed to do was to create a new directory with that name first, and then use the move command above:

```
mkdir "Otis Redding Live on the Sunset Strip" && find . -maxdepth 1 -iname 'Otis Redding - Live on*' -exec mv '{}' ./"Otis Redding Live on the Sunset Strip" \;
```

Of course with your find glob in there you'll get an error about it finding the files you just moved.  So, you'll probably want to set the maxdepth to 1 so that it doesn't find those files as well.

I would also highly advise that whenever you do something like this precede the 'mv' command with 'echo' so that you can see what would have happened first to make sure you didn't make any mistakes.  As it is now, you've overwritten all of your files, and you'll have to recover them from the original source.

EDIT: maybe an example is worth 1000 words in this case :)

```
$ ls
file1.mp3  file2.mp3  file3.mp3  file4.mp3  file5.mp3
$ find ./ -iname 'file*' -exec mv '{}' ./"newfolder" \;
$ ls
$ newfolder
$ touch file{1..5}.mp3
$ ls
file1.mp3  file2.mp3  file3.mp3  file4.mp3  file5.mp3
$ mkdir newfolder && find ./ -maxdepth 1 -iname 'file*' -exec mv '{}' ./"newfolder" \;
$ ls
newfolder
$ ls -R
.:
newfolder

./newfolder:
file1.mp3  file2.mp3  file3.mp3  file4.mp3  file5.mp3
```

---

### Post by steeldriver on 2012-11-15
one very simple thing you can do to prevent this kind of accident is to always add a / suffix to the destination so it is unambiguously a directory name not a filename

```
$ mv myfile mydir/
mv: cannot move `myfile' to `mydir/': Not a directory
```

---

### Post by Herbon on 2012-11-20
Thanks!

---

