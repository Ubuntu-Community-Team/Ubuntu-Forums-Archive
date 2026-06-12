---
title: "installing celtx"
date: 2006-10-22
forum: General Help
---

### Post by Chickenfoot on 2006-10-22
Hey Everybody,

I am having some challenges installing Celtx.

On their website, they have a set of [instructions]("http://celtx.com/download.html"):

Couldn't get it to work, so I went to the forums. I was reading these thread:

[http://ubuntuforums.org/showthread.php?t=192129&highlight=celtx]("http://ubuntuforums.org/showthread.php?t=192129&highlight=celtx")

[http://ubuntuforums.org/showthread.php?t=236440&highlight=celtx]("http://http://ubuntuforums.org/showthread.php?t=236440&highlight=celtx")

and then finally, the [How To Install Anything in Ubuntu]("http://www.monkeyblog.org/ubuntu/installing/") thread.

So, here's where I stand:

When I attempted to follow the Celtx instructions, and extract to /users/local, I got an error saying that I didnn't have pemission.

When I attempted to follow the "Anything in Ubuntu" thread, I got this:

chickenfoot@spanky:~$ cd /home/chickenfoot/Desktop/celtx
chickenfoot@spanky:~/Desktop/celtx$ ./configure
bash: ./configure: No such file or directory
chickenfoot@spanky:~/Desktop/celtx$

I then read and installed a compiler:

[COLOR="Red"]Before you want to compile anything from source, you need to install a compile, gcc. So, open a terminal and type
Code:

sudo apt-get install build-essential[/COLOR]

But I still get this error:

chickenfoot@spanky:~$ cd /home/chickenfoot/Desktop/celtx
chickenfoot@spanky:~/Desktop/celtx$ ./configure
bash: ./configure: No such file or directory
chickenfoot@spanky:~/Desktop/celtx$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chickenfoot@spanky:~/Desktop/celtx$ cd /home/chickenfoot/Desktop/celtx
chickenfoot@spanky:~/Desktop/celtx$ cd /home/chickenfoot/Desktop/celtx ./configu re
chickenfoot@spanky:~/Desktop/celtx$ make
make: *** No targets specified and no makefile found.  Stop.
chickenfoot@spanky:~/Desktop/celtx$ make
make: *** No targets specified and no makefile found.  Stop.
chickenfoot@spanky:~/Desktop/celtx$

So, what I am I doing wrong?  Any help would be greatly apperciated!

---

### Post by PriceChild on 2006-10-23
*moves*

---

### Post by cosine7 on 2008-03-09
i had the same problems... try ./celtx

---

### Post by dysaniak on 2008-03-09
I've got the same "problem."

> dysaniak@dysaniak-laptop:~/Desktop/celtx$ ./configure
bash: ./configure: No such file or directory
dysaniak@dysaniak-laptop:~/Desktop/celtx$

What're we noobs missing here?

---

### Post by flicman on 2008-03-10
It's working for this n00b - I followed the [directions on the Celtx.com wiki for Linux]("http://wiki.celtx.com/index.php?title=Installation#For_Linux").  I downloaded the Celtx.tar.gz file to my desktop, opened the Terminal and typed the commands below (modified for my install and download location).

> cd /usr/local

sudo tar zxf /path/to/Celtx.tar.gz

(enter your password)

sudo /usr/local/celtx/celtx 

I then put a link in my "Office" menu by right-clicking Applications and adding a New Item from the main menu editor there because I'm too lazy to type much before, you know, typing a whole screenplay.  I guess I'm just used to the GUI.

*hits self*
Bad Linux user!

Anyway, maybe this helps?

---

### Post by UKHamlet on 2008-05-13
I'm a newbie, but a bit of surfing gave me this:

sudo apt-get install libxul-dev
sudo apt-get install libstdc++5 

This worked for me on Ubuntu 8.04 - I hope it does likewise for you.

---

