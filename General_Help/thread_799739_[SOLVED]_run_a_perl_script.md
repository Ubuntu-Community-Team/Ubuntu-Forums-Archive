---
title: "[SOLVED] run a perl script"
date: 2008-05-19
forum: General Help
---

### Post by criptonite on 2008-05-19
Hi  I have downloaded a perl script called midi2hydrogen.pl which claims it will convert a midi drum track to a Hydrogen file.  That would be fantastic.  Trouble is, I haven't got a clue how to run a perl script.  It's currently sitting on my desktop.  I have tried running the file by typing perl midi2hydrogen.pl in the terminal but the terminal reports there is no such directory.  I have made the script an executable file and double clicked on it.  A terminal opens but then closes immediately.  

Fundamental stuff, I'm afraid.  Hope someone can help.

---

### Post by Monicker on 2008-05-19
You need to do either

```
perl midi2hydrogen.pl
```

or

```
chmod +x midi2hydrogen.pl
./midi2hydrogen.pl
```

---

### Post by criptonite on 2008-05-19
Have tried both of those but no luck.

Examples

david@david-desktop:~$ perl midi2hydrogen.pl
Can't open perl script "midi2hydrogen.pl": No such file or directory

david@david-desktop:~$ chmod +x midi2hydrogen.pl
chmod: cannot access `midi2hydrogen.pl': No such file or directory
david@david-desktop:~$ 

I should take a course in linux, I know

---

### Post by igster on 2008-05-19
This post might help you.

[http://ubuntuforums.org/showthread.php?t=473820](http://ubuntuforums.org/showthread.php?t=473820)

---

### Post by Monicker on 2008-05-19
> **criptonite said:**
> Have tried both of those but no luck.

Examples

david@david-desktop:~$ perl midi2hydrogen.pl
Can't open perl script "midi2hydrogen.pl": No such file or directory

david@david-desktop:~$ chmod +x midi2hydrogen.pl
chmod: cannot access `midi2hydrogen.pl': No such file or directory
david@david-desktop:~$ 

I should take a course in linux, I know

You are not running the commands in the directory to which you downloaded the file.  If the file is on your desktop then do this first.
```

cd Desktop
```

---

### Post by criptonite on 2008-05-19
Thank you, it tried to run the script this time but I'm missing some components after all.  Still, I learned something new.

---

