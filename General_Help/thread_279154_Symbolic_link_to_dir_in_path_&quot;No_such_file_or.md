---
title: "Symbolic link to dir in path: &quot;No such file or directory&quot;"
date: 2006-10-17
forum: General Help
---

### Post by kalle314 on 2006-10-17
I have not messed with the path variable much before, and now I have run into trouble for the first time.

I compiled the latest version of antiword, and now I need to put the executable in the path of course.

First i tried to make a symbolic link to the executable in one of the directories in the path, "/usr/local/sbin/".
```
$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

$sudo ln -s /home/kalle/program/antiword-0.37/antiword /usr/local/sbin/antiword
```

but then i got this error:

```

$ antiword Desktop/test.doc
bash: /usr/bin/antiword: No such file or directory

```


(Note that it is looking in the /usr/bin/ directory for some reason.)

Still 
```
$ which antiword
```
results in 
```
/usr/local/sbin/antiword
```

and i can do 
```
$ /usr/local/sbin/antiword Desktop/test.doc
```

Instead i moved the executable to /usr/local/sbin, but now it cannot find the exacutable at all - "which antiword" results in nothing. I get the same result by moving it it "/usr/bin".

I'm really interested in knowing what is the reason for the errors I get.

---

### Post by kuja on 2006-10-17
Certainly sounds interesting. Assuming that the file that you're linking to is a script to run the binary, open it with a text editor and see if it does anything directory specific which would make it run into trouble. Also, try making a symlink to it in /usr/bin.

---

### Post by kalle314 on 2006-10-17
The problem is solved, though I don't know at all why I got the above errors. I made a few tests with a small helloworld test-program, and there the sym-link worked.

Then I tried a second time to make a symbolic link to my executable in "/usr/local/sbin" and this time it worked! Weird... 

Maybe there was something left from my previous install of antiword from the repositories, allthough i removed that completely.

I was trying to link to a binary by the way:
"antiword: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), for GNU/Linux 2.2.0, not stripped"

---

### Post by ansi on 2006-10-17
> **kalle314 said:**
> 
I was trying to link to a binary by the way:
"antiword: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), for GNU/Linux 2.2.0, not stripped"

Are your **really** need in symlink? Imho, it makes a small trash from installed system. As alternative without symlinks, you can use this method also:
```
export PATH=$PATH:/home/kalle/program/antiword-0.37/antiword
```

and call this program, practically, anywhere under your user account.

---

### Post by kalle314 on 2006-10-17
ansi: I guess you are right. It is easier to change the path in .bashrc than to have to look for symbolic links in /usr/local/sbin when if I want to remove something I installed.

Though at the moment I'm a bit reckless with my system and I don't really care if I mess something up, since Edgy Eft arrives any time now, and I'll do a fresh install then. :)

---

