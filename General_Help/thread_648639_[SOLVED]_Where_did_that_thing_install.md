---
title: "[SOLVED] Where did that thing install?"
date: 2007-12-23
forum: General Help
---

### Post by as0l0 on 2007-12-23
I'm not sure if i need help or if this a suggested improvement.

When installing applications, once the install is complete there doesn't seem to be any information on where that program installed to.  Where in the menu or where on the disk.  I have to take a guess about where in the menu I can now launch the program from.

Am I missing something?

---

### Post by gvoima on 2007-12-23
Well usually the programmers who do the program decides in which category the program belongs and those are usually pretty easy to guess, as there is not so many.

But the program binarys are installed into /usr/bin/ and /usr/share/applications/ holds the icons that resides in the menus, try and open one of them in a editor and you will see what I mean with categories ;)

All the other configuration files are normally kept in the users own home directory e.g. /home/user/.file.conf (or .directory) etc.

I hope this clarifys things a little..

---

### Post by oldos2er on 2007-12-23
If you're using Synaptic, go to Status, Installed, right-click on a package, choose Properties, then Installed Files.
 Most user-installed programs (the executables) go to /usr/bin .

---

### Post by as0l0 on 2007-12-23
ok, so you can find out (thankyou for the info's), but wouldn't it be more friendly...y'know to humans....if it popped up at the end of an install?

Find your app at Applications > Games
Files installed to /us/bin

---

### Post by zvacet on 2007-12-24
If you don´t see icon after install you can make it yourself.System>preferences>main menu>on the left side choose games and after that on the right new item.That will start launcher and you will see 

1. name = your game name
2.command = usr/bin/your game (in most cases)
3.icon = usr/share/pixmaps or usr/share/applications

You are done and you have icon under games.

---

### Post by as0l0 on 2007-12-24
thanks for the info's.

i could use you guys over in my other thread where i'm desperate for an idea.

[http://ubuntuforums.org/showthread.php?t=648693](http://ubuntuforums.org/showthread.php?t=648693)

---

### Post by Punk_Piranha on 2007-12-24
You know you can use the *whereis* command to show where a program is installed, right?

```

user@hp-laptop:~$ whereis firefox
firefox: /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/share/firefox /usr/share/man/man1/firefox.1.gz

```

---

### Post by burbankmarc on 2007-12-24
if all else fails here's the sure shot way to find what you need

```

which *program*

```

or

```
whereis *program*
```

or

```
locate *program*
```

and if all else fails, use find, but it's the slowest process

```
find / -iname "**program**"
```

---

### Post by zvacet on 2007-12-24
For** find** command go to the top of filesystem with **cd /** and after that 

```
sudo find / -name *program*
```

---

### Post by as0l0 on 2007-12-26
these are all technically sound solutions, but shouldn't there be a better way than having someone execute those commands?

anyway, i appreciate the help.

---

