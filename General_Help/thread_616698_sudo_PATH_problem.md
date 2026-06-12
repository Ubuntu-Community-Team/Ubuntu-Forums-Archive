---
title: "sudo PATH problem"
date: 2007-11-18
forum: General Help
---

### Post by MicahWedemeyer on 2007-11-18
There are similar threads on this, but none have contained any information to help me out.  So, here comes another.

Basically, it's become painfully obvious that sudo has a different PATH than me and the root account.  Take a look:

As me:
> mwedemeyer@obsidianportal:~$ env | grep PATH
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/var/lib/gems/1.8/bin

As root:
> mwedemeyer@obsidianportal:~$ sudo -i 
root@obsidianportal:~# env | grep PATH
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/var/lib/gems/1.8/bin:/var/lib/gems/1.8/bin
(It's on there twice because I've been playing with A LOT of path-setting files...)

From sudo:
> mwedemeyer@obsidianportal:~$ sudo env | grep PATH
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

I have edited /etc/bash.bashrc, /etc/profile, /root/.bashrc, and /home/mwedemeyer/.bashrc to add the export line, and it seems to do nothing.

If anyone has any ideas, it would be greatly appreciated.  I'm trying to run mongrel_rails from sudo and it cannot find it.  It's becoming a major pain...

---

### Post by fjgaude on 2007-11-18
Seems to have something to do with not wishing anyone to be root when in "games", eh?

I don't have a clue as to what would fix this.

My three situations are just like your, me, root, sudo.

---

### Post by scorp123 on 2007-11-18
> **MicahWedemeyer said:**
>  Basically, it's become painfully obvious that sudo has a different PATH than me and the root account.  Sorry if this is a stupid question: But what exactly are you trying to achieve? How does the path being different in "sudo" negatively affect you? Again sorry if this is a stupid question ...

Just as a general hint ... Let's suppose you're trying to execute something via "sudo" (e.g. something you put in a directory outside any of the PATH variables?) then executing something like "sudo mycommand" will probably fail ... because if the directory is not in your path "sudo" won't be able to find what you try to execute.

Add a "./" ... This means "right here" in UNIX lingo and translates back into the current path being used. So while "sudo mycommand" might fail "sudo ./mycommand" will most likely work.

Hope this helped?

---

### Post by MicahWedemeyer on 2007-11-18
> **scorp123 said:**
> Sorry if this is a stupid question: But what exactly are you trying to achieve? How does the path being different in "sudo" negatively affect you? Again sorry if this is a stupid question ...

When I installed rubygems (a development tool for Ruby), it installed several useful tools in the /var/lib/gems/1.8/bin directory.  Some of these would be nice to run as root.  From the command line, I can do "sudo /var/lib/gems/1.8/bin/blah_blah"  However, some of the automated tools I've found (ie. mongrel_cluster and capistrano) are built around being able to sudo and execute commands from the rubygems bin.  Since the bin isn't on the PATH, the tools don't work.

---

### Post by scorp123 on 2007-11-19
> **MicahWedemeyer said:**
>  When I installed rubygems (a development tool for Ruby), it installed several useful tools in the /var/lib/gems/1.8/bin directory.  Some of these would be nice to run as root.  I'd take a different strategy there. If there are not too many files in that directory and if their names do not collide with any system-relevant program name (please check that before you do anything) you could create symbolic links between the files in **/var/lib/gems/1.8/bin/** to **/usr/bin/** ... So all the files in **/var/lib/gems/1.8/bin/** would also be reachable via **/usr/bin** ... I am sure "sudo" can find stuff there regardless of what the differences between the $PATH variables between the various accounts are ... **/usr/bin** is most likely always in the list any account will look into when searching for a program.

Another idea could be to modify **/etc/environment** .... As far as I can tell that file defined the system-wide $PATH variable every account gets on a system?

---

