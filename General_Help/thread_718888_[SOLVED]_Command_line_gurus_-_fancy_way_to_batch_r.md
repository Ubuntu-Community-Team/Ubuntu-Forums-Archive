---
title: "[SOLVED] Command line gurus - fancy way to batch rename?"
date: 2008-03-08
forum: General Help
---

### Post by kooldino on 2008-03-08
Ok, so I have a bunch of files that are named "XX. Artist - Title.mp3"

where XX is a number.  Most of the numbers are unique.

I'd like to simply rename it "Artist - Title.mp3"

How can I do this?  Also, can you explain to me the idea behind it so that way I can adapt it to other things in the future?

---

### Post by sisco311 on 2008-03-08
```
 rename **-n** 's/\d{2}\W{2}(.+)\.mp3/$1\.mp3/' *.mp3
```The **-n** means that it's a test run and will not actually change any files. It will show you a list of files that would be renamed if you removed the -n.

[http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal](http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal)

EDIT:

GUI options:

in kubuntu(kde) you can use krename:
```
sudo aptitude install krename
```in ubuntu(gnome):
```
sudo aptitude install gprename
```in xubuntu(xfce) you can use Thunar(the default file browser) to rename multiple files.(select the files, right click -> rename)

---

### Post by kooldino on 2008-03-08
Beautiful.  This is exactly what I was looking for.  Time for me to start practicing reg ex.  Kudos to you, sir.

edit: re: your edit - I'll check those out too, but before I even bother with that, I want to get this whole reg ex thing down.  I'm overdue for learning the syntax, but I like how it works.

---

### Post by kooldino on 2008-06-03
Bump - I need a better guide to this.  I need to figure out what the "d" and "W" means, etc.  

I'm thinking d=digit and W=word, but it's not explained in the above link.

---

### Post by ghostdog74 on 2008-06-03
you can make use of field delimiters instead of that much regular expression.
```

# echo XX.\ Artist\ -\ Title.mp3 | awk -F"." '{$1="";sub(/^ +/,"");print}'
Artist - Title mp3

```

---

