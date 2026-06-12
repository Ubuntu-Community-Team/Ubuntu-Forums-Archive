---
title: "Lubuntu 18.04.2 LTS - Terminal Commands &amp; Folder Organization"
date: 2019-04-24
forum: General Help
---

### Post by electrosteam on 2019-04-24
Is there a defining list of the terminal commands and folder organization for Lubuntu ( 18.04.2 )?

Searching for previously reported problems/solutions often brings up suggestions that do not apply to my system, due to older versions and/or different distributions.

I eventually always muddle through, but the memory lets me down for the next issue.

John.

---

### Post by TheFu on 2019-04-24
```
ls /bin
ls /usr/bin
ls /sbin
ls /usr/sbin
ls /usr/local/bin
```
Those commands will get you some lists of commands.

Almost every program you see in those directories has a manpage, which should describe in detail how to use it with all the options.  man {command}

Folders are a GUI thing.  Directories are laid out in the *Linux File System Hierarchy Standards*.  All the major distros follow it.  [https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)  Everything after that is controlled by each individual project. Gnome does things differently than KDE.  

If you want to have a much better understanding of all this, [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) has a good intro.  Eventually, things will start to "click" as you gain more and more time to see the subtle genius in how everything fits together.

And if someone suggests that you run a command like **lshw -C network** and that returns a "command not found", then just install it.  Linux systems have all sorts of tools, but they aren't all installed up front.  Not everyone wants everything pre-installed.  Sometimes using minimal disk storage is an important consideration.  Other times, eating an extra 1G of storage to have everything pre-installed is not an issue.

---

### Post by yancek on 2019-04-24
Googling Linux terminal commands should get you numerous sites such as the one below.  Putting Lubuntu or Ubuntu in the search field will help immensely.  A problems I see often is sites with 'explanations' of something with no date.  Computer operating system change rapidly so I generally ignore sites with no date.  I'm not sure what you mean by 'folder organization' but keeping notes on problems and hopefully solutions is always a good idea.

[https://fossbytes.com/a-z-list-linux-command-line-reference/](https://fossbytes.com/a-z-list-linux-command-line-reference/)

---

### Post by electrosteam on 2019-04-25
Thanks guys, great information and links.

The Fu,
I now have an icon on the desktop for xman, a plan to print out all the various ...bin contents, a bookmark to to the filesystem hierarchy and a copy of the command line introduction.

yancek,
the command line reference duly bookmarked, thank you.

Now on to my current issue, getting a new (to me ) video card (superseded chips) operational.
John,

---

### Post by TheFu on 2019-04-25
I wouldn't suggest printing anything.  With every upgrade command, the manpages are modified and options can change. Seldom do you need **all** the information contained in a manpage.

The link to tlcl.php - is a free pdf book.  You can buy it at any bookstore, if you like, but the PDF is just as good, maybe better, if you have a tablet. If you want to really learn Linux, here's a few of my blogs about that: 
[https://blog.jdpfu.com/2017/09/12/linux-command-line-or-shell-resources](https://blog.jdpfu.com/2017/09/12/linux-command-line-or-shell-resources)
[https://blog.jdpfu.com/2014/12/28/learning-linux](https://blog.jdpfu.com/2014/12/28/learning-linux)

---

