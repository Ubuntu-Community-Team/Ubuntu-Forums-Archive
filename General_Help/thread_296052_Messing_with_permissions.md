---
title: "Messing with permissions"
date: 2006-11-09
forum: General Help
---

### Post by blueturtl on 2006-11-09
Hi.

I was just wondering about something. Firstly, I keep a large collection of our music on my hard-disk for easy playback. Now since we have multiple users I have to set the permissions after each time I rip a CD to include the proper rights for my wife as well. I do this using commandline using the recursive chmod command. However I have somewhat of a puzzle:

I want to change the group of all the files and folders.
I want to change the permissions for all the files.
However the folders are required to have the x (opening a folder is equivalent to executing I guess). Now when I do a recursive permissions change (chmod -R u+x,g+x music) the music files in the folders also inherit the x which is not needed.

The question plain and simple: how do I recursively change the permissions so that only the files in the folders are affected and not the folders containing them?

---

### Post by Jussi Kukkonen on 2006-11-09
use capital "X" instead of "x" as the permission.

---

