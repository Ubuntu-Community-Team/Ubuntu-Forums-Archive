---
title: "copy a file to all folders and subfolders"
date: 2012-10-15
forum: General Help
---

### Post by sohlinux on 2012-10-15
How do I copy a file called readme.txt to all folders and sub folders in /home/test

thanks

---

### Post by Vaphell on 2012-10-15
try this
```
while read d; do cp readme.txt "$d"; done < <( find /home/test -type d )
```

---

### Post by sohlinux on 2012-10-15
> **Vaphell said:**
> try this
```
while read d; do cp readme.txt "$d"; done < <( find /home/test -type d )
```

perfect, and how about to copy a symbolic link to all folders so if I ever need to change the text in the readme file it will change all

thanks

---

### Post by Paddy Landau on 2012-10-15
That's a bit complicated. I would go for a slightly simpler solution as follows.
```
find /home/test -xdev -type d -exec cp readme.txt {} ';'
```
The [FONT="Lucida Console"]-xdev[/FONT] prevents it from traversing other file systems, e.g. If you have mounted a partition somewhere within [FONT="Lucida Console"]/home/test[/FONT]. Omit it if you do want it to traverse other file systems.

Making a symbolic link would be similar.
```
find /home/test -xdev -type d -exec ln readme.txt {}/readme.txt ';'
```

Warning: I am not at my computer right now so I cannot test this, but it should work.

---

### Post by Vaphell on 2012-10-15
so you need a single file and a bunch of symlinks? in that case replace cp with ln -s
```
ln -s "$PWD"/readme.txt "$d"
```
i used that PWD because my tests indicated that the parameter is pasted verbatim into symlink (eg *ln -s file /dir1/dir2* wont automagically create *file -> ../../file* in dir1/dir2 but broken *file -> file*)


i don't really see how a loop is more complicated than find -exec. It doe the same thing, amount of code is similar and it's easier to debug and expand if the need arises.

---

### Post by sohlinux on 2012-10-15
> **Paddy Landau said:**
> That's a bit complicated. I would go for a slightly simpler solution as follows.
```
find /home/test -xdev -type d -exec cp readme.txt {} ';'
```
The [FONT="Lucida Console"]-xdev[/FONT] prevents it from traversing other file systems, e.g. If you have mounted a partition somewhere within [FONT="Lucida Console"]/home/test[/FONT]. Omit it if you do want it to traverse other file systems.

Making a symbolic link would be similar.
```
find /home/test -xdev -type d -exec ln readme.txt {}/readme.txt ';'
```

Warning: I am not at my computer right now so I cannot test this, but it should work.

thanks I will give that a try :)

---

### Post by Paddy Landau on 2012-10-16
> **Vaphell said:**
> i don't really see how a loop is more complicated than find -exec. It doe the same thing, amount of code is similar and it's easier to debug and expand if the need arises.
You are right that there is not a huge difference. Using a single command is simpler to understand and therefore to debug, with fewer places to make mistakes — in that, I beg to differ from you.

---

### Post by Vaphell on 2012-10-16
*while read something; do ... done [COLOR="Blue"]< file[/COLOR] | [COLOR="DarkGreen"]< <( some_command )[/COLOR]* is as standard as it gets when it comes to traversing file or command output, after some thinking i agree that find is better in this case.
Syntax of find has its idiosyncracies as well so its not all roses but with *while* apprach one has to be more careful about caveats like delimiters or characters that can break things, should they appear.

---

### Post by Paddy Landau on 2012-10-16
> **Vaphell said:**
> Syntax of find has its idiosyncracies…
LOL, syntax of *every* Linux command has its idiosyncrasies!

---

