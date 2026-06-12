---
title: "Can one program/script control another?"
date: 2008-02-17
forum: General Help
---

### Post by ed-koala on 2008-02-17
I'm looking for a program or script that will, at a certain interval, send a quit command to another program.  I am NOT wanting to end process, just make the program quit as if you selected "quit" from the program manually.  If I end process, the running program will not store data, so the quit option is essential. I know a script can easily start a program, and kill a process, but can someone point me in the right direction here?

---

### Post by SpaceTeddy on 2008-02-17
in short - a programm can be controlled by another programm..

how ? well, **it depends** on the programm. there are programms that can receive signals, and there those that cannot... what exact program are you looking to controll ?

---

### Post by russell.h on 2008-02-17
If you are going to be writing both programs the best (not the easiest) way to do this is using sockets. That way the programs don't have to even be on the same computer. Which is just good for scalability/portability.

Or you could look in to this sort of thing (which could apply even if you aren't writing the program being controlled, depending on the program): [http://www.linuxhq.com/guides/LPG/node11.html](http://www.linuxhq.com/guides/LPG/node11.html)

---

