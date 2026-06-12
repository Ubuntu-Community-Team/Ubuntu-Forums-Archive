---
title: "/bin/sh"
date: 2006-09-08
forum: General Help
---

### Post by Zarathu on 2006-09-08
What is so great about the /bin/sh?  There is a lot of shellcode written to overflow a buffer and gain that shell access.  Does the shell have access that my standard username does not have?

---

### Post by IYY on 2006-09-08
I don't think you understand what a shell is, exactly. A shell is a program is an interface with which a user can communicate with the system. Your GUI is another such interface. When you run a shell (by executing /bin/sh, /bin/bash, or just logging into the system), you are still the user you were before, but instead of a GUI you use text input to communicate with the OS.

---

### Post by Zarathu on 2006-09-09
Of course, that's obvious.  But, I was wondering what the difference between these two are:

```
-bash-3.1$ sh
$
$
```

^^ OpenBSD, though.

But anyway, what is the difference between bash and sh?  Different privileges or something?

---

### Post by Zarathu on 2006-09-09
```
user@pc~ sh
-sh-3.1$
-sh-3.1$
```
Make it easier?  What does the "sh" do when I already have bash?

---

### Post by Lunar_Lamp on 2006-09-09
```
$ ls /bin -l | grep sh
-rwxr-xr-x 1 root root  664084 2006-04-21 23:51 bash
lrwxrwxrwx 1 root root       4 2006-06-09 19:43 rbash -> bash
lrwxrwxrwx 1 root root       4 2006-06-09 19:43 sh -> bash
```

/bin/sh is just linked to /bin/bash

Quoting from wikipedia:
> 
#!/bin/sh &#8212; Execute using sh program in the /bin/ directory (On some systems, such as Solaris, this is the Bourne shell. On Linux systems there is usually no Bourne shell and this is a link to another shell, such as bash. Using #!/bin/sh in shell scripts will thus invoke different shells on different systems. However, the Single UNIX Specification specifies certain requirements for /bin/sh, and some shells, such as bash, will alter their behaviour to match them when invoked with the name "sh".)

---

### Post by Zarathu on 2006-09-09
Excellent, thanks.

---

