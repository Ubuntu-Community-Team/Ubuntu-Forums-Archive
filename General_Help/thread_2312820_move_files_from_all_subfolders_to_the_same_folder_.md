---
title: "move files from all subfolders to the same folder but ignore deeper folders"
date: 2016-02-07
forum: General Help
---

### Post by sohlinux on 2016-02-07
Hello,

I have a folder with many sub-folders and inside the sub-folders are many files and more folders, I want to move all the files except the files in deeper folders to /data folder

I have tried the following which works but it also moves the files from the deeper folders which I do not want to do

```

find /data -type f -print0 | xargs -1 mv -ft /data
```

I have tried adding   -maxdepth 1 and -mindepth 1 but it will not work it says find: paths must precede expression: /data

anyone have any ideas?

thanks

---

### Post by steeldriver on 2016-02-07
*where* did you add -maxdepth 1 and -mindepth 1? As indicated by the error message, the placement is important

You probably want -maxdepth 2 and -mindepth 2 if you are trying to move items exactly from one directory below /data

```

$ tree
.
&#9500;&#9472;&#9472; dir1
&#9474;   &#9500;&#9472;&#9472; dir2
&#9474;   &#9474;   &#9500;&#9472;&#9472; dir3
&#9474;   &#9474;   &#9492;&#9472;&#9472; file2
&#9474;   &#9492;&#9472;&#9472; file1
&#9492;&#9472;&#9472; dirA
    &#9500;&#9472;&#9472; dirB
    &#9474;   &#9500;&#9472;&#9472; dirC
    &#9474;   &#9492;&#9472;&#9472; fileab
    &#9492;&#9472;&#9472; filea

```

```

$ find . -maxdepth 2 -mindepth 2 -type f
./dirA/filea
./dir1/file1

```

Also what is xargs -1 supposed to do? did you mean to write xargs -0 (since you are using print0)?
```

$ find . -maxdepth 2 -mindepth 2 -type f -print0 | xargs -0 mv -vt ./ 
‘./dirA/filea’ -> ‘./filea’
‘./dir1/file1’ -> ‘./file1’

```

You could skip the xargs altogether and just use -exec
```

$ find . -maxdepth 2 -mindepth 2 -type f -exec mv -vt ./ {} + 
‘./dirA/filea’ -> ‘./filea’
‘./dir1/file1’ -> ‘./file1’

```

---

### Post by sohlinux on 2016-02-07
I was putting -maxdepth 1 -mindepth 1 directly after the find command , I see you placed it after the folder name . which now works

yes I meant xargs 0

what I had tried didnt work
```
find -maxdepth 1 -mindepth 1 /data -type f -print0 | xargs -0 mv -ft /data
```

the following as you suggested works perfectly thanks
```
find /data/ -maxdepth 2 -mindepth 2 -type f -exec mv -vt /data/ {} +
```

what is {} + at the end for?

---

### Post by steeldriver on 2016-02-07
{} is a placeholder for the files found by the find command, and + says to process as many as possible in a single command (a la xargs)

See 'man find' - in particular

```

       -exec command {} +
              This  variant  of the -exec action runs the specified command on
              the selected files, but the command line is built  by  appending
              each  selected file name at the end; the total number of invoca&#8208;
              tions of the command will  be  much  less  than  the  number  of
              matched  files.   The command line is built in much the same way
              that xargs builds its command lines. <snip>

```

---

### Post by sohlinux on 2016-02-07
awesome thanks

---

### Post by sohlinux on 2016-02-15
I have found that some of the folders have files with the same name as some of the files in other folders so is it possible to add something to the script to rename the files if they have the same name? thanks

eg 

folder1 has 1.txt
folder2 has 1.txt

move both 1.txt but rename the second file to a1.txt

---

