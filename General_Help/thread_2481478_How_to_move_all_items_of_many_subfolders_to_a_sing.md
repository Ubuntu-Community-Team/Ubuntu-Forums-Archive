---
title: "How to move all items of many subfolders to a single folder in new location"
date: 2022-11-30
forum: General Help
---

### Post by padge01 on 2022-11-30
Using a fresh install of Ubuntu 22.1. I performed a disk recovery of a windows hard drive and received a large number of subfolders within the Recovery directory. I am trying to move these recovered files back to the (now formatted) drive they came from. Is there a way to select all the items within each subfolder and move them all to a single folder on a different drive? I want to list all recovered items in one folder so I can filter and identify valuables files.


I believe if I use the command


mv myfolder/* .


I will copy all items in the subfolder "myfolder" to the active directory. But since there are hundreds of subfolders in the directory is it possible to move all the files in multiple subfolders at once?
Thank you

---

### Post by TheFu on 2022-11-30
> **padge01 said:**
>  

mv myfolder/* .


I will copy all items in the subfolder "myfolder" to the active directory. But since there are hundreds of subfolders in the directory is it possible to move all the files in multiple subfolders at once?

Yes, but name collisions would be bad, right?

I can't tell if you just want to move everything up 1 directory or if you want to move only files from all subdirectories into a single directory. Both are possible.

Since we know that details are important, what is this 22.1 release?  It isn't Ubuntu.

---

### Post by padge01 on 2022-11-30
I would like to move only the files in all the sub-directories to a single directory. 

My OS is:

Distributor ID:	Ubuntu
Description:	Ubuntu 22.10
Release:	22.10
Codename:	kinetic


I am also having regular issues with the files app since installing the OS. Crashes where it asks me to choose wait or force kill. Only fix so far for this has been to reboot the system.

---

### Post by HermanAB on 2022-11-30
So, you have an unreliable system with a file system full of errors and you want to move many files with possible name collisions.  

What could possibly go wrong?

---

### Post by padge01 on 2022-11-30
Yep. Hoping to try and recover these files somehow.

---

### Post by TheFu on 2022-11-30
> **padge01 said:**
> Yep. Hoping to try and recover these files somehow.

Why not restore from the current backup?  That would be much easier.
BTW, when dealing with MS-Windows file systems, it is best to use MS-Windows tools.

> **padge01 said:**
>  I would like to move only the files in all the sub-directories to a single directory.

Easy. Run this from the directory where you want all the files to end up.
```
find myfolder -type f -exec mv "{}"    .     \; 
```
Best to have a backup BEFORE you run this.  I suspect the results will be undesirable, but it isn't like you have much to lose any way.  If there isn't a backup of important files, then they really aren't important, right?

---

### Post by padge01 on 2022-11-30
> **TheFu said:**
> 

Easy. Run this from the directory where you want all the files to end up.
```
find myfolder -type f -exec mv "{}"    .     \; 
```
Best to have a backup BEFORE you run this.  I suspect the results will be undesirable, but it isn't like you have much to lose any way.  If there isn't a backup of important files, then they really aren't important, right?

Thank you, this command is working. Wish I had enough disk space to back these up before hand, luckily important documents are on cloud and I'm hoping to recover mostly video files that were too big for my cloud storage.

---

### Post by HermanAB on 2022-12-01
BTW if you would go to your city’s garbage dump, you will likely find someone there who salvages dumped computers and sells them for about 50 dollars.

---

### Post by TheFu on 2022-12-01
> **padge01 said:**
> Thank you, this command is working. Wish I had enough disk space to back these up before hand, luckily important documents are on cloud and I'm hoping to recover mostly video files that were too big for my cloud storage.

The cloud isn't a unsuitable backup unless you are paying them and have a contract.  Otherwise, you are just putting your important data on 
* someone else's storage, 
* connected to someone else's computer, 
* on someone else's network, 
* inside someone else's building.
In short, "live by the cloud, die by the cloud".

RMS said it succinctly, "Cloud computing is careless computing." 
[https://www.networkworld.com/article/2228050/cloud-computing-is-careless-computing-and-chromeos-pushes-people-into-it-says-open.html](https://www.networkworld.com/article/2228050/cloud-computing-is-careless-computing-and-chromeos-pushes-people-into-it-says-open.html)

I fear that most of the world individuals and businesses don't understand the full risks with free cloudy services.  Sigh.  Talk with a lawyer over a beer about the negatives. It is scary.

---

