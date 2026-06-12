---
title: "Where can I learn most used Ubuntu Commands?"
date: 2020-10-20
forum: General Help
---

### Post by dezintop on 2020-10-20
question from a ubuntu newbie:

Where can I learn most used Ubuntu Commands? Can I have all complied in a list with short description?

---

### Post by kc1di on 2020-10-20
Hello And Welcome to Ubuntu Linux.
You can learn a lot from [this tutorial.]("https://ubuntu.com/tutorials/command-line-for-beginners#1-overview")
and [this list]("https://www.dummies.com/computers/operating-systems/linux/common-linux-commands/") will help.

---

### Post by ActionParsnip on 2020-10-20
The "most used commands" is pretty irrelevant. One command set that one person uses may be wildly different to another users. I suggest you simply use the OS in command line and research commands as and when you need to use them.
More of a "how do I do x?" rather than "what are _all_ he things I can do?"

---

### Post by HermanAB on 2020-10-20
YAUR (Yet Another UNIX Resource):
[http://mally.stanford.edu/~sr/computing/basic-unix.html](http://mally.stanford.edu/~sr/computing/basic-unix.html)

---

### Post by T6&amp;sfpER35% on 2020-10-20
being  a newbie , this advice 
> [COLOR=#000000]More of a "how do I do x?" rather than "what are [/COLOR]_all_[COLOR=#000000] he things I can do?"[/COLOR]
would probably work better 

having a list off **ALL/MOST USED**  commands ,is going to hurt your brain

[here's](https://ubuntuforums.org/showthread.php?t=2452116&p=13993311#post13993311) another topic to get you started

---

### Post by dragonfly41 on 2020-10-20
[COLOR=#000000]> Can I have all complied in a list with short description?

What might be helpful is a desktop tool to retain commands which you learn over time (rather than copying and pasting from fora).
Just look at the number of commands under various topics here.
I did try clicompanion but now I keep commands in codeboxes in [CherryTree editor]("https://www.giuspen.com/cherrytree/").
If you are on Ubuntu 20.04 then the latest 0.99.16 is the way to go.
Edit Node (e.g. create node titled Backup)) > Insert Codebox > select sh then you can run the command snippets.
This way you keep a text description of the command, plus the command snippets.
In fact CherryTree has two options for usage. XML and SQlite.[/COLOR]

---

### Post by TheFu on 2020-10-20
> **dezintop said:**
> question from a ubuntu newbie:

Where can I learn most used Ubuntu Commands? Can I have all complied in a list with short description?

I use the commands located in 
[LIST]
[*]/bin
[*]/usr/bin
[*]/sbin
[*]/usr/sbin
[*]
[/LIST]
on my systems.  Each of those has a manpage which provides the official documentation for the command. Manpages are installed on the system with the program installed package.  
```
$ **apropos less**
...
less (1)             - opposite of more
...
$ **apropos more**
...
more (1)             - file perusal filter for crt viewing
...
$ **man less**
LESS(1)                             General Commands Manual                            LESS(1)

NAME
       less - opposite of more

SYNOPSIS
       less -?
       less --help
       less -V
       less --version
       less [-[+]aABcCdeEfFgGiIJKLmMnNqQrRsSuUVwWX~]
            [-b space] [-h lines] [-j line] [-k keyfile]
            [-{oO} logfile] [-p pattern] [-P prompt] [-t tag]
            [-T tagsfile] [-x tab,...] [-y lines] [-[z] lines]
            [-# shift] [+[+]cmd] [--] [filename]...
       (See the OPTIONS section for alternate option syntax with long option names.)

DESCRIPTION
       Less  is  a  program similar to more (1), but it has many more features.  Less does not
       have to read the entire input file before starting, so with large input files it starts
       up  faster  than text editors like vi (1).  Less uses termcap (or terminfo on some sys&#8208;
       tems), so it can run on a variety of terminals.  There  is  even  limited  support  for
       hardcopy  terminals.  (On a hardcopy terminal, lines which should be printed at the top
       of the screen are prefixed with a caret.)
...
```
There are about 50 pgs of documentation for less.  This documentation explains all the options, what each does, caveats, environment variables, and a number of in-app techniques.

**less** and **more** are "pagers". Tools that show output a page at a time. Less has many features that more does not. Whenever I see people using 'cat', I freak out a little.  'cat' is nearly useless, since most commands will read a file or set of files automatically and **less** can do things that cat cannot.  Honestly, I use 'tac' more often then I use 'cat'.
Whenever I see something like this:
```
$ cat file |grep foo
```
I die just a little. Just use
```
$ grep foo file
```
and save 2 new processes from being started unnecessarily.  Whenever someone uses 'cat', they probably shouldn't.  I tend to use **egrep** over **grep -E** too.

There are about 2,000 commands in /bin/. On my 20.04 system, /usr/bin and /bin are the same location. There's a symbolic link from /bin --> /usr/bin.  Same for /sbin/ which only has about 500 commands.  /sbin/ is full of commands used by administrators.

Anyways, use the manpages. They are full if extremely useful information.  

There are always books too. When first starting out, having information provided in a logical order is really important, to prevent back-tracking to learn stuff that jumping around forces.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - read the first 250 or so pages to get a solid foundation. Be certain to do the exercises. Skipping them only hurts yourself.  Try out commands and options that are related, but not specifically shown in the chapter.  A solid understanding of users, groups, permissions, will go a long way to limiting confusion.

Oh ... I used the apropos command. That searches all installed manpages on a system based on the query provided and returns a 1-line, short, summary of what the command does. The query term must exist in that 1-line summary.
```
$ **apropos hdparm**
hdparm (8)           - get/set SATA/IDE device parameters
hdparm.conf (5)      - Debian configuration file for hdparm
```
That's pretty useful, yes?  hdparm is a tool that can be used to tune performance for storage.
**man -k** == **apropos**.

Learning to use manpages is like learning to use google advanced searches.  Manpages have a specific layout sorta like a newspaper article. The most important stuff comes first, but as we read farther down, more details are provided.  Often, we just need the different options as a reminder.  But sometimes we need more details for exactly what each option does.

```
$ **man apt**
```
is a good manpage.  We all use the 'apt' command to maintain our systems.
```
sudo apt update
sudo apt full-upgrade
sudo apt autoremove --purge
```
Those 3 commands, run once a week are nearly all an Ubuntu desktop needs to stay patched. If daily or weekly backups are being done too, we are pretty solid with out systems maintenance.

---

### Post by The Cog on 2020-10-20
I have to agree with ActionParsnip. Trying to learn all possible commands, or even just trying to learn the most commonly used ones will be too much. There are a very few that you will need over and over, so are worth learning right at the start. Off the top of my head: man, cd, pwd, ls, cp, rm are all fundamental. Even with those, don't try to memorise every option because you will rarely use most options.
Use how-to guides to find commands as you need them. Those that you expect to be using often, learn the options you need to know. Those that you expect to use rarely, just try to remember they exist.

---

### Post by T6&amp;sfpER35% on 2020-10-20
> **TheFu said:**
> I use the commands located in 
[LIST]
[*]/bin
[*]/usr/bin
[*]/sbin
[*]/usr/sbin
[/LIST]
on my systems.  Each of those has a manpage which provides the official documentation for the command. Manpages are installed on the system with the program installed package.  
```
$ apropos less
...
less (1)             - opposite of more
...
$ apropos more
...
more (1)             - file perusal filter for crt viewing
...
$ man less
LESS(1)                             General Commands Manual                            LESS(1)

NAME
       less - opposite of more

SYNOPSIS
       less -?
       less --help
       less -V
       less --version
       less [-[+]aABcCdeEfFgGiIJKLmMnNqQrRsSuUVwWX~]
            [-b space] [-h lines] [-j line] [-k keyfile]
            [-{oO} logfile] [-p pattern] [-P prompt] [-t tag]
            [-T tagsfile] [-x tab,...] [-y lines] [-[z] lines]
            [-# shift] [+[+]cmd] [--] [filename]...
       (See the OPTIONS section for alternate option syntax with long option names.)

DESCRIPTION
       Less  is  a  program similar to more (1), but it has many more features.  Less does not
       have to read the entire input file before starting, so with large input files it starts
       up  faster  than text editors like vi (1).  Less uses termcap (or terminfo on some sys&#8208;
       tems), so it can run on a variety of terminals.  There  is  even  limited  support  for
       hardcopy  terminals.  (On a hardcopy terminal, lines which should be printed at the top
       of the screen are prefixed with a caret.)
...
```
There are about 50 pgs of documentation for less.  This documentation explains all the options, what each does, caveats, environment variables, and a number of in-app techniques.

**less** and **more** are "pagers". Tools that show output a page at a time. Less has many features that more does not. Whenever I see people using 'cat', I freak out a little.  'cat' is nearly useless, since most commands will read a file or set of files automatically and **less** can do things that cat cannot.  Honestly, I use 'tac' more often then I use 'cat'.
Whenever I see something like this:
```
$ cat file |grep foo
```
I die just a little. Just use
```
$ grep foo file
```
and save 2 new processes from being started unnecessarily.  Whenever someone uses 'cat', they probably shouldn't.  I tend to use **egrep** over **grep -E** too.

There are about 2,000 commands in /bin/. On my 20.04 system, /usr/bin and /bin are the same location. There's a symbolic link from /bin --> /usr/bin.  Same for /sbin/ which only has about 500 commands.  /sbin/ is full of commands used by administrators.

Anyways, use the manpages. They are full if extremely useful information.  

There are always books too. When first starting out, having information provided in a logical order is really important, to prevent back-tracking to learn stuff that jumping around forces.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) - read the first 250 or so pages to get a solid foundation. Be certain to do the exercises. Skipping them only hurts yourself.  Try out commands and options that are related, but not specifically shown in the chapter.  A solid understanding of users, groups, permissions, will go a long way to limiting confusion.

Oh ... I used the apropos command. That searches all installed manpages on a system based on the query provided and returns a 1-line, short, summary of what the command does. The query term must exist in that 1-line summary.
```
$ apropos hdparm
hdparm (8)           - get/set SATA/IDE device parameters
hdparm.conf (5)      - Debian configuration file for hdparm
```
That's pretty useful, yes?  hdparm is a tool that can be used to tune performance for storage.
**man -k** == **apropos**.

Learning to use manpages is like learning to use google advanced searches.  Manpages have a specific layout sorta like a newspaper article. The most important stuff comes first, but as we read farther down, more details are provided.  Often, we just need the different options as a reminder.  But sometimes we need more details for exactly what each option does.

```
$ man apt
```
is a good manpage.  We all use the 'apt' command to maintain our systems.
```
sudo apt update
sudo apt full-upgrade
sudo apt autoremove --purge
```
Those 3 commands, run once a week are nearly all an Ubuntu desktop needs to stay patched. If daily or weekly backups are being done too, we are pretty solid with out systems maintenance.






TheFU . iv'e been seeing your replies to posts for awhile now . considering myself as a newbie (being at linux for 2yrs), i feel i need to point out that even to me your posts ,although probably very informative, just is like sooo technical looking that in most cases i just give up reading thinking wow i can't even try all that . (i'm especially referring to the codes) it all look like greek lol.
i'm not dissing you or trying to offend you , i'm merely stating that to a newbie (or someone else who doesn't know what he's doing)  it all looks over the top / out of their reach/understanding.
i know your trying to help a lot cause you have answers to most problems , all i'm saying maybe try and dumb it down a bit ? 
please don't take this the wrong way , this post is not intended that way 


;)

EDIT: just now realise should have probably inboxed you , sorry mate

---

### Post by TheFu on 2020-10-20
No offense taken.  Everyone has a point of view to share. There's no way to know what will "click" for any OP. The different perspectives are good, I hope. Once an OP makes a clear choice on the direction, I either try to help with that direction or step back because I don't have the knowledge.  

Everyone here is trying to help. 

My assumption is that people are at different levels and can follow along or not, as they feel comfortable.  manpages are very important, but nobody gets better at reading them without actually ... er ... reading some.

The OP has posted a few other questions which I interpreted as showing a deeper knowledge than a typical person who is really new would have.

When I've tried to "dumb it down", people don't like that either.

**apropos** is how to search manpages - and shows a short description, as the OP requested.

**less**/more are pagers, very helpful to see output from commands in a way that can be scrolled forwards and backwards and searched. **less** is like more, but better.
The cat-grep stuff is just a rant because people often will use them to search log files and for some reason, beginning Linux books show that sort of command.  I've seen people in my Linux classes use the cat ... | grep stuff much too often. Stamping that waste out is my personal jihad (holy quest).

I looked at the link you provided above. Some of those commands are the same as I posted above, so I can only guess the manpage for less was the concern?  manpages can be complex and ugly, but that doesn't mean Linux users shouldn't be using them when they seek to understand commands.

---

### Post by T6&amp;sfpER35% on 2020-10-20
points taken , i feel like i understand more now where you coming from 
keep up the good work ,just don't overwhelm me lol 

*PEACE*

---

### Post by T6&amp;sfpER35% on 2020-10-20
> [COLOR=#000000]I looked at the link you provided above. Some of those commands are the same as I posted above[/COLOR]

on a side note , i never used any of those commands ,guess i'm more of a click click guy (GUI) than a type stuff out on terminal guy .
like if for instance if want to copy this file to that folder i'll rather just do in the file manager than to try and remember the paths ect to do it in terminal
basically all i do in terminal is clean up system with the commands i gathered along the way (although i have stacer that does the same thing i suppose) ,and connect to my vpn .
otherwise i'm getting along fine without terminal

i know the linux system true potential lies through the terminal , but noobs/everyday users like myself doesn't realy need to know all the commands

---

### Post by ajgreeny on 2020-10-20
I'm not sure this will actually help you much as it's a very long list of just about every command available in bash but here it is anyway; make use of it if you find it helps.
[https://ss64.com/bash/](https://ss64.com/bash/)

---

### Post by grahammechanical on 2020-10-20
Most things can be done in Ubuntu using a utility with a Graphical User Interface (GUI). If a new user wishes to experiment with Ubuntu then I would recommend having a dual boot of Ubuntu with Ubuntu and messing around with commands on the second installation. Then if things get broken the second installation can be fixed by reinstalling. Or, experience can be gained by trying to fix what is broken.

An experimenter should at least become familiar with the Recovery mode option under Advanced Options for Ubuntu that is accessed from the Grub boot menu. That may be the only way to get a command line on a broken system.

I also suggest learning diagnostic commands and seeing the results they produce. It would be aid to determining what is wrong.

regards

---

### Post by Holger_Gehrke on 2020-10-20
There are various "Cheat Sheets" out there. Ask your favourite search engine for "Linux commands cheat sheet" or "Ubuntu commands cheat sheet". The problem with these is that they are meant mostly as a reference and not as a learning tool. Unless you understand some basic concepts (users and permissions, hierarchical file system and current working directory, standard IO redirection and piping, substitutions, return values of commands, flow control - meaning loops and decisions) these don't make much sense, especially since a lot of the power of the command line comes from the relative ease of combining multiple commands that each do one small thing to do something more complex. You're probably better of getting a book like "[The Linux Command Line]("http://www.linuxcommand.org/tlcl.php/index.php")" and working through the first few chapters then looking at a list of commands and working through their man pages.

Holger

---

### Post by Skaperen on 2020-10-20
the most important command to learn (first) is also one of the easiest to use:  [COLOR=#0000ff][FONT=courier new]**man**[/FONT][/COLOR]

---

### Post by kc1di on 2020-10-21
> **Skaperen said:**
> the most important command to learn (first) is also one of the easiest to use:  [COLOR=#0000ff][FONT=courier new]**man**[/FONT][/COLOR]

As Skaperen has said almost every program in Ubuntu has a text manual that can be accessed via the terminal and will answer may of your questions.  I guess the question is what is it you would like to learn.  Narrow it down a bit for us as you can see from the replies this is a vast area of learning.  There are actually on line and in person courses on the subject.  A simple search of the internet will yield a vast amount of information for you to consider.  

What specifically are you looking to learn, that is the question we need  answered first, so we can correctly direct you.  
Good luck in your learning and most of all have fun doing so.

---

### Post by dezintop on 2020-10-21
> **kc1di said:**
> Hello And Welcome to Ubuntu Linux.
You can learn a lot from [this tutorial.]("https://ubuntu.com/tutorials/command-line-for-beginners#1-overview")
and [this list]("https://www.dummies.com/computers/operating-systems/linux/common-linux-commands/") will help.

Thank you.

---

### Post by dezintop on 2020-10-21
Thanks all for sharing resources.

---

### Post by TheFu on 2020-10-21
> **Holger_Gehrke said:**
> There are various "Cheat Sheets" out there. Ask your favourite search engine for "Linux commands cheat sheet" or "Ubuntu commands cheat sheet". The problem with these is that they are meant mostly as a reference and not as a learning tool. Unless you understand some basic concepts (users and permissions, hierarchical file system and current working directory, standard IO redirection and piping, substitutions, return values of commands, flow control - meaning loops and decisions) these don't make much sense, especially since a lot of the power of the command line comes from the relative ease of combining multiple commands that each do one small thing to do something more complex. You're probably better of getting a book like "[The Linux Command Line]("http://www.linuxcommand.org/tlcl.php/index.php")" and working through the first few chapters then looking at a list of commands and working through their man pages.

Holger

Exactly.  

The "why" is usually more important than the actual commands, but learning what is possible, when to use the commands, with techniques that aren't intuitively obvious is much harder.  A book like [http://www.linuxcommand.org/tlcl.php/index.php](http://www.linuxcommand.org/tlcl.php/index.php) or a mentor or a local Linux Group (google for "LUG") can really help bridge the "why" with the "what to type, when" knowledge.  

Plus the specific types of skills for the work to be done varies greatly.  Many of the posts here are from end-users. Based on some other posts in these forums, I've gotten the impression the OP plans to be a web-app developer, so learning a shell and a little bash scripting will be extremely useful. Scripting comes after learning the basics.  [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) is pretty useful knowledge for being efficient on a command line. That link has some efficiency enhancing commands and links to other resources near the bottom, but the dense stuff at the top is were the daily use skills come in.  I use redirection a few times every day, for example.

---

### Post by dezintop on 2020-10-22
> **ajgreeny said:**
> I'm not sure this will actually help you much as it's a very long list of just about every command available in bash but here it is anyway; make use of it if you find it helps.
[https://ss64.com/bash/](https://ss64.com/bash/)

good staff. thx

---

