---
title: "[SOLVED] Favourite Apps list"
date: 2008-05-19
forum: General Help
---

### Post by neur0 on 2008-05-19
Is there any way to make a custom list of installed applications (favorite apps that don't come with Ubuntu) and then have them auto-install on a new system? I think I remember some method of copying lines from the dpkg -l output and pasting it in a text file, but I forgot about it.

---

### Post by zvacet on 2008-05-19
I don´t know if this will be what you want but anyway.... Type in terminal

```
dpkg --get-selections > installed-software
```

and you will find text file in your home directory.You can e-mail it to yourself(I think you have gmail,yahoo...address).When you download it to your new system (in home directory) type

```
dpkg --set-selections < installed-software
```

```
dselect
```

---

### Post by badactress on 2008-05-19
I've got a tiny simple script that looks something like:

```
#!/bin/bash/
aptitude install banshee anjuta soundconverter vlc deluge
```

etc..etc... just basically aptitude with all the stuff I want installed after it.

When I do a fresh install I can run the script & 10 mins later everything I need is there :)

Even just keeping it in a text file & pasting it into a terminal after a sudo aptitude (or apt-get) would work.

---

### Post by neur0 on 2008-05-19
Thanks for the reply,

Ok, that first line got me a list, and I assume I can edit it as I only need lines with Apps I installed after the OS installation (probably about 20 favourite apps).
The question is: what to do after "dpkg --set-selections < installed-software" ?
Will that line install the software or just make selections ?

Edit: Marking the thread as solved as Ill be using the badactress' solution since it does what I need.

---

