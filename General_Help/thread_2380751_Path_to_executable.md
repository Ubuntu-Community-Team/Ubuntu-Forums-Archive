---
title: "Path to executable"
date: 2017-12-21
forum: General Help
---

### Post by VanillaMozilla on 2017-12-21
For some reason bash is not seeing the whole path.  Here's the output:

$ fp
bash: /usr/bin/fp: No such file or directory
$ echo $PATH
/home/xxx/bin:/home/xxx/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/n
$ ls -Fal /usr/local/bin/fp
-rwxr-xr-x 1 root root 5092000 Oct  3 08:56 /usr/local/bin/fp*

Of course the command /usr/local/bin/fp works.  This is basic, but I'm a bit of a neophyte with bash.  What am I doing wrong?

---

### Post by faraco3 on 2017-12-21
```
[COLOR=#000000]bash: /usr/bin/fp: No such file or directory[/COLOR]
```[COLOR=#000000]

The path to ***fp ***program is wrong. It should be*** /usr/local/bin/fp*** and not /usr/bin/fp.

Thus, you don't have to add a new path for your fp executable in /usr/local/bin directory because every single executable in /usr/local/bin/ can be invoked from anywhere in the system without taking any extra steps.

Why?

```
$ echo $PATH
/home/xxx/bin:/home/xxx/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/n

```

Shows that ***/usr/local/bin ***is already in your $PATH. So, just put any executable in /usr/local/bin directory and you can invoke it like any other programs. (eg. ***ls *** that is located in /usr/bin/ directory)
[/COLOR]

---

### Post by VanillaMozilla on 2017-12-21
I didn't type the path.  It's the system default.  New system.

The directory is /usr/local/bin/, and the executable file is /usr/local/bin/fp .  /usr/local/bin/ is supposedly in the path, but bash doesn't search it.  It's looking in /usr/bin/ instead.

"Just leave your program there and you can access it without taking extra steps."

No, actually I can't, and that's the problem.  Reminder:  the command

fp does not work;
/usr/local/bin/fp works.

And /usr/local/bin/ is supposedly in the path.  What's wrong?

---

### Post by steeldriver on 2017-12-21
Probably the shell has hashed (remembered) an earlier location - try

```

hash -d fp

```

and then try executing the command again

---

### Post by VanillaMozilla on 2017-12-21
That did it, thanks.  It took two tries!  The first try returned 'fp not found'.  The second try succeeded.

Do I have to do this every time I install something in /usr/local/bin?  What do I have to do to keep the problem from recurring?

And by the way, isn't it supposed to search the WHOLE path by default?  Isn't that the point of having a path?

---

### Post by VanillaMozilla on 2017-12-21
OK, thanks.  That made me very happy that I got the compiler fully working.  :)

---

### Post by steeldriver on 2017-12-21
It shouldn't recur unless:

[LIST]
[*]you have an existing executable that's somewhere on your PATH and you run it (causing the shell to hash the location) 
[*]you then install an executable with the same name elsewhere and try to run THAT *from the same shell instance* 
[/LIST]
If you forget the hash -d trick, then simply starting a new shell should fix it

---

### Post by VanillaMozilla on 2017-12-21
That might explain it.  I installed the compiler from the repository (to an unknown location), and then uninstalled and reinstalleda later version to /usr/local/bin/  from the tar file.

---

