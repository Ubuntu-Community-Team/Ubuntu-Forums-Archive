---
title: "Issues with grep command"
date: 2014-05-06
forum: General Help
---

### Post by annemary on 2014-05-06
I am using Ubuntu 13.10 and my grep version is 2.14. Grep command stopped working recently and whenever I type a grep command, it always displays the help information. I tired several examples, but  output is always the same. Also I face this problem when I use other programs such as libreoffice and when installing new packages. 
Anyone faced similar issue? any clues of how to fix it? I am afraid this will affect lot of other command operations. 

Thanks in advance,

---

### Post by deadflowr on 2014-05-06
Can you give an example of the type of commands you have tried?
I find whenever the help options pop up it is because I have imputed an invalid command.

---

### Post by annemary on 2014-05-06
Here's an example:
grep -w 'ptmb7t' missfont.log 

The log file has the particular term. But this command returns help options.

Thank you!

---

### Post by steeldriver on 2014-05-06
Perhaps something has gone awry with the alias definition for grep in your ~/.bashrc file? what is the output of

```
type grep
```

on the command line (should be something like " grep is aliased to `grep --color=auto' ")

---

### Post by annemary on 2014-05-06
This is the output for "type grep" 

grep is aliased to `grep --color=auto'

---

### Post by annemary on 2014-05-09
Any tips on solving this? 
Thank you!

---

### Post by steeldriver on 2014-05-09
Is there an error message (in addition to the usage message)? Can you post a cut 'n' paste transcript of the exact command and its output?

It may not be relevant, but what shell are you using? What does

```

grep --version

``` say?

---

### Post by annemary on 2014-05-09
I am using bash shell and grep --version gives the following:

> grep (GNU grep) 2.14
Copyright (C) 2012 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.


Written by Mike Haertel and others, see <http://git.sv.gnu.org/cgit/grep.git/tree/AUTHORS>.





I don't see any error messages. This is the output I get for 
> grep -w 'ptmb7t' missfont.log 

[http://pastebin.com/8MjYMvxN](http://pastebin.com/8MjYMvxN)

---

### Post by sudodus on 2014-05-09
What happens if you type these commands?

```
which grep
```
```
grep UUID /etc/fstab
```
```
lsb_release -a 2>/dev/null|grep -w Release:
```
```
uname -a|grep -w Linux
```
```
uname -a|grep -w linux
```

Please cut and paste the output within code tags (mark and click the ***#*** icon above the editing window.

---

### Post by annemary on 2014-05-09
```
which grep 
/bin/grep

```
For all of the other commands the output is the same usage message [http://pastebin.com/8MjYMvxN](http://pastebin.com/8MjYMvxN)

Thank you

---

### Post by sudodus on 2014-05-09
What about this command

```
ls -l /bin/grep
```

and this sequence of commands

```

bash   # start a bash sub-shell
grep UUID /etc/fstab
exit   # exit from the sub-shell

```

---

### Post by annemary on 2014-05-09
Output

```
ls -l /bin/grep
-rwxr-xr-x 1 root root 187792 Aug 26  2013 /bin/grep



```

For the other sequence of commands, it is still the usage message. 


Thank you

---

### Post by steeldriver on 2014-05-09
What if you take aliasing out of the picture altogether e.g.

```
\grep -w 'ptmb7t' missfont.log
```
or
```
/bin/grep -w 'ptmb7t' missfont.log
```

or even

```

unalias grep

grep -w 'ptmb7t' missfont.log

```

---

### Post by annemary on 2014-05-09
None of that worked. All commands result in usage message.
Is is possible to reinstall grep?

Thank you

---

### Post by erind on 2014-05-09
> **annemary said:**
> None of that worked. All commands result in usage message.
Is is possible to reinstall grep?

Thank you

Yes, it is possible to reinstall grep (purge+reinstall), but before you do that can you run:

 ```
file /bin/grep
```
and post the output here ?  It's a possibility that other commands might have the same issue.

---

### Post by matt_symes on 2014-05-09
Hi

Out of interest, what is the output of this command ?

```
strace grep -w 'ptmb7t' missfont.log 2>&1 | head -n5
```

Make sure you're in the correct directory when you run it.

Kind regards

---

### Post by annemary on 2014-05-09
> **erind said:**
> Yes, it is possible to reinstall grep (purge+reinstall), but before you do that can you run:

 ```
file /bin/grep
```
and post the output here ?  It's a possibility that other commands might have the same issue.

This is the output 

```

file /bin/grep

/bin/grep: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0x1fbe356a5e43143bde398ac869413f687a9cd141, stripped


```

---

### Post by annemary on 2014-05-09
> **matt_symes said:**
> Hi

Out of interest, what is the output of this command ?

```
strace grep -w 'ptmb7t' missfont.log 2>&1 | head -n5
```

Make sure you're in the correct directory when you run it.

Kind regards

Here's the output, I have no clues what do these mean.

```

strace grep -w 'ptmb7t' missfont.log 2>&1 | head -n5

execve("/bin/grep", ["grep", "-w", "ptmb7t", "missfont.log"], [/* 62 vars */]) = 0brk(0)                                  = 0xbd0000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fe2bf481000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)



```

thank you

---

### Post by matt_symes on 2014-05-09
Hi

> **annemary said:**
> Here's the output, I have no clues what do these mean.

```

strace grep -w 'ptmb7t' missfont.log 2>&1 | head -n5

**execve("/bin/grep", ["grep", "-w", "ptmb7t", "missfont.log"], [/* 62 vars */])** = 0brk(0)                                  = 0xbd0000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fe2bf481000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)


```

thank you

I was interested in the line i have highlighted in bold above. I wanted to check that the correct parameters were being passed into grep.

I wonder if a full strace will shed any light on what is happening.

Can you run this command

```
cd ~ && strace -o strace.txt grep -w 'ptmb7t' ***/path/to/***missfont.log
```

It should create a file in your home directory called strace.txt. Can you post that file back here.

Kind regards

---

### Post by annemary on 2014-05-09
Here's the stack trace for
 ```
cd ~ && strace -o strace.txt grep -w 'ptmb7t' *** ~/***missfont.log
```

[http://pastebin.com/6iE6Wdg7](http://pastebin.com/6iE6Wdg7)

thank you

---

### Post by matt_symes on 2014-05-09
HI

This is a bit of an odd problem this one. 

I am using a different version of grep than you are (grep (GNU grep) 2.16), however i can really only see a couple of reasons why it may call into the usage() function that displays the extended help and one of them is if the color switch is called incorrectly.

After a quick glance at the code i have seen that a static variable called show_help is declared and being static, it should be set to a value of 0. It gets set to a value of 1 in a couple of places and, when set to 1, calls the function usage() that shows either the short help or the extended help, depending on the value of a parameter passed to that function.

Do you still get the extended help if you run this ?

```
grep --color=never deb /etc/apt/sources.list
```

EDIT:

Can you also post the output of 

```
env | sed -n /GREP/p
```

Kind regards

---

### Post by annemary on 2014-05-09
Okay thanks for the pointer - 

```
env | sed -n /GREP/p
```
resulted 
```
--color=always'
```

I think the issue was because of the wrong syntax (extra ' at the end). I know how this has happened, but now I modified it and grep is working correctly now. 

Thanks everyone for your great support. Appreciate your time and effort!

---

### Post by erind on 2014-05-09
> **annemary said:**
> This is the output 

```

file /bin/grep

/bin/grep: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0x1fbe356a5e43143bde398ac869413f687a9cd141, stripped


```

The output looks fine, for a moment I thought there was a binary corruption problem, for which the **file **command might have given a hint about it.
But now seeing your strace output (see below), I think this is a missing* english **locale*** issue.

**Strace output**, **Lines 48-51**
```
...
open("**/usr/share/locale/en_US/LC_MESSAGES/grep.mo**", O_RDONLY) = -1 ENOENT (**No such file or directory**)
open("/usr/share/locale/en/LC_MESSAGES/grep.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("**/usr/share/locale-langpack/en_US/LC_MESSAGES/grep.mo**", O_RDONLY) = -1 ENOENT (**No such file or directory**)
open("/usr/share/locale-langpack/en/LC_MESSAGES/grep.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
...
```
However I'm no expert in *locales*, and this is more of a pointer to your problem. Check this link in the meantime:

[http://hexample.com/2012/02/05/fixing-locale-problem-debian/](http://hexample.com/2012/02/05/fixing-locale-problem-debian/)

Hope it helps.

---

### Post by matt_symes on 2014-05-10
Hi

```
--color=always'
```

Yep. The extra ' at end would have caused it. I'm glad it's fixed.

> **erind said:**
> The output looks fine, for a moment I thought there was a binary corruption problem, for which the **file **command might have given a hint about it.
But now seeing your strace output (see below), I think this is a missing* english **locale*** issue.

**Strace output**, **Lines 48-51**
```
...
open("**/usr/share/locale/en_US/LC_MESSAGES/grep.mo**", O_RDONLY) = -1 ENOENT (**No such file or directory**)
open("/usr/share/locale/en/LC_MESSAGES/grep.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("**/usr/share/locale-langpack/en_US/LC_MESSAGES/grep.mo**", O_RDONLY) = -1 ENOENT (**No such file or directory**)
open("/usr/share/locale-langpack/en/LC_MESSAGES/grep.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
...
```
However I'm no expert in *locales*, and this is more of a pointer to your problem. Check this link in the meantime:

[http://hexample.com/2012/02/05/fixing-locale-problem-debian/](http://hexample.com/2012/02/05/fixing-locale-problem-debian/)

Hope it helps.

I have missing locale files as well. Thankfully, they should not be too much of an issue in this case.

Kind regards

---

### Post by steeldriver on 2014-05-10
Nice catch @matt_symes - I have to admit I never even knew there were GREP env vars!

---

### Post by erind on 2014-05-10
> **matt_symes said:**
> [...]

I have missing locale files as well. Thankfully, they should not be too much of an issue in this case.

Kind regards

Good to know,  I completely missed the last part of OP's final post, where the problem was actually resolved.  Thanks.

---

### Post by annemary on 2014-05-11
Thanks everyone for helping to fix the issue.

---

