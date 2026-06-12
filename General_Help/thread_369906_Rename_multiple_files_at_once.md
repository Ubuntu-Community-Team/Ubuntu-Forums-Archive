---
title: "Rename multiple files at once"
date: 2007-02-25
forum: General Help
---

### Post by shironeko on 2007-02-25
Ok, I've been searching and googling a bit but didn't find a clear answer. Here's my problem.

I got 29 images with random rames I want to rename to: X01.png X02.png X03.png ... X29.png
Where the value X is the name I want to give them.

I heard about commands like mmv or mv, but didn't find clear instructions to do this. It's only 29 files, I know that I could rename them all manually but** I want to learn how to do this.**

Thank you! ^^

---

### Post by jordilin on 2007-02-25
There are several programs to do it, but I wrote my own one with python. You can download it here:
[http://jordilin.wordpress.com/2006/11/11/howto-renaming-files/](http://jordilin.wordpress.com/2006/11/11/howto-renaming-files/)

---

### Post by shironeko on 2007-02-25
Ets de catalunya!? Gracies :P

(EN: Thanks)

EDIT: I modified the script a little bit for my own personal use so that the "_" doesn't display. I hope It's ok.

EDIT: It's ok, but I still got a problem. The filename I want is:

name01.png to name29.png

I managed to rename the files to:

name01.png .... name029.png

Ahrg But I want name29 not name029.... I'll have to learn some python to solve it next time by myself... Btw It's the first time I see a python script... doesn't look too difficult and looks rather interesting! I'll give it a try, but first I need your help to rename the files :P

---

### Post by highneko on 2007-02-25
For renaming X01.png, X02.png, X03.png:
```
[COLOR="DimGray"]# First test it. Maybe make backups or files for testing:[/COLOR]
x=1; for i in *.png; do d=$(printf "%02d " "$x"); echo "mv -i $i X$d"; x=$((x+1)); done
[COLOR="DimGray"]# Then rename if you want it:[/COLOR]
x=1; for i in *.png; do d=$(printf "%02d " "$x"); mv -i "$i" "X$d"; x=$((x+1)); done
```
That's for png files.

---

### Post by sysops on 2007-02-25
perl -e '$a="X0"; $a++,`mv -vi "$_" "$a.png"` for @ARGV' *png

---

