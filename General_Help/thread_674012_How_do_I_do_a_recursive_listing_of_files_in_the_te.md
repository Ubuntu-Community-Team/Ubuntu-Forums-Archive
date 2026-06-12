---
title: "How do I do a recursive listing of files in the terminal? (well its more than that)"
date: 2008-01-21
forum: General Help
---

### Post by ryodoan on 2008-01-21
Ok, I have a program I am trying to use that requires an input of all the files I want it to go through, however, I have a crap ton of files it needs to have input.

The program requires that the files be listed something like this:
> 
afile0.cpp
exampleDir/file3.cpp
exampleDir/file4.cpp
exampleDir/SubDir/file5.cpp
file1.cpp
file2.cpp
(they dont need to be alphabetical, or sorted, or filtered)

I know the command to just recursively list directories is:
ls -R

But that gives me a list like:
> afile0.cp
file1.cpp
file2.cpp

./exampleDir:
file3.cpp file4.cpp

./exampleDir/SubDir
file5.cpp

I dont know very much about bash commands, so thanks for any help you can give.

---

### Post by killermist on 2008-01-21
```
killermist@killermist:~/bin$ [COLOR="Red"]find[/COLOR]
.
./txt2tags
./flac2mp3.sh
./lame
./reference
./reference/flac2mp3.sh.reference
./sc_trans
./unrar
./sc_serv.conf
./sc_serv
./dos2unix
./unzip
./joe
./zipdir
./sc_trans.log
./rename
./rar
./hexedit
./sc_serv.log
./sc_trans.conf
```

There is more that the find command can do, but it looks like you're just looking for a simple output, and the raw command seems to do that fairly well.

---

### Post by ryodoan on 2008-01-21
Thanks, that looks to be exactly what I am looking for.

---

### Post by machoo02 on 2008-01-21
Also check out the xargs command, which lets you use a list of files (like that outputted by find) as input to a program on the command line

---

