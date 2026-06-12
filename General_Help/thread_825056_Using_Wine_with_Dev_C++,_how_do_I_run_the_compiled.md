---
title: "Using Wine with Dev C++, how do I run the compiled?"
date: 2008-06-10
forum: General Help
---

### Post by lorgonjortle on 2008-06-10
I have just installed Dev-C++ under Wine, so now I can completely get rid of Windowz. I wrote a test program to see how well it worked... When I compiled it and tried to run it, it did nothing. I realized that it compiles it to a .exe. So, how would I go about running the program? I went in through Wine and tried to run it, but it didn't work. Is there some way to do it through the terminal or something? Like save it, then just compile/run it through the terminal? Thanks for any help!:guitar:

---

### Post by spacesearcher on 2009-06-18
I know this is an old post but it shows up in google. The best way I know how to test a program you just made is to open a terminal. then cd to the source folder where the .exe is then in terminal type:
wine yourprogram.exe
it will then run. so you have to do compile (ctrl f9) then open it up in the terminal.

---

### Post by abdurahman.r on 2011-06-25
there is an easy way to run it , just go /home/username/.wine/dosdevices/c:/Dev-Cpp
for me the directory for wine is in the  home file . 
you just need to run it separately through  brows c: drive then where you saved your project  and run it using wine .

---

