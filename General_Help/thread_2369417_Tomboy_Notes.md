---
title: "Tomboy Notes"
date: 2017-08-22
forum: General Help
---

### Post by jim_deadlock on 2017-08-22
I've been using tomboy for years without any problems. I'm now running 17.04 and installed tomboy from the repo as usual, but it seems to be broken:

```
# tomboy

Unhandled Exception:
System.BadImageFormatException: Could not resolve field token 0x04000001
File name: 'Tomboy'
[ERROR] FATAL UNHANDLED EXCEPTION: System.BadImageFormatException: Could not resolve field token 0x04000001
File name: 'Tomboy
```

On further investigation it seems that tomboy has become a horrific windows app running under mono. What happened? Or was it always like this and I just didn't notice?

---

### Post by again? on 2017-08-22
Tomboy has always used mono to my knowledge,
so you get that extra layer where errors can occur.

Always avoided applications using mono but try gnote(Tomboy clone not using mono).
Don't know the differences but works for simple note taking 
and you can import Tomboy notes.

---

### Post by jim_deadlock on 2017-08-22
Thanks guber2, that's perfect, it even looks the same!

---

### Post by again? on 2017-08-22
No problem.
Have used gnote to document Ubuntu error fixes and customisations since 2009 without problems
If you want to backup, the files are stored @ ~/.local/share/gnote.

---

### Post by jim_deadlock on 2017-08-22
I've just been copying them over, works like a charm and couldn't be simpler. Awesome.

Re my original problem, I think it must be due to the fact that I force-installed a newer mono version recently so that probably broke tomboy. Glad it happened now :)

---

