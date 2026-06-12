---
title: "How do the terminal distinguish the run files"
date: 2013-09-27
forum: General Help
---

### Post by alex107 on 2013-09-27
I am using the terminal.
I have 2 files:
 run.sh which is a terminal script. It is run by "./run.sh";
 a.out which is a file compiled from c++ source code. It is run by "./a.out"

Now I change each file's name to "exec", both can be run by "./exec".
How does the terminal know if it is a executable file or just a script file? (It just read it and check? What if a file can be interpreted to both?)

---

### Post by 3rdalbum on 2013-09-27
The first line of a shell script identifies the program that can interpret it. A script is always ASCII data, an executable is always a binary file. The terminal can't tell if a file is really an executable, it just tries to run it regardless.

---

### Post by Habitual on 2013-09-27
> **alex107 said:**
> How does the terminal know if it is a executable file or just a script file?
it would be marked as executable by the OS.
```
ls -al file
```

---

### Post by Impavidus on 2013-09-27
It reads the magic number. Scripts start with **#!/path/to/interpreter**, executables start with **<del>ELF**. Usually at least.

---

### Post by alex107 on 2013-10-03
That's very odd.
I wrote the script using vim normally (no adding of character, just simple commands like ls, clear..). Then i chmod it to 775 (same as the a.out file)
And the terminal still knows!
I guess the the <del>ELF at the start of the executables explains it.

---

### Post by whitesmith on 2013-10-03
The "magic" is the *nix concept of modalities, one of which is executable```
chmod +x filename
```makes filename executable, along with the shebang, as **Impavidus** explained. Both are required, by the way.

---

### Post by Lars Noodén on 2013-10-03
If you don't specify a path to a script interpreter on the first line of your script it will get interpreted by whatever you are running at the time.  That's probably bash, since it's the default login shell.  

If you specify #!/bin/sh then you are running dash instead of bash.  The former is smaller and faster and POSIX compliant.  The latter is more useful for interactive sessions being bigger, slower and a superset of POSIX.

---

