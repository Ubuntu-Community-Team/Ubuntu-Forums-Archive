---
title: "cant install pidgin"
date: 2007-05-25
forum: General Help
---

### Post by louislepperd on 2007-05-25
hi i had lots of trouble installing pidgin 
so i followed the instructions in this [article]("http://ubuntuforums.org/showthread.php?t=441363")
and it still did not work i have attached a picture of what went wrong
thanks in advance
louis

---

### Post by mbradlcu on 2007-05-25
maybe try removing /usr/share/sounds/pidgin/alert.wav? if it exists.. or if not maybe create the dir /usr/share/sounds/pidgin?

---

### Post by amphet on 2007-05-25
I installed it from source without problems

just get the tar from their site, untar then:

sudo apt-get build-dep gaim
./configure
make
sudo make install

---

### Post by louislepperd on 2007-05-25
hi
i downloaded the source
but when i extracted it there was an error and i haven't compiled source before so im not to sure how to do it
thanks in advance
Louis
this was the error
bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

---

### Post by mbradlcu on 2007-05-26
this worked for me:
```
tar -jxvf pidgin-2.0.1.tar.bz2 
```
check out the readme as it will explain what packages you'll need to have installed on your system to build it.. build-essentials, GTK+ and the dev packages,, libgtkspell (important for guys like me)

---

### Post by watkinsted on 2007-11-11
I downloaded pidgin-2.2.2 the libxml parser perl module the GLib 2.0 dev headers and the GTK+ 2.0 dev headers and then typed in ./configure.  It configures successfully and tells me to type 'make'.  When I do this is what i get:

Use kerberos 4 with zephyr.... : no
Use external libzephyr........ : no
Has you....................... : yes

Use XScreenSaver Extension.... : no
Use X Session Management...... : yes
Use startup notification...... : no
Build with GtkSpell support... : no

Build with plugin support..... : yes
Build with Mono support....... : no
Build with Perl support....... : no
Build with Tcl support........ : no
Build with Tk support......... : no

Print debugging messages...... : no

Pidgin will be installed in /usr/local/bin.

configure complete, now type 'make'

ted@ted-desktop:~/pidgin-2.2.2$ make
bash: make: command not found
ted@ted-desktop:~/pidgin-2.2.2$

is there something I'm not aware of?

---

### Post by mbradlcu on 2007-11-11
yea it seems you don't have make? check to see if you installed the 'build-essential' package I believe it has 'make'

---

