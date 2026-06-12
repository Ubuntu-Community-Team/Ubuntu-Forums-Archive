---
title: "Were is &quot;cd //&quot;  documenmted ?"
date: 2020-10-17
forum: General Help
---

### Post by helen314 on 2020-10-17
I am sorry for asking this , obviously DOS question , way, way  off topic...
I did ask Mrs Google and got "certificate of deposit". 
Anybody have  suggestion how to ask Mrs Google or have a link to "DOS  shorthand commands
Cheers

---

### Post by Holger_Gehrke on 2020-10-17
The 'cd' command is built into the shell. You can either look in the manual for your shell ('man bash' if you're using the default Bourne Again SHell; warning: long and **extremely** dense manual page) or use 'help cd'. And it's not a DOS-command originally, DOS 1.0 didn't have (sub-)directories; they copied that feature from Unix, which had a hierarchical file system since the early 70s.

Holger

---

### Post by GhX6GZMB on 2020-10-17
If it's DOS, wouldn't it be **cd \\** ?
Never seen that syntax, though. Normal is **cd \**

---

### Post by QIII on 2020-10-17
Sometimes the internet monkeys expect you to know what you are looking for before you know what you are looking for, unfortunately.

You might change your search criteria to "DOS commands" or "MS-DOS commands" to cast a wider net.

I found [this]("https://www.computerhope.com/dostop10.htm"), for instance.

I'm not sure where you might find something official at a Microsoft site.

---

### Post by GhX6GZMB on 2020-10-17
I think the question is related to this thread:
[https://ubuntuforums.org/showthread.php?t=2451872&page=2](https://ubuntuforums.org/showthread.php?t=2451872&page=2)

**cd //** doesn't exist AFAIK, I suppose bash simply  ignores the second "/"

---

### Post by grahammechanical on 2020-10-17
The link below is from a Ubuntu tutorial

[https://ubuntu.com/tutorials/command-line-for-beginners#3-opening-a-terminal](https://ubuntu.com/tutorials/command-line-for-beginners#3-opening-a-terminal)

And then there is section 3 from How - To - Geek

[URL="https://www.howtogeek.com/412055/37-important-linux-commands-you-should-know/"]https://www.howtogeek.com/412055/37-important-linux-commands-you-should-know

[/URL]All useful stuff if we ever need to use Recovery mode and the Root Shell prompt to try and fix things. I go back to the days when MS-Dos was not a shell but an operating system. Nothing could be done without a knowledge of Ms-Dos commands.

Regards

---

### Post by helen314 on 2020-10-17
> **QIII said:**
> Sometimes the internet monkeys expect you to know what you are looking for before you know what you are looking for, unfortunately.

You might change your search criteria to "DOS commands" or "MS-DOS commands" to cast a wider net.

I found [this]("https://www.computerhope.com/dostop10.htm"), for instance.


Been there, no go 


I'm not sure where you might find something official at a Microsoft site.

```

a@a-SATA:~$ cd \\
bash: cd: \: No such file or directory
a@a-SATA:~$ cd //
a@a-SATA://$ 


```

I am begging to wonder if it is  Linux command.

I think these are called "navigational shorthands " such as single dot "." or doulbe dot ".." 

I'll keep looking.

---

### Post by Impavidus on 2020-10-17
> **ml9104 said:**
> I think the question is related to this thread:
[https://ubuntuforums.org/showthread.php?t=2451872&page=2](https://ubuntuforums.org/showthread.php?t=2451872&page=2)

**cd //** doesn't exist AFAIK, I suppose bash simply  ignores the second "/"

Bash doesn't really ignore that second /, but // is like a synonym for /. Bash appears to keep track of it and pwd, which is a shell built-in, will just report you're in //. However, /usr/bin/pwd, which is the same tool but now as a separate executable, will tell you the truth:```
x@y:~$ cd //
x@y://$ pwd
//
x@y://$ cd etc
x@y://etc$ pwd
//etc
x@y://etc$ /usr/bin/pwd
/etc
```
So I'd say that // is a bash peculiarity.

---

### Post by TheFu on 2020-10-17
```
cd /
```
is the same as 
```
cd //
```

is the same as ```
cd //////////////home//////thefu
# and
cd /home/thefu

```

More than 1 / is ignored by the OS. Always has been that way.

Code tags really help people understand what is being typed into a terminal.

Lots of these basic questions can be tested in 10 seconds.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) covers Linux stuff in a good order since advanced skills build on intermediate skills that build on beginner skills.  Trying to do non-beginner stuff when the skill level is still beginner leads to difficulties.

---

### Post by GhX6GZMB on 2020-10-17
@TheFu:

"More than 1 / is ignored by the OS. Always has been that way"
Thanks. That was also my suspicion.

---

### Post by sisco311 on 2020-10-20
> **helen314]
Were is "cd //"  documenmted ?
[/quote]

```
man path_resolution
```

[QUOTE=helen314 said:**
> 
Anybody have  suggestion how to ask Mrs Google or have a link to "DOS  shorthand commands


First of all it is [BASH]("https://en.wikipedia.org/wiki/Bash_(Unix_shell)") not [DOS]("https://en.wikipedia.org/wiki/DOS").
I did a search for: 'unix slash vs double slash'
and found this very interesting reading: [https://unix.stackexchange.com/questions/12283/unix-difference-between-path-starting-with-and](https://unix.stackexchange.com/questions/12283/unix-difference-between-path-starting-with-and)

Bash runs on nearly every version of Unix and a few other operating systems. According to the [POSIX Pathname Resolution specification]("https://pubs.opengroup.org/onlinepubs/009695399/basedefs/xbd_chap04.html#tag_04_11"):
> 
A pathname consisting of a single slash shall resolve to the root directory of the process. A null pathname shall not be successfully resolved. A pathname that begins with two successive slashes may be interpreted in an implementation-defined manner, although more than two leading slashes shall be treated as a single slash.
But yeh, on most OSes  / and // are the same.

---

### Post by TheFu on 2020-10-20
For all programmers, if you always use '/' as your directory separator, it works on all the popular OSes, including MS-Windows.  Has for decades.

Every shell I've used - probably all the popular ones, but not fish, handle // anywhere in the path as a single /.

I suspect the confusion comes due to SMB, which likes \\server\path\to\something.  However, if //server/path/to/something is used, that works.  Whereas,  \\server\path\to\something really must be entered as  \\\\server\\path\\to\\something to be correct on a Unix system.  On Unix, to get a single \ character, we have to escape it by using the escape character, which is almost always a single \.

\\ --> \\\\

It is just easier to use /, unless that doesn't work. But I can see where personal preference would see that as odd.

---

