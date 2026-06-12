---
title: "Program Instillation"
date: 2008-03-29
forum: General Help
---

### Post by keenish27 on 2008-03-29
I've been using ubuntu for about a year now and I have just recently come across a problem.  Where are the program files stored when you install a program.

For example, i installed transmission and i wanted to use that to d/l a torrent.  However, my default is set to bittorrent and i have no idea where transmission is stored so that i can tell the browser to use it.

Knowing this information would have been handy in some other situations too.

Anyway, thanks for the help in advance.

---

### Post by Whiffle on 2008-03-29
The easy way to find the executable of a program is to open up a terminal, and type

```

which  nameofprogram

```

For example, on mine if I'm looking for pidgin, I can do 
```

[andy@blacktop ~]$ which pidgin
/usr/bin/pidgin

```

But, program executables are usually stored in /usr/bin, and their associated files in /usr/share, although there are plenty of exceptions.

---

### Post by nickoli_02 on 2008-03-29
All binaries should be stored in /bin, /usr/bin, or /usr/local/bin, I believe. Transmission is probably in one of the latter two folders.

---

### Post by keenish27 on 2008-03-29
Thanks so much for the help.  I've found it.

Its in the /usr/bin folder.

Only tricky thing was, its under transmission-gtk not just transmission.

Thanks again

---

### Post by fela on 2008-03-29
you can set preferences about specific apps and associated files/tasks using System > Preferences > Preferred applications.

---

### Post by ellalan on 2008-03-29
Hi fela
I copied your bunny, Thanks for that.

---

### Post by fela on 2008-03-29
> **ellalan said:**
> Hi fela
I copied your bunny, Thanks for that.

cool

i copied it from someone else actually...(although can't remember who :S)

and just to note, you should center the bunny in you signature and have the 'world domination' thingy with it, so other people know what to do...:)

---

### Post by ellalan on 2008-03-29
Hi fela
You beat me to it, I have been trying to rectify the mistake and made amends, it is very nice.
Thanks again.

---

