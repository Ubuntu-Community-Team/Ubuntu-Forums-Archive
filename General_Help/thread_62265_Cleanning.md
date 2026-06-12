---
title: "Cleanning"
date: 2005-09-04
forum: General Help
---

### Post by ubuntuubuntu on 2005-09-04
Does someone know a software that deletes temporary internet files, recent files lists and other temp files in order to free space in disk? If you don't know a software that does it, do you know how to do it manually?
Thanks!

---

### Post by KingBahamut on 2005-09-04
rm all the files in the /tmp/ directory

apt-get clean
apt-get autoclean

cleans out unessecary stored debs in the apt cache folders.

---

### Post by ubuntuubuntu on 2005-09-04
[QUOTE=KingBahamut]rm all the files in the /tmp/ directory

apt-get clean
apt-get autoclean

cleans out unessecary stored debs in the apt cache folders.[/QUOTE]

Oops! I deleted the /tmp/ directory. I guess I shouldn't have done this. Now, when I start the computer, I get the following message: "mkdtemp: private socket dir: Permission denied"

What should I do? Please explain it in details.
Thank you!

---

### Post by KingBahamut on 2005-09-04
recreate the tmp directory 

mkdir /tmp

chmod it as 777 I think.

---

### Post by arnieboy on 2005-09-04
[QUOTE=KingBahamut]recreate the tmp directory 

mkdir /tmp

chmod it as 777 I think.[/QUOTE]
its not wise to delete the entire /tmp directory. u shd know what u are deleting.
ubuntuubuntu: can u log into gnome?

---

### Post by az on 2005-09-04
[QUOTE=ubuntuubuntu]Does someone know a software that deletes temporary internet files, recent files lists and other temp files in order to free space in disk? If you don't know a software that does it, do you know how to do it manually?
Thanks![/QUOTE]

You can go into your firefox preferences and set the size of your cache.  You can also remove every bit of personal information there, too.

---

### Post by skoal on 2005-09-04
[QUOTE=azz]You can go into your firefox preferences and set the size of your cache.  You can also remove every bit of personal information there, too.[/QUOTE]
Booyah! 'Azz' must be latin for 'A+ answer'.  I set mine to 1MB (from the default 50MB).  However, I have a broadband connection and frequent many sites, not just one.  If your browsing habits are similiar, I would follow azz's suggestion...

For further pruning, 'sudo apt-get distclean' or 'sudo apt-get clean' will work, removing all downloaded .deb packages.

Check the ~/.<hidden> folders like this: du -sh ~/.*
That will let you know if any one particular (hidden) path is chewing up hdd bits, which is common with games (needing to dl maps and such).

If you need to recreate your /tmp directory, I would do it as such:

sudo install -d /tmp -m 1777

* You will want that "sticky" bit in there.  Someone check that sudo cmd above for me.  I'm not in linux right now to test it...

\\//_

---

### Post by az on 2005-09-04
If you want to really be skimpy on disk space, check out your /var/log directory.  Logrotate compresses logs periodically, but they can build up and take several hundred megs over the months...

---

### Post by exhuma.twn on 2006-01-17
[QUOTE=skoal]Check the ~/.<hidden> folders like this: du -sh ~/.*[/QUOTE]

"du" is _very_ useful to find lost space. However, if you really need do find out where things go wrong I suggest you use "du -s" instead of "du -sh" as the "h" flag makes things easier to understand, but harder to compare with other folders.
My favourite command:

```
du -s * .* | sort -n
```

This will list _everything_ in the current folder including dot-files and sort them nicely by size.

Enjoy.

nb: Another nice gimmick is a tool called "[FSV]("http://fsv.sourceforge.net")". It will display your File-System grahically using OpenGL. But using "du" is much faster.

---

### Post by exhuma.twn on 2006-01-17
I could not help myself but write a small script that gives a du-ish output but nicer ;)

Leech here:
[http://www.albert.lu/michel/stuff/pydu.py](http://www.albert.lu/michel/stuff/pydu.py)

You can either give it a healthy "chmod +x" or run it using the python interpreter. It takes one optional argument: The folder to inspect. If that parameter is ommitted, it displays the current folder.

However, the values it returns for folder sizes seem to be slighltly smaller than the ones returned by "du". I suppose that's some sort of file system issue and how python vs du handles them. In any case I tend to trust "du" more than python. But as this script's main purpose is to find out which folder is the biggest/smallest it does not really matter that much.

If anyone can shed light on that, please feel free to teach us ;)

[edit]
Woooops. I accidentally uploaded it with a syntax error. It's corrected now.

---

