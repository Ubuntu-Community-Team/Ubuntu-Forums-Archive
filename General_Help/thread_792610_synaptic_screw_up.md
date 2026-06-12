---
title: "synaptic screw up"
date: 2008-05-13
forum: General Help
---

### Post by saltynay on 2008-05-13
I have somehow managed to corrupt my synaptic package manager :(. Every time I try to install or remove a package through terminal sudo apt-get install as well it says;

dpkg: failed to open package into file /var/lib/dpkg/available for reading no such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

Any help would be much appreciated this started occurring after trying to add AWN toolbar :confused:

---

### Post by hermes0710 on 2008-05-13
Is there a folder /var/lib/dpkg/available?

---

### Post by kesman on 2008-05-13
Something else is locking the directory. What if you type in terminal:
```

sudo apt-get update

```
does it give the same error?
You can browse trough your processes with
```

ps -A | more

```
and if you see something with "update" or "apt" or "synaptic", memorize the four-digit number in front of it and kill the process with
```

sudo kill -9 number

```
with number being the number of the process.

---

### Post by saltynay on 2008-05-13
[IMG]http://i205.photobucket.com/albums/bb223/Saltynay/Screenshot.png[/IMG] thats the file it is referring to

---

### Post by saltynay on 2008-05-13
Tried to use the solution here:
[http://ubuntuforums.org/showthread.php?p=4933498](http://ubuntuforums.org/showthread.php?p=4933498)
Didn't work

can someone please navigate to this section of there computer and tell me if my screenshot is missing any files

---

### Post by saltynay on 2008-05-13
ok after using my other linux machine I found there are two files missing available and available-old so I emailed myself these files and am now copying them over to the correct folder hopefully it will work

edit: it worked :D:D:D happy days

---

