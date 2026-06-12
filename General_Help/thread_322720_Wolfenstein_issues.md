---
title: "Wolfenstein issues"
date: 2006-12-20
forum: General Help
---

### Post by GuitarHero on 2006-12-20
I installed wolfenstein and it's patch but it lacks sound.  Also I can't start it now.  After it installed it let me launch it, and i did and i saw it had no sound.  Now when i type et nothing happens.  Also clicking on the sh file doesn't work either.

Im runnin edgy.

---

### Post by po0f on 2006-12-20
GuitarHero,

Try running this command from the terminal:
```
[FONT="Courier New"]$ sudo dpkg-reconfigure dash[/FONT]
```
and answer "No".  Some games won't work under Edgy due to Dash being the default shell interpreter (as opposed to Bash).

---

### Post by GuitarHero on 2006-12-21
Thanks for replying.

That didn't do it.  When I type in et it says command not found, and when i click on the file it just kinda flashes then does nothing.

---

### Post by po0f on 2006-12-21
GuitarHero,

How did you install it?

---

### Post by xopher on 2006-12-21
> **GuitarHero said:**
> Thanks for replying.

That didn't do it.  When I type in et it says command not found, and when i click on the file it just kinda flashes then does nothing.

Command not found: This means you don't have a symbolic link to the 'et' program in your $PATH, eg. /usr/local/bin. Try running it in terminal where you installed it:

1. ```
cd /path/to/etinstallation/
```

2. ```
./et
```

This will probably give you more output on what's wrong with the installation.

---

### Post by GuitarHero on 2006-12-21
I got this:

./et: line 6: /home/ryan/enemy-territory/et.x86: Permission denied
./et: line 6: exec: /home/ryan/enemy-territory/et.x86: cannot execute: Success

---

### Post by GuitarHero on 2006-12-21
Now the program opens but sound still doesnt work.
When the game starts, this is something that looks like a problem:
```
Sys_LoadDll(/root/.etwolf/etmain/ui.mp.i386.so) failed:
"/root/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
```

---

### Post by lamego on 2006-12-21
Not a solution but a warning, playing games with root is a VERY BAD practice.

---

### Post by GuitarHero on 2006-12-22
Still need help...

---

### Post by GuitarHero on 2006-12-23
bump

---

### Post by GuitarHero on 2006-12-24
bump, someone help

---

### Post by Adramelech on 2006-12-24
I use this when et gets no sound: 

echo 'et.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss
echo 'et.x86 0 0 disable' > /proc/asound/card0/pcm0c/oss

---

### Post by GuitarHero on 2006-12-24
Nope that didnt do it either : /

I dont know why nothing works.

---

### Post by kr0n1x on 2006-12-26
try to reinstall it...reading this topic: [http://www.ubuntuforums.org/showthread.php?t=5246](http://www.ubuntuforums.org/showthread.php?t=5246)

---

### Post by misfito on 2007-01-09
> **lamego said:**
> Not a solution but a warning, playing games with root is a VERY BAD practice.

What do you mean by root? How do I avoid playing in root?

---

