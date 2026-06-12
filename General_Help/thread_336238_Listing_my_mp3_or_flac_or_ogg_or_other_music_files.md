---
title: "Listing my mp3 or flac or ogg or other music files"
date: 2007-01-11
forum: General Help
---

### Post by andybleaden on 2007-01-11
Hi 

When I used to use windows I had a neat ( for windows anyway) little programme that would list the contents of a folder and produce a report of what was in it and any subdirectories. The was good for cataloging my mp3 and music collection created a neat list of files. I did not need info relating to id3 tags etc just name of folder eg Jimi Hendrix and the files contained within it eg Track1.mp3, track2.mp3,cover.jpg

Now then I have had a search around and maybe using the wrong words but am surprised to find nothing out there in linux land

I use dapper and I am not good at command stuff so please clear and slow. Assume I know nothing and I can only surprise!

Any help would be gratefully received. Either to a topic where this is covered or to a programme etc

Andy

---

### Post by Elim on 2007-01-11
Hmm.  Well, this is not the ideal solution, but in a pinch the Search function (Places --> Search for Files...) might provide some of the functionality that you're looking for.  Limit your search to, say, /home/Andy/Music/Hendrix and search for *.mp3.  Not perfect, I know, but I can't think of any programs that do what you're talking about...

---

### Post by andybleaden on 2007-01-11
Cheers for getting back to me so soon on that. I will give that a try . Any other help would be gratefully received

Andy

---

### Post by ajgreeny on 2007-01-11
Do you want a report you can print, or just a listing of the files in a folder?  You could always use the terminal command ls -1l.  This will list the files in columns, one file per line, with the details of size and date.  The folders in that folder will be shown blue and the files will be a variety of colours depending on what type they are.

If you want to print out this it is easy enough to do it by copying the output to a wordprocessor, or if it all fits in one terminal just print that.  There may be some way to print all the output that overflows from the window showing but I don't know how to do that.  I suspect someone else may know, however.

---

### Post by Elim on 2007-01-11
> **ajgreeny said:**
> Do you want a report you can print, or just a listing of the files in a folder?  You could always use the terminal command ls -1l.  This will list the files in columns, one file per line, with the details of size and date.  The folders in that folder will be shown blue and the files will be a variety of colours depending on what type they are.


Is there a way to list not only all the files and folders in a dir but also the files in the subfolders?  Something like this:

user@Music/Hendrix: ls -l -special_flag_for_listing_subfolder_contents
Album 1 (Folder)
     Track1.mp3
     Track2.mp3
     ...
Album 2 (Folder)
     Track1.mp3
     ...

---

### Post by ajgreeny on 2007-01-11
If the mp3 files are all in a folder called music or mp3 or something you can just change to that folder (cd music or cd mp3) then do the same command I gave but add R to the end.  That will list recursively all the files in that music or mp3 folder, including the subfolders.  Give it a try!

If you have all your mixed music files (mp3 or flac or ogg) in one folder, then everything will be shown.  It could be worth considering this when you set up your /home file system.

---

### Post by Theimon on 2007-01-11
Or take a look in Synaptic for mp3report. Scans the folders you enter after the command and can generate a big html list of what's what including duration of songs, the amount of songs etc.

---

### Post by ajgreeny on 2007-01-11
Never seen or heard of mp3report, but what a find!  Thanks a million.  Is there anything like it for ogg or flac files that you know of;  I can't find anything.

---

### Post by Theimon on 2007-01-12
I'm not sure, I don't have a lot of lossless files, so I can't really help you there, sorry.

---

### Post by ajgreeny on 2007-01-13
Don't know why I forgot about it but you should also remember the command:-
locate *.mp3 (or *.ogg, *.flac)

---

