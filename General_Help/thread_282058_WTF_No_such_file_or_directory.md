---
title: "WTF? No such file or directory???"
date: 2006-10-22
forum: General Help
---

### Post by Kazade on 2006-10-22
Hey,

I've just replaced my Dapper install with a nice clean Edgy one, and everything seemed to work well, until I tried to install swiftfox. Swiftfox was installed into the /opt/swiftfox directory. But for some reason when I try to run it I get " /opt/swiftfox/swiftfox-bin: No such file or directory" the reason I'm posting here and not on the swiftfox forums, is that the file IS there. I can see it, I can tab-complete the filename, I can change its permissions, I just cant run the thing! 

Does anybody have any ideas?? I'm baffled (and frustrated)!

I'm running AMD64 Edgy, and i've chowned the file to me and given it full permissions, ubuntu still cant find it though :/

---

### Post by po0f on 2006-10-22
Kazade,

Post the output of:
```
$ echo $PATH
```

---

### Post by Kazade on 2006-10-22
Here it is:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

---

### Post by po0f on 2006-10-22
Kazade,

The reason it will not run is because the /opt/swiftfox directory is not in your PATH.  This is a list of directories to look for programs in when you type a command in the terminal.

To add /opt/swiftfox to your PATH, edit ~/.bashrc:
```
PATH="/opt/swiftfox:${PATH}"
```

You might have to log out and log back in for the changes to take effect.

Post back if you have problems.

---

### Post by Kazade on 2006-10-22
Thanks for the help, but im afraid its not that simple. Im calling the file directly (i.e going to the directory itself and trying to run it) not using the path. I've tried what you said but the same problem. Its happening to other files too, I installed wine, and it cant find /usr/bin/wine... yet its there :/

---

### Post by CatKiller on 2006-10-22
These are fairly wild stabs in the dark, but if the files aren't executable and you try to execute them, then you'll get the "file not found" error, since there's still no executable of that name to be found. Also, if you cd to a directory that isn't in your path and try to run something there, you'll need to use ./filename to show it that you mean "definitely the file in this directory".

It might be that neither of these is the problem you're facing, but it's the closest I come to knowledge about your situation. Sorry.

Good luck.

---

