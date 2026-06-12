---
title: "How does the 'du' command work?"
date: 2008-06-13
forum: General Help
---

### Post by neoAnderson on 2008-06-13
Hello all,

I have a more specific question than the title of the thread. Let me state the problem in general terms:

I have two folders, F1 and F2, containing plain text files. Each file in F1 has exactly one corresponding related file in F2 (they are translations of each other). Thus both folders contain, say, a 100 files each. Now, I take one file from F1, take 10 lines from it, then I take the corresponding related file from F2, take 10 lines from that, combine them, and produce a new file in a new folder, say F3. I repeat this until I reach the end of the file in F1 (which also means the end of the corresponding file in F2 because the two corresponding files have the exact same number of lines) - thus the file in F1 along with the file in F2 get fragmented, say 10 times (depending on the size), and these two files therefore produce 10 new, compounded files in F3. I repeat this for all the files I have in F1 (which is equal to the number of files in F2).

Now my question is, the Linux 'du' command shows 113MB for F1, 122MB for F2 (which is ok because the two folders contain text files in two different languages). But the compounded documents in F3 have a size of 626MB, as reported by 'du'. I do not understand where so much extra size is coming from, because I am not duplicating the data. 

Any thoughts? :confused:

---

### Post by VMC on 2008-06-13
If you type from Terminal ls -a do you see any "dot" like ".junk". Maybe you have extra hidden files in one or the other.

edit: I just remembered du will show the hidden files. Maybe the du in including other folders not accounted for.

---

### Post by gug@fnal.gov on 2008-06-13
There is potentially wasted space as the filesystem allocates space in discrete chunks. For large files this is often insignificant in terms of percentage of space used. For tiny files this can be very significant. I think there might also be space used up just to hold the metadata for a file, again for large files that can be usually ignored, but for tiny files that can be a big penalty. 


small file example
gug@samurai:~$ echo "a" > a.a
gug@samurai:~$ cat a.a
a
gug@samurai:~$ ls -lk a.a
-rw-r--r-- 1 gug gug 1 2008-06-13 17:49 a.a
gug@samurai:~$ du a.a
4       a.a
gug@samurai:~$ du -k a.a
4       a.a
gug@samurai:~$ 

compare that to the large file example

gug@samurai:~$ ls -lk deskjet6127.ps 
-rw-rw-r-- 1 gug 1533 15687 2005-04-17 17:58 deskjet6127.ps
gug@samurai:~$ du -k deskjet6127.ps 
15708   deskjet6127.ps
gug@samurai:~$ 

I am not an expert, but I am sure others can explain the details of why this happens.

---

### Post by neoAnderson on 2008-06-14
> **VMC said:**
> If you type from Terminal ls -a do you see any "dot" like ".junk". Maybe you have extra hidden files in one or the other.

edit: I just remembered du will show the hidden files. Maybe the du in including other folders not accounted for.

Well, no - I do not see any file names starting with a dot... wouldn't expect it either - seeing as it my own script that is creating this folder and producing the files. Thanks for the reply though. I am using

```
du -hs folderName
```

which gives the summary of the folder in human readable format.

---

