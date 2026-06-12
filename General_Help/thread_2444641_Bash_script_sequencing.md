---
title: "Bash script sequencing"
date: 2020-06-02
forum: General Help
---

### Post by yegnal on 2020-06-02
In my shell environment:
GNU bash, version 5.0.16(1)-release (x86_64-pc-linux-gnu)


echo {1..10} 
1 2 3 4 5 6 7 8 9 10
&
echo {a..f}
a b c d e f 

The problem is in making that work as a for loop sequence

#! /bin/bash
for i in {1..10}; do 
echo $i 
done

output from script: 
{1..10} 

for i in {a..f}; do
echo $i
done

output from script: 
{a..f} 


I can get the numeric part to work using an outside function, $(seq 1 10), but that solution probably isn't as efficient, and isn't doing anything to help me sequence alphabetical characters inside a for loop.

---

### Post by sisco311 on 2020-06-02
How are you invoking the script? 

In Ubuntu sh is symlink to dash NOT bash.

The brace expansion should work in bash unless you start the shell with `+B' option or disable it with the set command.

---

### Post by TheFu on 2020-06-02
This works here:

```
$ for N in {01..10} ; do echo "# $N  "; done
# 01  
# 02  
# 03  
# 04  
# 05  
# 06  
# 07  
# 08  
# 09  
# 10
```
Inside a script, it also works:
```
#!/bin/bash

for N in {01..10} ; do 
  echo "# $N  "
done

```

And this works in a script too:
```
#!/bin/bash

for N in {a..f} ; do
  echo "# $N  "
done
```

Run using:
```
$ ./t 
```
or
```
$ /tmp/t 
```

If you are trying to double-click to run something, then that issue is a problem with the file manager or GUI program.
Don't forget to set the execute permissions on the script file(s).  **chmod +x /tmp/t**

Linux as an OS doesn't care anything about file extensions. Those are handy for humans and some ported Windows programs.  For example, if I rename /tmp/t to /tmp/t.pdf ... it still works exactly the same way as before.
```
$ ./t.pdf 
# a  
# b  
# c  
# d  
# e  
# f  
```

I can also rename a PDF file to be "book" without any extension, then use evince to open and read it.
```
$ evince The_Linux_Command_Line-William_Shotts_1364
```
Works 100% fine. Can change it to .xls ... 
```
$ evince The_Linux_Command_Line-William_Shotts_1364.xls
```
Still works perfectly.  It isn't the extension that matters. It is the first few lines of any file that says what it is.
**#!/bin/bash** ... for bash scripts.
**%PDF-1.5 ** ... for a PDF v1.5 file.

```
$ file The_Linux_Command_Line-William_Shotts_1364.xls 
The_Linux_Command_Line-William_Shotts_1364.xls: PDF document, version 1.5
```
See. The file command know what type of data it holds. On Unix systems, this is called "the magic number" 
[https://en.wikipedia.org/wiki/Magic_number_(programming)](https://en.wikipedia.org/wiki/Magic_number_(programming))

Extensions are handy for humans.

---

### Post by yegnal on 2020-06-02
Invoking at the prompt:      sh script.sh

The post was for illustrative purposes, I have more complex intentions.

The reason I included the successful iteration simply typed from a shell prompt was to illustrate that it DOES work in my bash environment, just not working inside of a shell script in combination with a for loop.  

I thought that in and of itself was very odd.

Tried what you posted here, 
[COLOR=#000000][FONT=&quot]for N in {01..10} ; do echo "# $N  "; done[/FONT][/COLOR]
and got
# {01..10} 
so clearly there is a glitch

---

### Post by TheFu on 2020-06-02
"sh" isn't bash.  It is Borne Shell.  Different shells have different capabilities.
Try **bash ./script.sh**.  The ./ could be critical.  Hopefully, you don't have the CWD in your PATH. That is a security failure.

Whenever posting code, please use 'code tags' as I've done.  The advanced editor has that or just change an of the other wrapped formatting options quote --> code.

---

### Post by yegnal on 2020-06-04
So the solution comes in the form of chmod +x whatever.sh
then ./whatever.sh

It works this way, but not without the chmod.

If I run it sh whatever.sh it fails.....

---

### Post by sisco311 on 2020-06-04
> **yegnal said:**
> Invoking at the prompt:      sh script.sh





On Ubuntu `sh' is a symbolic link to dash (Debian Almquist shell) NOT bash (Bourne-again shell).

For sh (the interpreter) your [shebang]("https://en.wikipedia.org/wiki/Shebang_(Unix)") is just a comment and simply ignores it.

Just make your script executable and run it as any other command and the OS/kernel will use the interpreter specified by the shebang line.

NOTE:

Even when sh is a link to bash one could run in some troubles; because when invoked as sh, bash will try to mimic the startup behavior of historical versions of sh as closely as possible, while conforming to the POSIX standard as well.

 Here is an exemple:
```

sisco@acme:~/xtmp $ ls -al /bin/sh
lrwxrwxrwx 1 root root 4 May 22 15:29 /bin/sh -> bash
sisco@acme:~/xtmp $ cat myscript 
#!/bin/bash

0-non-POSIX_function_name(){
    echo non-POSIX
}

0-non-POSIX_function_name
sisco@acme:~/xtmp $ bash myscript 
non-POSIX
sisco@acme:~/xtmp $ sh myscript
myscript: line 5: `0-non-POSIX_function_name': not a valid identifier
sisco@acme:~/xtmp $ dash myscript 
myscript: 3: myscript: Syntax error: Bad function name

```

---

### Post by TheFu on 2020-06-04
> **yegnal said:**
> So the solution comes in the form of chmod +x whatever.sh
then ./whatever.sh

It works this way, but not without the chmod.

If I run it sh whatever.sh it fails.....

It works as expected.  

Unix permissions are part of Linux. There's no way around that and not understanding Unix permissions means not understanding all the most popular OSes in the world, except, cough, one.

The **chmod +x** is just one way.  It can be restricted to 1 userid, a specific group of users, everyone except a specific group of users or to allow everyone, as the chmod +x does.

I'll stand corrected about sh --> dash.  Can't say if that is a Linux or Ubuntu oddity.  It isn't something I've needed to know since the 1990s.  When scripting, it is best to pick the interpreter you want explicitly and use that. There must be 100 different interpreters, not all are sh/bash compatible.

---

### Post by sisco311 on 2020-06-05
> **TheFu said:**
> 
I'll stand corrected about sh --> dash.  Can't say if that is a Linux or Ubuntu oddity.  It isn't something I've needed to know since the 1990s.  When scripting, it is best to pick the interpreter you want explicitly and use that. There must be 100 different interpreters, not all are sh/bash compatible.

It's a Unix/Linux/Unix-like oddity :)

The sh is dead, long live the sh!

 [https://en.wikipedia.org/wiki/Bourne_shell](https://en.wikipedia.org/wiki/Bourne_shell)

---

### Post by TheFu on 2020-06-05
> **sisco311 said:**
> It's a Unix/Linux/Unix-like oddity :)

The sh is dead, long live the sh!

 [https://en.wikipedia.org/wiki/Bourne_shell](https://en.wikipedia.org/wiki/Bourne_shell)

Perhaps I wasn't clear.  The "dash" shell being used at all is what seems odd to me unless it is an embedded system with 1KB of storage.  I've never seen dash used on any commercial Unix system. It was always Bourne Shell with an option to use ksh or csh.
For example: [https://docs.oracle.com/cd/E19455-01/805-6331/6j5vgg67n/index.html](https://docs.oracle.com/cd/E19455-01/805-6331/6j5vgg67n/index.html)

Of course, admins can add other shells. I always added tcsh for about a decade before trying out bash and finding it was fine for interactive sessions and BETTER for scripting.

---

### Post by sisco311 on 2020-06-05
[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

In the [Upstart]("http://upstart.ubuntu.com/") era they argued that dash would improve the boot process and it did.

---

### Post by kneutron on 2020-06-06
> [COLOR=#000000][INDENT]In the [Upstart]("http://upstart.ubuntu.com/") era they argued that dash would improve the boot process and it did

--Yeeeeah, that change from 14 years ago should probably be revisited these days. With modern disks being orders of magnitude faster than what we had back then.  They could probably optimize bash a bit, or strip out the interactive parts to make the file size smaller, or simply **copy it to RAM disk and call it from there for the bootup stuff**.  Which is less of a consideration these days anyway, because now we have *systemd* wanting to be like the MCP from TRON.[/INDENT]
[/COLOR]

---

### Post by TheFu on 2020-06-06
But Ubuntu runs off a Rasberry Pi with microSD for storage. The Canonical teams should always remember that.  Not everyone has a Core i7 with 64G of RAM and a $550 GPU.

---

