---
title: "Bash says &quot;no such file&quot; but the file is there !"
date: 2007-08-08
forum: General Help
---

### Post by Bachstelze on 2007-08-08
```

kwesi@kwesi-desktop:/opt/shake-v4.00.0607/bin$ ls -l
total 320
-rwxr-xr-x 1 root root  20173 2005-06-09 03:53 mkpak
-rwxr-xr-x 1 root root    965 2005-06-09 03:53 shake
-rwxr-xr-x 1 root root  77456 2005-06-09 03:53 shkv.exe
-rwxr-xr-x 1 root root 174188 2005-06-09 03:53 shkx.exe
-rwxr-xr-x 1 root root    967 2005-06-09 03:53 tshake
-rwxr-xr-x 1 root root  32856 2005-06-09 03:53 tshkx.exe
kwesi@kwesi-desktop:/opt/shake-v4.00.0607/bin$ ./shkx.exe
-bash: ./shkx.exe: No such file or directory
```

Pretty self-explanatory. The file is *not* a Windows executable, it works just fine on my other systems. Anyone has ever seen this ?

---

### Post by apetresc on 2007-08-08
That truly is bizarre. Since this is Shake, do you have the /usr/lib/libstdc++.so.5 library?

---

### Post by bashologist on 2007-08-08
If the executable is outputting that message maybe to trick you then try:
```
./shkx.exe > ~/test.txt; cat ~/test.txt
```
Maybe try entering random parameters:```
./shkx.exe --help
```
Maybe check what type of file it is would help:
```
file shkx.exe
```
Try entering the full path like this:
```
/opt/shake-v4.00.0607/bin/./shkx.exe
```

---

### Post by Bachstelze on 2007-08-08
As I said, the executable works just fine on my other systems. But when I try to do the exact same thing on that particular one - which is not mine by the way but never mind -, Bash throws this error.

And yes, libstdc++5 is installed.

---

### Post by ljkwesi on 2007-08-08
Hi,

Actually it's on my system that Shake won't run... HymnToLife is helping me figure this out since I'm totally new to Ubuntu.

@AdrianP
I checked concerning the libs, they are installed so it shouldn't be the problem.

@bashologist
I tried the different commands you gave me and the results are :

```
kwesi@kwesi-desktop:~/Desktop/shake/bin$ ./shkx.exe > ~/test.txt; cat ~/test.txt
bash: ./shkx.exe: No such file or directory

kwesi@kwesi-desktop:~/Desktop/shake/bin$ ./shkx.exe --help
bash: ./shkx.exe: No such file or directory

kwesi@kwesi-desktop:~/Desktop/shake/bin$ file shkx.exe
shkx.exe: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), stripped

kwesi@kwesi-desktop:~/Desktop/shake/bin$ /home/kwesi/Desktop/shake/bin/./shkx.exe
bash: /home/kwesi/Desktop/shake/bin/./shkx.exe: No such file or directory
```

I'm lost...

---

### Post by lambros on 2007-08-08
I think I've seen this kind of thing before.  I'm guessing that the phrase "no such file" doesn't refer to the file "./shkx.exe" but, instead, some *other* file that shkx.exe (or the shell) tries to access.  I'd be inclined to run 'strace' against it, to see where the "no such file" is actually coming from.

Lambros

---

### Post by ljkwesi on 2007-08-08
I'm not sure if this is the proper way to "strace" but here's what I get :

```
kwesi@kwesi-desktop:~/Desktop/shake$ strace bin/shkx.exe
execve("bin/shkx.exe", ["bin/shkx.exe"], [/* 31 vars */]) = -1 ENOENT (No such file or directory)
dup(2)                                  = 3
fcntl(3, F_GETFL)                       = 0x8002 (flags O_RDWR|O_LARGEFILE)
fstat(3, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 1), ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2b8a2b597000
lseek(3, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: No such file or di"..., 40strace: exec: No such file or directory
) = 40
close(3)                                = 0
munmap(0x2b8a2b597000, 4096)            = 0
exit_group(1)                           = ?
Process 13451 detached
```

... I think that even in chinese I'd understand better what is said here...

---

### Post by nine01a on 2007-08-08
What about `sh shkx.exe`?

---

### Post by ljkwesi on 2007-08-08
Gives me a "shkx.exe: shkx.exe: cannot execute binary file"... The further I get into this thing, the more desperate I become...

I'll take an absolutely wild guess, but it couldn't have anything to do with the fact that I'm running on 64 bits, could it ? (I've encountered a couple of errors related to my platform being AMD64 or something around those lines when trying to install other software...)

---

### Post by lambros on 2007-08-08
> **ljkwesi said:**
> I'm not sure if this is the proper way to "strace" but here's what I get :

```
kwesi@kwesi-desktop:~/Desktop/shake$ strace bin/shkx.exe
execve("bin/shkx.exe", ["bin/shkx.exe"], [/* 31 vars */]) = -1 ENOENT (No such file or directory)
...

```

... I think that even in chinese I'd understand better what is said here...

That looks good enough to me :-)  We can see clearly that the Linux system call "execve" is returning ENOENT when applied to that file.  The mysterious thing is, why?  Also, I'm not sure what's causing the "31 vars".  [Edit] OK, these are just the environment variables. [/Edit]

I'll have a think about this...
Lambros

---

### Post by Bachstelze on 2007-08-08
Problem "solved", his system is a 64 bits. I should have checked that before :p

---

### Post by dr.koljan on 2007-08-08
Have you tried launching the file WITHOUT the dot and slash (shkx.exe not ./shkx.exe)?

---

### Post by ljkwesi on 2007-08-08
Well seems like I'm gonna have to settle for 32 bits after all...

Thanks for all your swift help and advice :)

PS. @dr.koljan : I tried doesn't seem to work either.

---

### Post by bashologist on 2007-08-08
Ah. So typing "file shkx.exe" could have helped. Next time you can try the "file" command to see what it was built for.

---

### Post by ljkwesi on 2007-08-08
Sure thing. I'll remember this next time before coming here crying for help... and sorry for the unnecessary trouble.

---

### Post by lambros on 2007-08-08
> **ljkwesi said:**
> Sure thing. I'll remember this next time before coming here crying for help... and sorry for the unnecessary trouble.

No worries, I had a bit of fun with that :-)  I'm still a little surprised that running a 32-bit exe on a 64-bit system would give that particular error.

Lambros

---

