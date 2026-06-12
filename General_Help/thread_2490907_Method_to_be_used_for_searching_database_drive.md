---
title: "Method to be used for searching database drive"
date: 2023-09-20
forum: General Help
---

### Post by satimis on 2023-09-20
Hi all

I have text files and image files stored on /folders/sub-folders on a storage database drive.

Drive - PCIe 3.0 SSD
Size - 2TB
solely for storage without OS installed

Files
.txt
.png
.jpg
etc.

Please advise what method/methods shall I use to search;
1) the contain on text files
2) name of all files

Thanks in advance

Regards

---

### Post by TheFu on 2023-09-20
Assuming there's a file system and it is mounted ... 

**recoll**
There are many, but I think you'd like recoll best for looking inside. It is basically your own private google. Recoll has a GUI or it can be used with the CLI - I have a little script that searches it, since GUIs are too slow.

As for filenames, **locate** is the tool. It has been around 30 yrs.  The package name has changed a few times.  I think it it is currently updatedb.

BTW, probably best NOT to call this a database drive, since it is probably/hopefully, a partition with a file system (that isn't mandated) nor what people think of as a DBMS.  It is just a file system with lots of files on it, right?

**Alternative that requires more work:**
Use either **find** or **ls -lr** to create a list of files and save those into a text file.  then just use grep/egrep to search that text file.  I do this for my video collection.  When each optical disc was "burned", I numbered the disc and created a file dvd-001.txt ----> dvd-999.txt. Inside each is the **ls -lr** text file that has the filenames for the files stored on that disc.  All the dvd* files are stored into a single directory. 
```
...
dvd-145.txt                 dvd-351.txt
dvd-146.txt                 dvd-352.txt
dvd-147.txt                 dvd-353.txt
dvd-148.txt                 dvd-354.txt
...
```
you get thee idea.  Next, I wrote a script that uses egrep to search those dvd* files.
```
$ search-dvd starman jones
  /d/D2/DVD/dvd-019.txt:dr-xr-xr-x    2 4294967295 4294967295     4552 Sep 18 07:46 Starman_Jones
  /d/D2/DVD/dvd-019.txt:/cdrom/Heinlein/Starman_Jones:
...

```
Those search results tell me to pull dvd 19 to find the files. This is for things that are offline. For online filenames, **locate** is better, but it requires smarter searching since it doesn't have my script wrapped around it that deals with word separators.

If you just want a list of files for the entire file system, 
```
ls -lR /data > /data/ls-lr.txt 
```
or 
```
find /data  /data -type f > /data/find-files.list 
```

**Recoll** is in the repos and much more likely to be what you want. Indexing will take some time and requires some "helpers" be installed, but once that is done, searches are extremely fast.

---

### Post by satimis on 2023-09-20
> **TheFu said:**
> Assuming there's a file system and it is mounted ... 

**recoll**
There are many, but I think you'd like recoll best for looking inside. It is basically your own private google. Recoll has a GUI or it can be used with the CLI - I have a little script that searches it, since GUIs are too slow.

As for filenames, **locate** is the tool. It has been around 30 yrs.  The package name has changed a few times.  I think it it is currently updatedb.

BTW, probably best NOT to call this a database drive, since it is probably/hopefully, a partition with a file system (that isn't mandated) nor what people think of as a DBMS.  It is just a file system with lots of files on it, right?

**Alternative that requires more work:**
Use either **find** or **ls -lr** to create a list of files and save those into a text file.  then just use grep/egrep to search that text file.  I do this for my video collection.  When each optical disc was "burned", I numbered the disc and created a file dvd-001.txt ----> dvd-999.txt. Inside each is the **ls -lr** text file that has the filenames for the files stored on that disc.  All the dvd* files are stored into a single directory. 
```
...
dvd-145.txt                 dvd-351.txt
dvd-146.txt                 dvd-352.txt
dvd-147.txt                 dvd-353.txt
dvd-148.txt                 dvd-354.txt
...
```
you get thee idea.  Next, I wrote a script that uses egrep to search those dvd* files.
```
$ search-dvd starman jones
  /d/D2/DVD/dvd-019.txt:dr-xr-xr-x    2 4294967295 4294967295     4552 Sep 18 07:46 Starman_Jones
  /d/D2/DVD/dvd-019.txt:/cdrom/Heinlein/Starman_Jones:
...

```
Those search results tell me to pull dvd 19 to find the files. This is for things that are offline. For online filenames, **locate** is better, but it requires smarter searching since it doesn't have my script wrapped around it that deals with word separators.

If you just want a list of files for the entire file system, 
```
ls -lR /data > /data/ls-lr.txt 
```
or 
```
find /data  /data -type f > /data/find-files.list 
```

**Recoll** is in the repos and much more likely to be what you want. Indexing will take some time and requires some "helpers" be installed, but once that is done, searches are extremely fast.
Hi TheFu,

Lot of thanks for your detailed advice.

I prefer using command lines NOT GUI.  The database drive can be mounted manually

1) 
.txt files
I only search its content having particular words which I'm looking for.

2)
Filenames
To search words, which I'm looking for, contained in the filename

Before I ran "find" but there are lots of work for me afterwards, searching for my words on the file.

Your help would be much appreciated.  Thanks in advance.

Regards

---

### Post by TheFu on 2023-09-20
Then use recoll.

---

### Post by satimis on 2023-09-20
> **TheFu said:**
> Then use recoll.
Thanks

Recoll is on repo

Is following document suitable for me to follow?
**[COLOR="#FF0000"]Recoll user manual[/COLOR]**
[https://www.lesbonscomptes.com/recoll/usermanual/usermanual.html](https://www.lesbonscomptes.com/recoll/usermanual/usermanual.html)

I prefer command lines operation NOT GUI

Regards

---

### Post by TheFu on 2023-09-20
> **satimis said:**
>  I prefer command lines operation NOT GUI

Then don't use the GUI version.  The manpage for recoll is pretty clear.

---

### Post by dragonfly41 on 2023-09-20
[COLOR=#000000]> I prefer command lines operation NOT GUI

You can try ripgrep.

But also I played my party trick by asking Phind.com for a script.  I am trying to get order out of chaos in my desktop.

I can send the script I settled on but just try this AI enabled browser for ideas.

Incidentally recoll is a good app and SearchMonkey but ripgrep serves your CLI needs.

Here is the Phind.com query I dreamed up. Note that queries close to the task should be asked.

[/COLOR]QUERY:
```
In a very chaotic Ubuntu Linux desktop, this user is trying to get order out of chaos in files and folders,  list by date accessed each selected file type and path to each file in a json array for automation script purposes in searching documents.  Also extend this automation task to apply ripgrep to this array to find content inside each file. 
For each search a list of matching phrases will be supplied to the suggested bash or python script
This script must search recursively through subfolders throughout the entire desktop and/or mounted drives.
```

P.S. you might consider offering a list of words/phrases/patterns you are searching for.


P.P.S. Another very effective method is using corpus linguistic tools 

[https://neon.niederlandistik.fu-berlin.de/en/textstat/](https://neon.niederlandistik.fu-berlin.de/en/textstat/)

but this only works on txt files. Ripgrep scans through multiple file types.

---

