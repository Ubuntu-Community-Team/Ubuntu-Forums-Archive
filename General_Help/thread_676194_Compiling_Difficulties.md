---
title: "Compiling Difficulties"
date: 2008-01-23
forum: General Help
---

### Post by Andrew07 on 2008-01-23
For some strange reason Ubuntu (7.10) doesn't want to compile any software. I've tried three different .tar.gz's (flock, opera, and hamachai) to the same result. I have the build-essential package (and additionally devscripts and dh-buildinfo packages). 

I'll go through the process just incase.

Download the tar.gz
Extract said file
Navigate the the extracted directory (root terminal)
Enter ./configure command (Bash: ./configure: No such file or directory)
Enter make (make: *** No targets specified and no makefile found. Stop.)

It is the same with all three tar.gz's. Any idea what I might be doing wrong?

---

### Post by Nepherte on 2008-01-23
You don't need sudo rights for ./configure and make, only for make install/ checkinstall but that should not be the problem. Are you sure you're in the right directory?
In some cases you don't have to install the program in the first place, e.g. eclipse. Maybe you should also try to use the version in the repositories.

---

### Post by Nepherte on 2008-01-23
In case of opera, there is no configure and make file. To install it, just run
```
sh install.sh
```

But you can also already run opera by typing:
```
./opera
```

---

### Post by Keith Hedger on 2008-01-23
some sources use autogen.sh to create the configure script so look for that file too

---

### Post by Andrew07 on 2008-01-23
> **Nepherte said:**
> In case of opera, there is no configure and make file. To install it, just run
```
sh install.sh
```

But you can also already run opera by typing:
```
./opera
```

Worked in the case of opera, but the other two I still can't figure out. Tried searching for a .sh file and running it through the terminal (in the case of flock "sh run-mozilla.sh" did not work). 

Anything else I'm missing. I'd prefer to use flock (which is not in the repos) over Opera.

---

### Post by Nepherte on 2008-01-23
Here are some directions for flock:[http://brentroos.com/2006/07/24/install-flock-on-ubuntu/](http://brentroos.com/2006/07/24/install-flock-on-ubuntu/)
This is one of these programs you don't have to compile. You can simply "extract and run". The executable file to run is <flock directory/flock

---

### Post by Andrew07 on 2008-01-23
> **Nepherte said:**
> Here are some directions for flock:[http://brentroos.com/2006/07/24/install-flock-on-ubuntu/](http://brentroos.com/2006/07/24/install-flock-on-ubuntu/)
This is one of these programs you don't have to compile. You can simply "extract and run". The executable file to run is <flock directory/flock

Thanks.. and quick google search found a fix for hamachai. Remind me to use google more often ;).

---

