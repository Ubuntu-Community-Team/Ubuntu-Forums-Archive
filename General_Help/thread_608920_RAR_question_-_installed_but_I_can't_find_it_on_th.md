---
title: "RAR question - installed but I can't find it on the system!"
date: 2007-11-10
forum: General Help
---

### Post by willfriedwald on 2007-11-10
for years I have never been able to get RAR to work on my Mac - am sure it's just because I don't know what I am doing - I download these RAR & PAR2 files on the newsgroups, and I have no idea how to unpack and decode them!

I wanted to try doing this on ubuntu & see what happens - 

I installed a program called "RAR" - and the system tells me the program is installed, but I have no idea where!  I don't know how to find it on the system - it doesn't seem to be in any of the applications submenus... how do I find a program?  (unlike mac os x, there's no one apps folder where all the programs are - right?)

thanks!

by the way, I noticed that the PAN newsgroup reader works very well - I get better results than the reader program I was using on Mac.

willfriedwald

---

### Post by songshu on 2007-11-10
you need:

apt-get rar unrar
(think its in universe or it might also be in an medibuntu repo, not really sure.
mind: you don't want the unrar-free)

when you have these instaled you can rar and unrar with your normal installed archiver.

---

### Post by FuturePilot on 2007-11-10
Rar is actually a command line program, however you can access the most basic functions of Rar using the Archive Manger.

---

### Post by mcduck on 2007-11-10
After installing the 'unrar' package all you need to do is to right-click the archive and select 'Extract here'. In case of a divided archive, do this on the first file and the whole archive will be extracted.

To create rar packages you also need the 'rar' package.

---

### Post by willfriedwald on 2007-11-10
thanks -

what would be the exact terminal command to install the UNRAR application?

(I could swear that I did this via the graphical thing - install/remove programs...)

anyhow, will try it with the terminal command, which I am sure is a "sudo"

thanks!

w

---

### Post by ViRMiN on 2007-11-10
sudo apt-get install unrar

---

### Post by willfriedwald on 2007-11-10
will@will-linux:~$ sudo apt-get install unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  unrar
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 97.0kB of archives.
After unpacking 238kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse unrar 1:3.7.3-1.1 [97.0kB]
Fetched 97.0kB in 1s (95.7kB/s)
Selecting previously deselected package unrar.
(Reading database ... 131056 files and directories currently installed.)
Unpacking unrar (from .../unrar_1%3a3.7.3-1.1_i386.deb) ...
Setting up unrar (1:3.7.3-1.1) ...
will@will-linux:~$ 

well, I gotta admit that seems to have worked .... now let me see if I can actually unpack / decode (or whatever the term is) some par2 files that I downloaded earlier from a newsgroup...

thanks!

---

### Post by ViRMiN on 2007-11-10
If it's Par2 files you need to use to recreate missing files, there are a couple of possibilities; "gpar2" or "pypar" are GUI frontends...

---

