---
title: "Can't run binary files in edgy?"
date: 2006-11-04
forum: General Help
---

### Post by Casey on 2006-11-04
Can anyone else not run binary files in edgy?

I get "no such file or directory" even when the file is clearly there.

E.G.

```

:~/savage$ ls
agp_error.txt           editor.sh  libs          savage.bin      updater
commander_controls.txt  eula.txt   licenses.txt  silverback.bin
dedicated_server.sh     game       logo.png      uninstall
editor                  icon.xpm   savage        update
:~/savage$ ./silverback.bin 
bash: ./silverback.bin: No such file or directory
:~/savage$ 

```

I can run scripts that call silverback.bin, but the script will also fail because it will say "no such file or directory."  The same thing occurs for savage.bin.

---

### Post by CatKiller on 2006-11-04
Have you made it executable? If not, then there will be no executable file of that name, hence "no such file".

---

### Post by ~LoKe on 2006-11-04
```
sudo chmod +x silverback.bin
```

---

### Post by taurus on 2006-11-04
```
ls -la
```
will tell you much more...

---

### Post by Casey on 2006-11-04
It is executable.  That's what baffles me.

---

### Post by Casey on 2006-11-04
-rwxrwxrwx 1 user user  801537 2006-11-04 13:55 silverback.bin


777'd it just to check

:~/savage$ ./silverback.bin 
bash: ./silverback.bin: No such file or directory
:~/savage$ ls -l silverback.bin 
-rwxrwxrwx 1 anna anna 801537 2006-11-04 13:55 silverback.bin

---

### Post by CatKiller on 2006-11-04
> **Casey said:**
> It is executable.  That's what baffles me.

Maybe it's calling some other file that isn't there? I have no idea how binary files work.

---

### Post by taurus on 2006-11-04
```

ls -la
file silverback.bin

```

---

### Post by Casey on 2006-11-04
x:~/savage$ file silverback.bin 
silverback.bin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.0.30, dynamically linked (uses shared libs), for GNU/Linux 2.0.30, not stripped

---

### Post by taurus on 2006-11-04
And what about the "ls -la"?  This is like trying to pull teeth here!!!

Also, what is the output of 

```
ldd silverback.bin
```

---

### Post by Casey on 2006-11-04
Speaking of which, you can actually get this file (well, the game so this directory) from:
[http://www.happypuppy.com/s2games/Savage_with_sep3t.run]("http://www.happypuppy.com/s2games/Savage_with_sep3t.run")

It's been released for free by the company that made it.

---

### Post by Casey on 2006-11-04
:~/savage$ ls -la silverback.bin 
-rwxr-xr-x 1 anna anna 801537 2006-11-04 13:55 silverback.bin


$ ldd silverback.bin 
/usr/bin/ldd: line 171: /lib/ld-linux.so.2: No such file or directory
ldd: /lib/ld-linux.so.2 exited with unknown exit code (127)


Looks like the ldd error might be getting us somewhere.

---

### Post by Casey on 2006-11-04
:~/savage$ ls /lib/ld-
ld-2.4.so             ld-linux-x86-64.so.2

I should have specified, using x86-64

:~/savage$ ls -la /lib/ld-*
-rwxr-xr-x 1 root root 119448 2006-10-10 09:27 /lib/ld-2.4.so
lrwxrwxrwx 1 root root      9 2006-11-04 05:23 /lib/ld-linux-x86-64.so.2 -> ld-2.4.so

---

### Post by taurus on 2006-11-04
> **Casey said:**
> :~/savage$ ls /lib/ld-
ld-2.4.so             ld-linux-x86-64.so.2

I should have specified, using x86-64

:~/savage$ ls -la /lib/ld-*
-rwxr-xr-x 1 root root 119448 2006-10-10 09:27 /lib/ld-2.4.so
lrwxrwxrwx 1 root root      9 2006-11-04 05:23 /lib/ld-linux-x86-64.so.2 -> ld-2.4.so
If you want to run 32bit binaries in 64bit environment, you MUST install all those 32bit libraries first!!!  That's your problem right there.  You don't have the right library to run that file...  So, you can use synaptic and search for those 32bit libraries then.

---

### Post by Casey on 2006-11-04
Gotcha

Installed the 32bit ld-linux library (through 32bit c++ libs) and now i'm working on tracking down dependencies.  Thanks!

---

### Post by taurus on 2006-11-04
> **Casey said:**
> Gotcha

Installed the 32bit ld-linux library (through 32bit c++ libs) and now i'm working on tracking down dependencies.  Thanks!
Good luck.

---

### Post by nemoder on 2007-02-08
the game ships with all the libs you need, just run it like this:

LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./silverback.bin "$@"

---

