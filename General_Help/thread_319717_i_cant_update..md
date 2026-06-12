---
title: "i cant update."
date: 2006-12-16
forum: General Help
---

### Post by Tekovro on 2006-12-16
E: Malformed line 57 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by IusedTObeSOMEONEelse on 2006-12-16
Can you post your sources list so we can see where the problem is? Which ubuntu are running?

---

### Post by Tekovro on 2006-12-16
how so do i get that?

please help me get this resolved. i have to go to work and i dont want to come back to windows :(

---

### Post by Tekovro on 2006-12-16
i got the problem sorted out. but i cant change it unless i go into safe mode or whatever. is there a safe mode for linux?

i need to delete a line in the sources.list file but it wont let me replace it.

---

### Post by Topsiho on 2006-12-16
Safe mode: restart the computer in recovery mode.

You'll get a textscreen in which you can operate as root (see the #-prompt)

I hope this will do for you :)

After that restart the computer in the ususal mode. No good to be root longer than necessary.

Topsiho

---

### Post by Tekovro on 2006-12-16
thanks for your help! i finally managed to fix my problem by typing this in the terminal

```
gksudo gedit /etc/apt/sources.list
```

which allowed me to edit the sources.list file. im finally starting to understand a bit more how this works :)

I learned it from here

[http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")

---

