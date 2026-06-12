---
title: "Unix, GNU and bash"
date: 2013-09-22
forum: General Help
---

### Post by sark89 on 2013-09-22
Hi all, 
I seem to be getting myself confused with all the media out there talking about unix, gnu etc etc. Can anyone tell me what the real difference between unix and gnu? What I gather is that gnu is a unix-like operating system and that bash is the command shell so why then when I type bash commands on a mac it doesn't understand the command despite it being a bash shell. But is OS X a unix OS compared to Linux being gnu? Are all Linux distros gnu? If all Linux distros are gnu and use the same command shell, why if I was to run the command to unzip a file on say kali I'd type -zxvf where as on mint I run this command and it doesn't work and uses a different command. 
As you can imagine its rather frustrating! I look forward to peoples answers, hopefully not ones calling me a noob or what have you, we all have to start somewhere. 
Thanks.

---

### Post by Lars Noodén on 2013-09-22
bash is just the user interface that lets you connect to the user-space utilities on  the system.  These utilities include ls, cd, mv, rm, and tens of thousands of others.  There are other shells to provide about the same UI, such as tcsh and ksh, instead of bash.  But they all allow you to run the various utilities on your system.   So if you run **tar** any of them it can be **tar** from GNU's [tar](http://manpages.ubuntu.com/manpages/raring/en/man1/tar.1.html) or BSD's [tar](http://www.openbsd.org/cgi-bin/man.cgi?query=tar&apropos=0&sektion=0&manpath=OpenBSD+Current&arch=i386&format=html).  OS X has a fair number of GNU utilities, but really it is based on BSD.  So quite a few of the utilities you will find there differ from the GNU utilities in small ways.  

Look in /bin, /sbin, /usr/bin, and /usr/sbin to see some of these utilities.  

Most linux distros are GNU (RHEL, Mageia, Debian, Knoppix, etc).  Pretty much anything you would run on the desktop or a server will be GNU/Linux.  There is of course on mobile devices now the distros based on Android/Linux, which has the Linux kernel but a different set of user-space tools.  I'm not sure where ChromeOS stands, but it is probably not GNU either even if it is certainly Linux.

---

### Post by santosh83 on 2013-09-22
> **sark89 said:**
> Hi all, 
I seem to be getting myself confused with all the media out there talking about unix, gnu etc etc. Can anyone tell me what the real difference between unix and gnu? What I gather is that gnu is a unix-like operating system and that bash is the command shell so why then when I type bash commands on a mac it doesn't understand the command despite it being a bash shell. But is OS X a unix OS compared to Linux being gnu? Are all Linux distros gnu? If all Linux distros are gnu and use the same command shell, why if I was to run the command to unzip a file on say kali I'd type -zxvf where as on mint I run this command and it doesn't work and uses a different command. 
As you can imagine its rather frustrating! I look forward to peoples answers, hopefully not ones calling me a noob or what have you, we all have to start somewhere. 
Thanks.

Back in the 1970s and 80s UNIX systems were commercial and source code was restricted and users were not allowed to modify the system. Richard Stallman the founder of GNU project and FSF thought this was an unacceptable restriction on computing freedoms and started the so-called GNU project in 1984 to develop a UNIX-like operating system right from scratch, but now one which had freely available source code and allowed modifications and reuse, under the GPL license which also he conceived.

He was successful in creating all the basic utilities of such a system, as well as the toolchain to compile it, but the kernel subsystem he started (GNU Hurd) got seriously lagging, and to date is nowhere near practically useful state. But it so happened that that didn't matter cause by 1991 a Finnish computing student, Linus Torvalds, authoured the core of a UNIX-like kernel and decided to release it under GPL. This Linux kernel then took off enormously and later became the de facto kernel underneath all the GNU utilities and toolchain. This is why Stallman wants everybody to call Linux distributions as "GNU/Linux"... i.e., to recognise the fact that a significant and important part of it (the basic utilities and toolchain) came from the GNU project, while the kernel of course is Linux.

Bash is GNU's implementation of sh, a popular UNIX shell. In sh compatibility mode, bash will accept all sh commands although it is now much more complex than sh. I don't know whether the shell in Mac is bash, having never used a Mac. Perhaps the command you invoked was something that doesn't exist on a Mac system? What command was it?

As for OS X, I've never used an Apple product so rather than my own words I'll just quote the relevant wikipedia bits.

"OS X is based upon the Mach kernel. Certain parts from FreeBSD's and NetBSD's implementation of Unix were incorporated in NeXTSTEP, the core of Mac OS X. NeXTSTEP was the graphical, object-oriented, and UNIX-based operating system developed by Steve Jobs' company NeXT after he left Apple in 1985.  Eventually, NeXT's  OS, then called  OPENSTEP , was selected to be the basis for Apple's next OS, and Apple purchased NeXT outright. OS X's core is a  POSIX  compliant operating system (OS) built on top of the  XNU kerne l, with standard Unix facilities available from the  command line interface . Apple has released this family of software as a  free  and  open source  operating system named Darwin. On top of Darwin, Apple layered a number of components, including the Aqua interface and the Finder, to complete the GUI-based operating system which is OS X. Since OS X is POSIX compliant, many software packages written for the *BSDs, Linux, or other Unix-like systems can be recompiled to run on it."

---

### Post by Lars Noodén on 2013-09-22
If you want to get a general idea of where OS X fits in, look at Éric Lévénez's timeline around 1999:

[http://www.levenez.com/unix/](http://www.levenez.com/unix/)

But that's mostly the kernel not the utilities.

---

### Post by santosh83 on 2013-09-22
> **Lars Noodén said:**
> If you want to get a general idea of where OS X fits in, look at Éric Lévénez's timeline around 1999:[ http://www.levenez.com/unix/]("http://www.levenez.com/unix/")

Awesome page! TFS.

---

### Post by sark89 on 2013-09-22
Wow thanks for your detailed replies! They answered my question quite nicely! :D So am I right in saying then that Unix was created and so people created a version of Unix called GNU which allowed access to the source code this then led to operating systems like Linux. So it looks like then that OS X is a Unix based operating system which uses some features from GNU such as the bash shell which then answers why some GNU commands won't work on OS X where as some will since only uses some features. Very interesting stuff. I was doing some research on books which would be a good reference on getting to grips with the command shell on Linux. I came across The Linux Command Line: A Complete Introduction which seems to get some good reviews however I'm just concerned that different distros use different commands. I wouldn't want to buy this book and use it on a distro only to find it was a bit of a waste as the commands won't work! 
Once again thank you for your replies :D

---

### Post by santosh83 on 2013-09-22
> **sark89 said:**
> Wow thanks for your detailed replies! They answered my question quite nicely! :D So am I right in saying then that Unix was created

During the 70s, 80s and 90s there were a variety of operating systems (anscestor of which was from Bell Labs, 1969) which followed a set of common conventions and commands and they came to be known as the UNIX family of operating systems. Later a consortium (The Open Group) also purchased the rights to the name UNIX and now labels any system as "UNIX" when they go through it's certification process, though very few otherwise practically UNIX compatible systems do, since the certification is expensive. When talking about UNIX a closely related term is POSIX, which is a standardised set of conventions and tools that allow interoperability between any operating systems that implement the POSIX standard. The POSIX interface is was historically modelled after the existing interfaces and tools of the UNIX systems of the day, so a POSIX compliant system is practically a UNIX even if it never went through a formal certification from Open Group.

>  and so people created a version of Unix called GNU which allowed access to the source code this then led to operating systems like Linux. 

More or less although when using the term Linux there's an ambiguity as to whether you're talking about the kernel alone (to which the term strictly applies) or a complete operating system built around the kernel. There can be non-UNIX operating systems built on top of Linux kernel and there can be UNIX compliant systems which arose completely outside the UNIX family tree. I think Android is an example of the former, can't think of any for the latter!

> I was doing some research on books which would be a good reference on getting to grips with the command shell on Linux. I came across The Linux Command Line: A Complete Introduction which seems to get some good reviews however I'm just concerned that different distros use different commands. I wouldn't want to buy this book and use it on a distro only to find it was a bit of a waste as the commands won't work! 

Generally you'll find broad compatibilty among the majority of Linux distributions for all the common command line tools and tasks. While they do differ I don't think you'll encounter the differences while still a command-line beginner. Much of this compatibility extends to all POSIX compliant systems. Many of these basic commands will work on the BSDs too for example, and so should work on a Mac too. Any gotchas should be explained in any good command-line book, though I don't know how good the book you cited is. The one I use is O'Reilly's Linux in a Nutshell.

[http://en.wikipedia.org/wiki/UNIX](http://en.wikipedia.org/wiki/UNIX)
[http://en.wikipedia.org/wiki/POSIX](http://en.wikipedia.org/wiki/POSIX)

---

### Post by sark89 on 2013-09-22
I see so Linux really refers to the kernel not the operating system built around it. Thank you very much for that detailed message. I think I'll have to check out that book you mentioned! :D
Thanks again.

---

### Post by Lars Noodén on 2013-09-23
The Debian distro is an interesting example.  It is most known for its GNU/Linux version.  However, it is also working on parallel distros that use the FreeBSD kernel and the Hurd Mach microkernel, both still using GNU.  

[https://wiki.debian.org/Debian_GNU/kFreeBSD_FAQ](https://wiki.debian.org/Debian_GNU/kFreeBSD_FAQ)
[https://wiki.debian.org/Debian_GNU/kFreeBSD_why](https://wiki.debian.org/Debian_GNU/kFreeBSD_why)

[http://www.debian.org/ports/hurd/](http://www.debian.org/ports/hurd/)

So you have Debian GNU/Linux, Debian GNU/xFreeBSD and Debian GNU/Hurd.

Most users don't worry too much about the kernel as it is the system component that interacts with the hardware and is thus usually the most distant from user interaction.  So if you are and average desktop user you could use any of those three and pretty much not see the difference, it would all be Debian and GNU.

---

### Post by Sef on 2013-09-23
> [COLOR=#000000]So am I right in saying then that Unix was created and so people created a version of Unix called GNU which allowed access to the source code this then led to operating systems like Linux[/COLOR]

Linux is a cousin of Unix, while OSX is a child of Unix.  What I mean is that Linux is based on Unix, but not directly decended from it; but OSX is directly decended from Unix.

---

### Post by buzzingrobot on 2013-09-23
Bash is the default shell on OS X. While Linux uses the "GNU toolset" (the traditional set of character-based tools), OS X uses the "BSD toolset". There are minor differences in options, command invocation, etc., seen in some executables in the two sets. ("BSD" is Berkeley Software Distribution', a famous Unix created at the University of California at Berkeley.

Certain shell commands are sometimes aliased by distros, often to prevent user-inflicted damage or just to tweak them a bit. Perhaps Mint is aliasing tar.

---

### Post by grahammechanical on 2013-09-23
> so people created a version of Unix called GNU

That is not correct. A man called Richard Stallman rebelled against the way software was developed, used, and owned. He came up with the idea of free and open source software development. He refused to use proprietary software to write software. So, he began to develop utilities to write software that he would allow others to install, use and even modify the code of without the need to buy a license.

[http://www.gnu.org/](http://www.gnu.org/)

He and others who collaborated with him had the intention of using these developer utilities to write a free and open souce operating system. That is the GNU operating system. It has the code name of Herd. In no way should it be considered a version of Unix but only Unix like.

In the mean time a man called Linus Torvalds created some utilities based upon the Minix operating system and invited everyone to collaborate in developing his code further. That has progressed into Linux. Those that developed Linux accepted the prinicples of Free and Open source software and used the Gnu developer utilities as well as open source code from the developers of Gnu. This is why some like to speak of Linux as Gnu/linux.

[http://www.minix3.org/](http://www.minix3.org/)

Regards.

---

### Post by buzzingrobot on 2013-09-23
For a few years before the PC market locked into one kind of x86 architecture, there were attempts to market Unix as a PC OS. ATT tried, including selling ATT-branded PC's. Microsoft licensed Unix from ATT and released it as a PC OS  called Xenix.

---

