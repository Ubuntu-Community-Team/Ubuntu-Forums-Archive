---
title: "Command line java compiling"
date: 2005-08-14
forum: General Help
---

### Post by numberexhaust on 2005-08-14
Hey guys...
I just installed java from sun's website (so I could get SDK 5.0) and I wanted to know how to change the PATH variables (or whatever linux's equiv. is) so that I can run the compiler, etc via command line in the terminal.

Thanks a lot

---

### Post by lovebug356 on 2005-08-14
[QUOTE=numberexhaust]Hey guys...
I just installed java from sun's website (so I could get SDK 5.0) and I wanted to know how to change the PATH variables (or whatever linux's equiv. is) so that I can run the compiler, etc via command line in the terminal.

Thanks a lot[/QUOTE]
 If you installed the SDK 5.0 with apt-get all path setup was fine.

You now need this to add dir's to the path:
```
export PATH=/where/you/want:$PATH
```

---

### Post by numberexhaust on 2005-08-14
Thanks a lot... working fine now :)

---

### Post by numberexhaust on 2005-08-16
OKAY never mind about that... I ran that command and it worked fine, but when I exited the terminal the PATH variable reset itself to normal.  How do I make the change permanent?

---

### Post by lovebug356 on 2005-08-16
Then you need to add that command to your .bashrc file, if you use bash. this script is run every time you start your terminal.

vim ~/.bashrc  (or use another editor)
add the line above.
restart your terminal.

---

### Post by numberexhaust on 2005-08-16
nice... thanks a lot... now it works fine for real.

---

### Post by lovebug356 on 2005-08-16
no problem :-)

---

