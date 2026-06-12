---
title: "iTunes streaming from Ubuntu host"
date: 2005-10-23
forum: General Help
---

### Post by primitive on 2005-10-23
I want to stream songs from my Breezy machine to machines in the apartment that run iTunes.  After doing some research, I need the following packages:

- howl
- mdnsresponder
- daapd

These appear to neither be in the universe or the multiverse for Breezy.  Does anyone have a download site for these packages and their dependencies?

Thanks!
p

---

### Post by chaumurky on 2005-10-23
(ignore)

---

### Post by evil-boweevil on 2005-10-23
mt-daapd.org supplies .deb packages, and I believe I installed the rest of the dependencies from ubuntu repositories.

---

### Post by sciurus on 2005-11-03
I'm thinking of trying this soon. Any tips? I've found instructions for mt-daapd [http://www.macdevcenter.com/pub/wlg/6067](http://www.macdevcenter.com/pub/wlg/6067) and daapd [http://www.macosxhints.com/article.php?story=20030711140157143](http://www.macosxhints.com/article.php?story=20030711140157143)

---

### Post by doclivingston on 2005-11-03
I used to use the mt-daapd .debs from the site, and they worked well.

---

### Post by odyssey on 2005-11-21
Check my HOWTO [here.]("http://dotnet.org.za/matt/articles/48417.aspx"):D

---

### Post by sciurus on 2005-11-25
[QUOTE=odyssey]Check my HOWTO [here.]("http://dotnet.org.za/matt/articles/48417.aspx"):D[/QUOTE]

That worked swimmingly. Thanks. For anyone who's interested, <a href="http://wiki.mt-daapd.org/wiki/SSH_Tunnel">this</a> will show you how to access your share across subnets.

---

### Post by prasys on 2005-12-05
Kudos for the superb how-to..Worked for me fine !

---

### Post by Robocoastie on 2005-12-05
I'm going to follow those howto's but I am curious as to what the advantage of streaming the music is over just having the music in a shared directory and setting your iTunes computer(s) to use that share for its library? Is it because iTunes doesn't have a monitor feature like just about every other media player out there from MSFT Media Player to the *nix ones?:confused: 

thanks,

Rob

edit/update:

I'm trying to use 64bit Ubuntu only so mt-daapd must be compiled rather than by the i386.deb. My question is though what do I put in for the dir=
I'm guessing configure needs to be told where to find the build tools. Here's what I encountered to be exact:

```

rob@dell5100:~/mt-daapd-0.2.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for bison... no
checking for byacc... no
checking for flex... no
checking for lex... no
checking for flex... /home/rob/mt-daapd-0.2.2/missing flex
checking for yywrap in -lfl... no
checking for yywrap in -ll... no
checking lex output file root... lex.yy
checking whether yytext is a pointer... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for pthread_creat in -lc_r... no
checking for pthread_create in -lpthread... yes
Host type is x86_64-unknown-linux-gnu
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking gdbm.h usability... no
checking gdbm.h presence... no
checking for gdbm.h... no
configure: error: gdbm.h not found... try --with-gdbm-includes=dir
rob@dell5100:~/mt-daapd-0.2.2$ loc gdbm.h
bash: loc: command not found
rob@dell5100:~/mt-daapd-0.2.2$ locate gdbm.h
rob@dell5100:~/mt-daapd-0.2.2$ sudo locate gdbm.h
rob@dell5100:~/mt-daapd-0.2.2$
gggrrr finding stuff is a pain...must learn the find and locate commands better....

```

---

### Post by billputer on 2005-12-07
It looks like you need the "libgdb-dev" development libraries.  A simple "apt-get install libgdb-dev" should suffice.

You may need other development libraries as well.  I suggest that whenever you get a "xxxx.h" not found, that you type the "xxxx" into synaptic, and see if you get anything that may contain those dependencies.

---

