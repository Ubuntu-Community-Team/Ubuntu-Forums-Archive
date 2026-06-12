---
title: "Wine File Recognition Error"
date: 2008-03-24
forum: General Help
---

### Post by Jookia on 2008-03-24
I was trying to run a program in wine, shortcuts won't work to it because it can't find a file to do with the program's C++ code BUT if I use terminal it works. So I'm wondering, is there a way to make it open the terminal and type it all in?

---

### Post by insineratehymn on 2008-03-24
Some programs in wine require it to be ran from its home folder, like:
/home/user/.wine/drive_c/Program\ Files/Adobe/Macromedia/dreamweaver.exe

If you try to run it from somewhere other than that, it freaks out.

What you may be able to do is write a simple shell script that declares itself a bash script, changes directories to the parent folder, then runs the required exe.

---

### Post by Jookia on 2008-03-24
****, after looking around I saw a 'wine' forum category.. Thanks also, but what's the extension to make exeuctable scripts?

Edit: Nevermind about that.

A launcher that runs the command 'wine "/home/jookia/My Programs/game/game.exe"' runs the program but the engine of the game says "Failed to open " then the filename.

BUT if I do the same in the terminal using this:

jookia@J-66291:~$ cd "My Programs/game"
jookia@J-66291:~/My Programs/game$ wine game.exe

It runs fine.

---

