---
title: "How do I compile a program from the source?"
date: 2007-10-02
forum: General Help
---

### Post by Yes on 2007-10-02
I would like to make a small change in the kiba-dock source file dock.c.  I think I downloaded the source files when I ran the command 

```
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/ kiba-dock
```

Now I can't figure out where the files that I downloaded are.  Also, when I'm done editing the file, how do I compile it?  I have build-essentials installed and everything, but I'm not sure what file I would compile?  Or would I just compile one, and it would automatically compile all the rest?

Thanks.

---

### Post by bodhi.zazen on 2007-10-02
You probably downloaded to "kiba-dock" or ./kiba-dock

Hint : enter ls

OK, now cd kiba-doc and again ls, lets see what you have , source code, a binary, a patch, I hope a README ...

---

### Post by Yes on 2007-10-03
Well, I can't seem to find the files that were outputted when I ran that command.  Prehaps I didn't download them afterall?

---

### Post by distroman on 2007-10-03
If you paste that command into a terminal you'll get a folder in you're home directory called "kiba-dock".
[http://www.kiba-dock.org/](http://www.kiba-dock.org/)
Look at the wiki for compiling.

---

### Post by distroman on 2007-10-04
I was thinking ;-)
If it’s not working it might be because you need to install svn, anyway post you’re output from the terminal if you still got trouble.

---

