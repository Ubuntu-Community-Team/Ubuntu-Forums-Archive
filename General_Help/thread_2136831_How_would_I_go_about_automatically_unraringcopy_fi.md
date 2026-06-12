---
title: "How would I go about automatically unraring/copy files?"
date: 2013-04-18
forum: General Help
---

### Post by roseysdaddy on 2013-04-18
First off, I am very new to linux, but was able to setup Ubuntu server by using many tutorials and a whole lot of googling, but im still very much a noob.
I am running qbitTorrent-nox (the webui) and it has an option for "Run an external program on torrent completion" but I don't think that will encompass what I'm attempting to do.
What I would like is a script or cron job or whatever is the correct/best route to:
1. unrar any completed torrent to a temp folder
2. if the completed torrent wasnt a series of rar's but perhaps an avi, mkv, or mp4 file, then to copy, not move, that file to a temp folder.
Any help in the right direction would be very much appreciated.

---

### Post by Vaphell on 2013-04-18
do you have have separate directories for in-progress and completed downloads? If you have everything in one place it's hard to differenciate if the file is in its final form or not.

Files in ready-to-use video formats look like a job for hardlinks (they work only in the scope of a single partition). When you hardlink a file you create another filesystem entry for it (inode) , so it can exist in 2 different places and/or with 2 different names at once without data duplication. Only after the last instance of the file is deleted, it's deleted permanently. On the other hand this means if you plan to modify the files in any way, hard links  can be bad idea (it's the same file so all instances are changed, both 'source' and 'copy')

this will create additional handle for $file in $dest:
```
ln -t "$dest" "$file"
```
combined with *find* searching for all files with given extensions 
```
src="$HOME/my_downloads"
dest="$HOME/temp"
find "$src" -regextype posix-extended -iregex '.*[.](avi|mkv|mpe?g|mp4|mov)$' -type f -exec ln -t "$dest" "{}" \;
```
or
```
while read -rd $'\0' f
do
  ln -t "$dest" "$f"
done < <( find "$src" -regextype posix-extended -iregex '.*[.](avi|mkv|mpe?g|mp4|mov)$' -type f -print0 )
```
if hardlink is not suitable for whatever reason just replace *ln* with *cp* or whaterver.


unraring to directory should work in similar way.
```
find "$src" -iname '*.rar' -type f -exec unrar x -ad "{}" "$dest" \;
```
or
```
while read -rd $'\0' f
do
 unrar x -ad "$f" "$dest"
done < <( find "$src" -iname '*.rar' -type f -print0 )
```

---

### Post by bcschmerker on 2013-04-18
> **roseysdaddy said:**
> First off, I am very new to linux, but was able to setup Ubuntu server by using many tutorials and a whole lot of googling, but im still very much a noob.
I am running qbitTorrent-nox (the webui) and it has an option for "Run an external program on torrent completion" but I don't think that will encompass what I'm attempting to do.
What I would like is a script or cron job or whatever is the correct/best route to:
1. unrar any completed torrent to a temp folder
2. if the completed torrent wasnt a series of rar's but perhaps an avi, mkv, or mp4 file, then to copy, not move, that file to a temp folder.
Any help in the right direction would be very much appreciated.
The unpacking of a BitTorrent RAR may be impossible under LinUX.  The Roshal Archive process (after inventor Evgeniy Lazarevich Roshal) is closed-source, and [RARLab](http://www.rarlab.com/) currently offers its applications only in Microsoft® Windows® 6-up, with Release 4.20 being available for Windows® Se7en™ Service Pack 1 7.0.8001, Windows® 8ight™ 8.0.10000, Windows® Server 2008 Release 2 Service Pack 1 6.1.7601, and Windows® Server 2012 8.0.10000.

Resources in LinUX may be available for the old Microsoft® Audio Video Interleave format, which is similar to Resource Interchange File Format from 1991.  The [Matroška Media Container](http://matroska.org/) is open-source.  The Moving Picture Experts Group MPEG-4 Part 14 format is supported by open-source software.

---

### Post by lisati on 2013-04-18
> **bcschmerker said:**
> The unpacking of a BitTorrent RAR may be impossible under LinUX.  The Roshal Archive process (after inventor Evgeniy Lazarevich Roshal) is closed-source, and [RARLab](http://www.rarlab.com/) currently offers its applications only in Microsoft® Windows® 6-up, with Release 4.20 being available for Windows® Se7en™ Service Pack 1 7.0.8001, Windows® 8ight™ 8.0.10000, Windows® Server 2008 Release 2 Service Pack 1 6.1.7601, and Windows® Server 2012 8.0.10000.

In Ubunutu, we have the [unrar]("https://help.ubuntu.com/community/FileCompression#Rar") command.

---

