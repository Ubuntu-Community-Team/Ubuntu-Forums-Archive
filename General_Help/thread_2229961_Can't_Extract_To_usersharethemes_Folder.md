---
title: "Can't Extract To user/share/themes Folder"
date: 2014-06-16
forum: General Help
---

### Post by jooge on 2014-06-16
So I just upgraded to ubuntu 14.04 last night and now I cant seem to extract themes (or icons for that matter) to my user/share/themes or user/share/icons folders like I was able to without issue with 12.04. What can I do?

It says:

Extraction Not Preformed

You do not have the right permissions to extract in the folder "themes"

---

### Post by deadflowr on 2014-06-16
Are these folders in your home folder?

(I ask because of the user/share designation,
if you meant /usr/share, then you'd need sudo to write to it)

---

### Post by jooge on 2014-06-16
> **deadflowr said:**
> Are these folders in your home folder?

(I ask because of the user/share designation,
if you meant /usr/share, then you'd need sudo to write to it)

Yes I meant /user/share not ~.icons. How do I write that sudo command? Thanks

---

### Post by deadflowr on 2014-06-16
one of two ways would be
graphically first
```
 gksu nautilus
```
then go to the side panel and click "Computer(or file system, whichever is listed)
then go to the directory home . then your username > then Downloads > find the file.
double click should ask to extract, then find the location you need to extract it to, and extract.

From a command line
It depends on the file.
An example of extracting a bz2 tar ball into that directory would be
```
sudo tar -xjvf file.tar.bz2 -C /usr/share/themes
```
a quick breakdown
sudo gives you root
tar is the command
-xjvf is the options of the command
file.tar.bz2 is the file that the command will run for.
and the -C option tells it to extract into the succeeding directory /usr/share/themes.

This is basic tar extraction, though it depends on the tar ball type.
This might give you some help on more about that
[http://www.cyberciti.biz/faq/tar-extract-linux/](http://www.cyberciti.biz/faq/tar-extract-linux/)

I don't know if any of this will be helpful.
Maybe?

---

### Post by jooge on 2014-06-16
> **deadflowr said:**
> one of two ways would be
graphically first
```
 gksu nautilus
```
then go to the side panel and click "Computer(or file system, whichever is listed)
then go to the directory home . then your username > then Downloads > find the file.
double click should ask to extract, then find the location you need to extract it to, and extract.

From a command line
It depends on the file.
An example of extracting a bz2 tar ball into that directory would be
```
sudo tar -xjvf file.tar.bz2 -C /usr/share/themes
```
a quick breakdown
sudo gives you root
tar is the command
-xjvf is the options of the command
file.tar.bz2 is the file that the command will run for.
and the -C option tells it to extract into the succeeding directory /usr/share/themes.

This is basic tar extraction, though it depends on the tar ball type.
This might give you some help on more about that
[http://www.cyberciti.biz/faq/tar-extract-linux/](http://www.cyberciti.biz/faq/tar-extract-linux/)

I don't know if any of this will be helpful.
Maybe?

It was. Your first option worked like a charm. Thanks my friend.

---

### Post by deadflowr on 2014-06-16
If the solution works for you, then
[Please mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

