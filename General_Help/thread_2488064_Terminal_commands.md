---
title: "Terminal commands"
date: 2023-06-22
forum: General Help
---

### Post by bootofbeer on 2023-06-22
Is there an easy list I canrefer to

---

### Post by Rubi1200 on 2023-06-22
Hi,

everyone will have their own favorite references but this one has the most commonly used commands with examples:
[https://phoenixnap.com/kb/linux-commands](https://phoenixnap.com/kb/linux-commands)

---

### Post by TheFu on 2023-06-22
> **bootofbeer said:**
> Is there an easy list I canrefer to

Sure, 
```
$ ls /usr/bin/
```

On my desktop, it shows, 
```
$ ls /usr/bin/ |wc -l
2374

```
so there are 2300 commands, each with a manpage which explains the options.  To see the manpage, follow this example, 
```
$ man ls
LS(1)                                   User Commands                                  LS(1)

NAME
       ls - list directory contents

SYNOPSIS
       ls [OPTION]... [FILE]...

DESCRIPTION
       List  information  about  the FILEs (the current directory by default).  Sort entries
       alphabetically if none of -cftuvSUX nor --sort is specified.

       Mandatory arguments to long options are mandatory for short options too.

       -a, --all
              do not ignore entries starting with .

       -A, --almost-all
              do not list implied . and ..
...

```
About 5 pages more explain how to use **ls** and what the options are.

There are some under /bin and /sbin and /usr/sbin and /usr/local/sbin and /usr/local/bin  too. Just depends on which packages you've installed.

---

### Post by ActionParsnip on 2023-06-22
Try to approach it as
```

How can I do x

```
rather than
```

What are all the things I can do

```
You'll be less overwhelmed. As TheFu has shown, there are lots of commands, most of which you'll NEVER use

---

### Post by TheFu on 2023-06-22
> **ActionParsnip said:**
>  
You'll be less overwhelmed. As TheFu has shown, there are lots of commands, most of which you'll NEVER use

+1.  Learning Linux is like learning English. There are always new words you don't know, but the most common 100 words are things you use every week.  Understanding that Unix/Linux philosophies are different from other OSes, is another important idea to understand.  

In Unix, ... heck, AT&T had a short video to describe it back in the 1970s.
[https://www.youtube.com/watch?v=tc4ROCJYbm0](https://www.youtube.com/watch?v=tc4ROCJYbm0)

---

### Post by Rubi1200 on 2023-06-22
> **ActionParsnip said:**
> Try to approach it as
```

How can I do x

```
rather than
```

What are all the things I can do

```
You'll be less overwhelmed.
+1 excellent advice!

---

### Post by Holger_Gehrke on 2023-06-22
Such 'cheat-sheets' are usually not especially useful since they lack explanations of essential concepts. What's the use of reading 'cd - change the current working directory' if you don't know what the 'current working directory' is and have no idea why you'd want to change it. Learning the command line is a bit like learning maths, to understand the more advanced concepts you need to have understood the more basic ones.

The manual pages usually aren't good for learning the command line since they are meant as a reference for users who already understand the concepts and just need to see what a specific option is called or what parameters can be given to a specific command.

There are a lot of books on the topic and you can get good ones quite cheaply since the command line changes very slowly - if at all - so a used book from the 1990s meant for Unix will still be very close to up to date on any Linux. A good and free (licensed under Creative Commons "Attribution-NonCommercial-NoDerivs 3.0 Unported  (CC BY-NC-ND 3.0)) one is 'The Linux Command Line' by William Shotts which can be downloaded from linuxcommand.org. That site also features a lot of other good information you might want to take a look at, including a script which uses 'whatis' and package management tools to generate a listing of programs with short descriptions and the packages they were installed from. Basically, that's the raw material from which to selectively build your own 'cheat-sheet' ...

Holger

---

### Post by TheFu on 2023-06-22
> **Holger_Gehrke said:**
> Such 'cheat-sheets' are usually not especially useful since they lack explanations of essential concepts. What's the use of reading 'cd - change the current working directory' if you don't know what the 'current working directory' is and have no idea why you'd want to change it. Learning the command line is a bit like learning maths, to understand the more advanced concepts you need to have understood the more basic ones.

The manual pages usually aren't good for learning the command line since they are meant as a reference for users who already understand the concepts and just need to see what a specific option is called or what parameters can be given to a specific command.

There are a lot of books on the topic and you can get good ones quite cheaply since the command line changes very slowly - if at all - so a used book from the 1990s meant for Unix will still be very close to up to date on any Linux. A good and free (licensed under Creative Commons "Attribution-NonCommercial-NoDerivs 3.0 Unported  (CC BY-NC-ND 3.0)) one is 'The Linux Command Line' by William Shotts which can be downloaded from linuxcommand.org. That site also features a lot of other good information you might want to take a look at, including a script which uses 'whatis' and package management tools to generate a listing of programs with short descriptions and the packages they were installed from. Basically, that's the raw material from which to selectively build your own 'cheat-sheet' ...

Holger

All true. When staring at a flashing cursor, it is nice to throw a few data showing commands, before someone has learned to about users, groups, permissions, etc.  I always found that creating my own notes (a personal wiki) with the commands I learned and what they do (as far as I knew at the time, which was often simplistic and sometimes wrong) was still helpful as my vocabulary was extended every day.
[https://blog.jdpfu.com/2017/09/12/linux-command-line-or-shell-resources](https://blog.jdpfu.com/2017/09/12/linux-command-line-or-shell-resources) has a list of links with other short introductions to the command line. Two are help.ubuntu.com links, but there are some others.  Don't get too hung up on "Ubuntu" or "Linux", since over 90% will apply to UNIX as well.  If you have a used bookstore nearby, look for a 10, 20, 30 yr old UNIX Shell book for $0.50. It will be good enough to begin learning.  Very little has changed in all these years, except a few options exist now for some commands that we didn't have back then.

---

### Post by aljames2 on 2023-06-22
Agree with all of this above..

My first use for Linux was to have a backup server, while still using a Windows desktop some, which led to fully moving away from MS.  I started w/Ubuntu Server for this.  It forced me to learn the command line starting out.  Probably not the best idea using your backup system to learn a new OS, but with careful patience, reading, and asking, it worked.  I am a good documenter, so while learning, I also have created probably 50 little helper docs (text files), with steps, diagrams, cheat sheets, etc.  It helps when you enjoy it.

---

