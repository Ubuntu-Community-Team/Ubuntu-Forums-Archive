---
title: "How can I stop error messages from appearing in the console"
date: 2007-03-21
forum: General Help
---

### Post by Jimcanoa on 2007-03-21
Hello,
I'm recently getting a lot of errors when executing graphical apps such as gedit, for instance:

** (gedit:15637): WARNING **: invalid source position for horizontal gradient

The program works fine, but it's quite annoying to get all those error messages in the console, is there a way to tell the system to output those errors to a log instead of the console?

Thanks

---

### Post by dcstar on 2007-03-21
> **Jimcanoa said:**
> Hello,
I'm recently getting a lot of errors when executing graphical apps such as gedit, for instance:

** (gedit:15637): WARNING **: invalid source position for horizontal gradient

The program works fine, but it's quite annoying to get all those error messages in the console, is there a way to tell the system to output those errors to a log instead of the console?

Thanks

Simple, don't run them from a terminal, they are supposed to be run from a launcher.

---

### Post by Jimcanoa on 2008-02-15
It's almost one year ago that I asked this question, and I've learned much since. Not that you need to be an expert to answer to this question, but I think knowing how to do this may come in handy for some people. Dcstar reply wasn't satisfactory for me at the moment, since sometines you just need to launch a graphical application from the command line, for instance when you're working remotely on another machine with x11 port forwarding.

Now I know two ways, one consists of using nohup to launch a program, that is:
```
nohup gedit myfile &
```
Nohup will create a file (nohup.out) where it will store the output of the program it launched.
Another way is to manually redirect the output (both error and standard) to /dev/null:
```
gedit myfile >& /dev/null &
```

I hope this helps someone, I wish someone would have said this to me one year ago!

---

### Post by kesman on 2008-02-15
also, you could run the program with alt+f2, but the options you gave are much more advanced.

---

