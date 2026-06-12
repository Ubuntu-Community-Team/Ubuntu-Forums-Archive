---
title: "cant move file"
date: 2008-05-06
forum: General Help
---

### Post by darthphume on 2008-05-06
I'm very new to linux, im trying to move files to usr/local/games so i can host my gameserver and it won't let me, and using the terminal all the time to do it is really starting to annoy me, is there a faster way?

---

### Post by sstusick on 2008-05-06
Try 

> sudo mv /location/file name/ /usr/local/games

---

### Post by darthphume on 2008-05-06
i have done that, it worked, but it really slows me down having to use the terminal to move things, especially when theres allot of things to move, i have to move 100 mappack files...

edit: does that command move all contents of a directory.?

---

### Post by darthphume on 2008-05-06
mv: cannot stat `usr/home/null/linuxjampded': No such file or directory

i keep getting that, yet that is the correct file... null is my account name

---

### Post by sstusick on 2008-05-06
Oops my mistake. 

sudo mv /home/user/<file name>/ /usr/local/games

It should only move that one file. If you have multiple files you could drag them into the terminal after typing "sudo mv" and then at the end put the directory you wish to move the files to.

---

### Post by darthphume on 2008-05-06
bah i still get 

sudo mvmv: cannot stat `usr/home/null/linuxjampded': No such file or directory

---

### Post by darthphume on 2008-05-06
nevermind, works now, had to ad ''s for some reason

---

### Post by dbrine on 2008-05-06
can you get to the directory from the terminal panel? Linux is very picky about spaces, caps, etc. Personally I hate using the mv command. Darn thing has always given me problems. I use the cp (or scp) -r command. this will copy all directories and files. then you can remove the old directory using the command rm -rf /media/Games. I used the scp command (across network) for for 700gb of crap and cp for local HDD xfers. This may be the long way but it worked. Of course make sure you have permissions (another linux pain in the ###).



Ex: cp -r /media/Games /home/me/Games (LOCAL HDD)
Ex: scp -r /media/Games login@ipaddress:/media/Games (across network)


just me 2 cents...

---

### Post by erginemr on 2008-05-06
If you dislike using terminal to move files in your system, you can consider running nautilus (gnome's file manager) temporarily with root permissions via:
```
Alt+F2 -> gksu nautilus
```

and do whatever you want in your file system. 

Be careful though not to delete any system files / folders by mistake, and you should close the root nautilus window as soon as your job is done.

---

