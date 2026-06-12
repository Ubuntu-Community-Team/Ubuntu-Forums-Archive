---
title: "gfortran executable"
date: 2008-06-27
forum: General Help
---

### Post by richardmems on 2008-06-27
Hi

i compile simple test.f with gfortran by typing

>>gfortran test.f

and 'a.out' file is created.

but when i type 'a.out' in prompt, i got 'command not found' error.
the program is suppose to print HELLO WORLD on console.


how to run the executable produced by gfortran?

Thanks

Richard

---

### Post by squaregoldfish on 2008-06-27
When you say nothing happens, is that literally the case, or do you get a 'command not found' error?

Without knowing what the program does, it's hard to tell what it's supposed to have done. Is it supposed to print messages to the console?

Steve.

---

### Post by richardmems on 2008-06-27
sorry

i got 'command not found' error.

the program was suppose to print Hello World on console.

thanks
richard

---

### Post by squaregoldfish on 2008-06-27
OK, there's two possible problems here then.

First, is a.out executable? chmod a+x a.out will fix that.

Second, try ./a.out - The chances are your current directory isn't in the path, so Ubuntu doesn't know to look where you are for things to execute.

Steve.

---

### Post by richardmems on 2008-06-27
Thanks for your rpely.

chmod doesn't work. after that i'm still getting the "command not found error'

since i am running from the same directory where a.out exist, it's unlikely that linux cannot find the path.

for the computational software i compiled on ubuntu, i'm facing same problem. the executable file pw.x is there when i type 'ls' command in same directory. but when i run the program by typing pw.x  , 'command not found' error came out.

Thanks again
richard

---

### Post by squaregoldfish on 2008-06-27
Ah, but did you actually try it?

To work out what's on your path, type

```
echo $PATH
```

You'll get a list of directories separated by colons. If the directory '.' isn't there, Ubuntu won't run things in the current directory (this is the default setup, for system security reasons). Hence the need to add './' to anything you want to run from the current directory.

Steve.

---

