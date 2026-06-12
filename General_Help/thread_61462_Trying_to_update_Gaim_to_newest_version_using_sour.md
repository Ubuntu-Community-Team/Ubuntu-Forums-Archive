---
title: "Trying to update Gaim to newest version using source"
date: 2005-08-31
forum: General Help
---

### Post by schizoid_embolism on 2005-08-31
Hi everybody,

I'm using Gaim version 1.1.4 and am trying to install 1.5.0.  I'm trying to do this by compiling the source downloaded from the Gaim website.  I'm pretty much a newbie to Linux so maybe this is too advanced of a project for me.  I prefer to try the source rather than the autopackage so that I can get a better understanding of how things work.

Now I don't know if I'm doing things correctly but I figured I should extract the files out of gaim-1.5.0-0.src.rpm (as well as the tar.gz file inside it).  Now I have a folder on my Desktop called gaim-1.5.0 with a bunch of files in it.  One of these files is called Install and has some instructions on compiling the program.  Following these instructions, I went to the command line, went into the directory where the files are, and typed ./configure which produced the following output:

> checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for sed... /bin/sed
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

I suspect I'm doing something obviously wrong and somebody can point me in the right direction if so.  If not, and I need to paste my config.log file to this thread, please let me know.

Thank you,

Jeremy

---

### Post by jasmuz on 2005-08-31
You need to open a terminal and type sudo apt-get build-essential
wich will download and install the compilers for your system.
Then proceed to compile.

---

### Post by schizoid_embolism on 2005-09-01
Boy have I managed to screw things up!

First of all, jasmuz, thank you for your quick reply.  I followed your suggestion and was moving right along, when I got a new error message, telling me I needed this thing called GTK+.  So I go to the website, start downloading the libraries, which depend on more libraries, which depend on more libraries...

After downloading about eight different library packages and installing each of them, I was at the point to where I could install GTK.  Well, one of these libraries that GTK wanted me to install were these jpeg libraries, called jpegsrc.v6b.tar.gz.   This one gave me a bit of trouble because even after I installed it, GTK still insisted I didn't have it.  So I found that it wasn't installing to my /usr/local/lib directory like all the other libraries were, but to /usr/local/bin instead.

During the course of my downloading libraries, I found that I had to add a line to my /etc/ld.so.conf file that said /usr/local/lib.  I assumed that the purpose of this file must be to point to directories where my libraries are so that programs I install will find them, or something.  So I went ahead and added a line to the file that said /usr/local/bin, and ran /sbin/ldconfig (which I assume tells Linux to put the ld.so.conf file into action or something).  At that point everything in Linux stopped responding, and I had to restart.

When Linux tried to start back up, the screen kept flashing, and it took me to a strange screen that said that it tried to start the 'display server' 6 times in a row and failed each time and then dropped me to a command line.  So I stumbled my way through that INSANE text editor Vi to delete that line I put in the /etc/ld.so.conf file and save it.  Then I rebooted, and still I get the same problem.   No display.  Am I SCREWED?  Will I have to re-install?

Jeremy

---

### Post by Seth on 2005-09-01
Oh dear me.

The whole point of the apt package management system is that you **never** just go installing libraries and development headers from source.

There are a whole bunch of -dev packages in Synaptic. That's all you needed to install, and it would have automatically given you all the files you needed.

At this point a reinstall would probably be a good idea. Search "-dev" in Synaptic when you get back and check out the yummy development headers.

---

### Post by schizoid_embolism on 2005-09-01
LOL I had a feeling I messed it up good this time.

Yeah I guess I better re-install.  So you were saying I need to use Synaptic, is this similar to apt-get?  I remember reading a thread on this forum somehwere where somebody was explaining how apt-get is better.. is it possible to get these -dev packages that way?

Jeremy

---

### Post by Elrohir on 2005-09-01
Imagine Synaptic as the GUI for apt-get...

on another thread around here, there's a link for the .deb file which is the latest version (1.5.0)... try downloading that one and install through command-line: ```
dpkg - gaim*.deb
``` have fun...

---

### Post by taktu on 2005-09-01
i'm also having trouble compiling gaim 1.5.0. the configure file looks ok:

```
Build with Plugin support..... : yes
Build with Perl support....... : yes
Build with Tcl support........ : no
Build with Tk support......... : no
Build with Audio support...... : yes
Build with NAS support........ : no
Build with GtkSpell support... : yes

Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no

Use XScreenSaver Extension.... : no
Use X Session Management...... : yes
Use startup notification.......: yes

Print debugging messages...... : no

Gaim will be installed in /usr/local/bin.

configure complete, now type 'make'
``` 

the problems appear when i type 'make':

```
libtool: link: warning: `/usr/lib/gcc-lib/powerpc-linux/3.3.5/../../..//libglib-2.0.la' seems to be moved
/bin/sed: can't read Downloads/gaim-1.5.0/plugins/gaim-remote/libgaim-remote.la: No such file or directory
libtool: link: `Downloads/gaim-1.5.0/plugins/gaim-remote/libgaim-remote.la' is not a valid libtool archive
make[3]: *** [gaim-remote.la] Error 1
make[3]: Leaving directory `/home/msuciu/My Downloads/gaim-1.5.0/plugins/gaim-remote'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/msuciu/My Downloads/gaim-1.5.0/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/msuciu/My Downloads/gaim-1.5.0'
make: *** [all] Error 2
``` 

i used sudo so i understand it's not a permission problem. it's just that i don't really know what's wrong, please help me!

i'm using Hoary 5.04 on a g4 ppc processor. (dunno if that helps anyone)

---

### Post by mcduck on 2005-09-01
[QUOTE=schizoid_embolism]
So I stumbled my way through that INSANE text editor Vi
[/QUOTE]
This sure is a bit offtopic, but for future's sake you may want to install Jed. It's a commandline text editor very similiar to 'Edit' in DOS/Win. Way easier to use than Vi. Sooner or later you'll need it ;)

---

### Post by schizoid_embolism on 2005-09-02
Success!  Thank you everybody for all your help.

And Synaptic kicks ass  :grin:

I had a feeling that downloading, compiling & installing all those packages manually was not appropriate  :lol: 

Jeremy

---

### Post by Elrohir on 2005-09-02
from source? still have my doubts... from deb files, I trust more on those than myself... :razz:

---

### Post by taktu on 2005-09-02
[QUOTE=taktu]i'm also having trouble compiling gaim 1.5.0.[/QUOTE]

well... i finally got gaim running. the key was running make with -ik options. had my doubts that it would do any good, but gaim seems to be fully functional.

---

### Post by MetalHannes on 2005-09-04
I have the same problems with the new Gaim installation but when i type sude apt-get build-essential it says that build-essential is not a valid option
+
wenn i connect to MSN it says that my username and psswrd are wrong. But i am very sure that they are yorrect can somebody lease help me??

thx very much

Hannes

---

### Post by MetalHannes on 2005-09-04
OK i fixed the MSN problem but i would love to have the nweset gaim...

thx anyway

Hannes

---

### Post by plb on 2005-09-04
why don't you guys just use the gaim autopackage installer from sourceforge? Just run the script and voila gaim 1.5

---

### Post by MetalHannes on 2005-09-04
Its not just about gaim i want to install other program and they give the same errors(asc and KBear)

thx

Hannes

---

