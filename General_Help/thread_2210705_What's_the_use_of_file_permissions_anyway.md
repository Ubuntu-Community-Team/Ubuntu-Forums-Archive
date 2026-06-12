---
title: "What's the use of file permissions anyway?"
date: 2014-03-12
forum: General Help
---

### Post by goghvv on 2014-03-12
I have installed Ubuntu 3.11 for learning purposes, and I have a question.
What is the use of file permissions in Ubuntu, if I can just change them however and whenever I like?
What kind of security does that provide, if anyone can just run the chmod command and change the file permissions as he see fit?
And if he can't, he can just stick the magic word "sudo" wherever he like, and override any limitations that there might be on the computer.

I'm guessing that this whole file permissions concept makes more sense in big server based systems, where I'm not the only user on the computer, but I'm not sure exactly how...

Any clarification would very much appreciated.

---

### Post by Frogs Hair on 2014-03-12
3.11 ?

```
man chmod
```

[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

[http://www.linux.org/threads/file-permissions-chmod.4094/](http://www.linux.org/threads/file-permissions-chmod.4094/)

---

### Post by Impavidus on 2014-03-12
Not every user can just chmod anything, but (non-root) users can only chmod their own files. And only the system administrator can use sudo. And don't just change permissions all over the place, as this will break your system.

It's true that the permissions system is more important on large server based systems, but Linux has been designed with these systems in mind from the beginning. Still, even on a single-user laptop it's useful, as it can protect you from yourself (sudo forces you to think twice before you can harm your system), from external threats (permissions make it more complicated for malware to penetrate your system) and can limit the effect of software errors (a problem in a user program can never damage the entire system).

By the way, Ubuntu 3.11 doesn't exist. Did you mean Ubuntu 13.10, running Linux kernel 3.11?

---

### Post by mastablasta on 2014-03-12
try changing files on someone elses server if you can. ;-)

or for that matter reading certain files (you can't since if server is propperly confuigured you can't even see them easilly)

they also decide which file is executable and which one isn't.

---

### Post by SeijiSensei on 2014-03-12
Unix was designed as a multi-user operating system from the outset.  As a Unix derivative, Linux employs the same filesystem primitives like permissions.

I can understand how someone used to working only on a personal computer might think this is all overkill, but as Impavidus observes permissions also keep you from making potentially disastrous changes to your system.  Nor can ordinary users affect the execution of processes owned by other users or root.  There is more to permissions than just files and directories.

On my CentOS servers, sudo isn't an option.  You need the root password to do anything to files and directories you do not own.

---

### Post by matt_symes on 2014-03-12
Permissions can be a great help if someone tries to hack you. 

They can also help defend against malware.

They can stop rouge processes trashing other config (and other) files.

Remember, it's not only users that have permissions but some applications, many userspace daemons and other programs.

---

### Post by goghvv on 2014-03-12
Thank you all for the great answers.
This was all very informative.

---

### Post by goghvv on 2014-03-12
> **Impavidus said:**
> By the way, Ubuntu 3.11 doesn't exist. Did you mean Ubuntu 13.10, running Linux kernel 3.11?

I don't know... 
this is what I got when I ran uname -a :
```
Linux ubuntu 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by deadflowr on 2014-03-12
Yeah 3.11 is just the ubuntu kernel(what ubuntu calls their build of the linux kernel).
to see what version of Ubuntu try
```
lsb_release -a
```

---

### Post by oldos2er on 2014-03-12
I've found [this article]("http://www.linuxquestions.org/linux/answers/Security/Quick_and_Dirty_Guide_to_Linux_File_Permissions") to be helpful.

To see which Ubuntu version you're running (as opposed to kernel version) try ```
lsb_release -r
```

---

