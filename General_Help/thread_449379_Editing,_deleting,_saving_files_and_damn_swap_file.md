---
title: "Editing, deleting, saving files and damn swap files"
date: 2007-05-20
forum: General Help
---

### Post by moodly45 on 2007-05-20
Although I am a very proficient Windows user, I am fairly new to linux, in general however i have managed to get my head round the main basic concepts. 
I have been trying to setup up a webserver using ubuntu and have been happily following a step by step guide on 'The Perfect Setup' site.
I have run  into difficulty when trying to modify the host file.

[LIST]
[*]have succefully become root using 'su' command
[*]then attempted to edit host file using 'vi /etc/host'
[*]this is where the problems start. while trying to edit the file i found it very difficult to actually type in the modified values, its as if the keys on my keyboard dont work. after a bit of playing around i managed to edit the file successully (by typing into a text editor then pasting into host file) im sure theres an easier way than this!
[*]Right now the main issue. once i am done modifying the file, how do i save it?
I have tried just closing the window, but all this seems to achieve is creating a duplicate 'swap' file.
[*]I now have two duplicate swap files, and i understand i have to delete them, but how the hell do i do this? i assume there is a command but what is it? and how do i make sure that the final file i am left with is the correctly modified one? have tried to navigate to them using the GUI but cannot for the life of me find the stinking files!!?! ( i asume this is because the GUI doesn't know about my root priviledges)
[/LIST]

I know this is probably a really simple query, but please to not condemn me for my ignorance, i am a beginner after all! ;) Any help appreciated!
Cheers!!

---

### Post by PgR on 2007-05-20
When you've opened the file 
```
vi /etc/hosts
```
press i to use "insert" mode (which will allow you to use it like a normal text editor.
When you've made the modifications you desire, press
```
[escape] :wq [enter]
```
which will save and quit. If you want to exit without saving, then it's
```
[escape] :q! [enter]
```

---

### Post by moodly45 on 2007-05-20
Spot on! Thanks mate!
Am i correct in thinking that i can use 'rm' to remove the uneeded swap files?

---

### Post by PgR on 2007-05-22
Yes, rm <filename>

---

