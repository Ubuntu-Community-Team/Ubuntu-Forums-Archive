---
title: "A question about Daemon Tools"
date: 2007-07-16
forum: General Help
---

### Post by Popolop on 2007-07-16
Is it possible to install/download Daemon Tools? If so, can you tell me how to (not very good with Ubuntu)? And if you can't, then can you tell me how to mount .nrg and .iso?

---

### Post by ayoli on 2007-07-16
```
sudo mkdir /mnt/ISO 
```
and 
```
sudo  mount -t iso9660 /path/to/filename.iso /mnt/ISO/ -o loop
```
replace /path/to/filename.iso with the path to your iso.

---

### Post by bodhi.zazen on 2007-07-16
And for your nrg files :

[http://ubuntuforums.org/showpost.php?p=3028694&postcount=10](http://ubuntuforums.org/showpost.php?p=3028694&postcount=10)

---

### Post by Popolop on 2007-07-16
Alright, thanks.

One last thing (I swear >.>). How do you burn a .nrg?

---

### Post by yabbadabbadont on 2007-07-16
Use NeroLinux or convert it to an ISO first.

---

### Post by Popolop on 2007-07-16
I tried doing

```
 nrg2iso [nrg-file] [iso-file] 
```

But it keeps on saying 

> WINXPPROITT : No such file

Tips?

---

### Post by yabbadabbadont on 2007-07-16
Post the *exact* command that you used as well as the output of "ls -l" in the directory that contains the files.  Linux is case sensitive by the way, in case you didn't know that.

---

### Post by bodhi.zazen on 2007-07-17
You need to use the path to the .nrg file as well as the file name ...

so if the .nrg is on your Desktop ...

```
nrg2iso Desktop/file.nrg Desktop/file.iso
```

where file is the name of the respective files.

---

### Post by crispy_420 on 2007-07-17
[http://www.acetoneteam.org/latest-news.html](http://www.acetoneteam.org/latest-news.html)

try this tool

---

