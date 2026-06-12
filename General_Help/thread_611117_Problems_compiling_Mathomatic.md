---
title: "Problems compiling Mathomatic"
date: 2007-11-12
forum: General Help
---

### Post by bluehue on 2007-11-12
Hello everyone,

I want to install the latest version of Mathomatic (12.7.9) and I'm having troubles compiling from source. The file is 'mathomatic-12.7.9.tar.bz2' available at [http://www.mathomatic.org/math/index.html](http://www.mathomatic.org/math/index.html). Here's what the installation instructions suggest:
```

The requirements for easy installation from source are the Unix or GNU make
utility and the GCC C compiler.  Other C compilers may be used, but may
require slight modification of the makefile and sources.  You will need to
open a shell window to compile and run Mathomatic.  You need root
(super-user) permissions to install Mathomatic.

A typical installation is done by typing the following at the shell prompt:

	make READLINE=1
	make test
	sudo make install

This will compile, test, and install the Mathomatic executable and docs in
"/usr/local" in less than a minute.  Type "mathomatic" at the shell prompt to
run Mathomatic.  If Mathomatic doesn't run, check that the shell "PATH"
environment variable includes "/usr/local/bin".

If "sudo" doesn't work, type:

	su -c "make install"

and enter the root password.

To completely remove Mathomatic from the system, type:

	sudo make uninstall
```
And here's my compilation error output:
```

spiral@spiral-desktop:~/Desktop/mathomatic-12.7.9$ make READLINE=1
cc -Wuninitialized -Wshadow -Wformat -Wparentheses -Wcast-align  -O -DUNIX -DVERSION=\"`cat VERSION`\"  -DREADLINE   -c -o main.o main.c
In file included from main.c:37:
includes.h:8:19: error: stdio.h: No such file or directory
includes.h:9:20: error: stdlib.h: No such file or directory
includes.h:10:20: error: unistd.h: No such file or directory
includes.h:12:20: error: libgen.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
                 from includes.h:14,
                 from main.c:37:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
In file included from main.c:37:
includes.h:15:18: error: math.h: No such file or directory
includes.h:16:20: error: setjmp.h: No such file or directory
includes.h:17:19: error: ctype.h: No such file or directory
includes.h:18:20: error: string.h: No such file or directory
includes.h:19:19: error: errno.h: No such file or directory
includes.h:20:20: error: signal.h: No such file or directory
includes.h:25:31: error: readline/readline.h: No such file or directory
In file included from includes.h:32,
                 from main.c:37:
externs.h:70: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
externs.h:71: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘jmp_save’
main.c:38:23: error: sys/ioctl.h: No such file or directory
main.c:39:21: error: termios.h: No such file or directory
main.c: In function ‘main’:
main.c:59: warning: incompatible implicit declaration of built-in function ‘strdup’
main.c:59: warning: passing argument 1 of ‘strdup’ makes pointer from integer without a cast
main.c:66: error: ‘gfp’ undeclared (first use in this function)
main.c:66: error: (Each undeclared identifier is reported only once
main.c:66: error: for each function it appears in.)
main.c:66: error: ‘stdout’ undeclared (first use in this function)
main.c:81: warning: incompatible implicit declaration of built-in function ‘fprintf’
main.c:81: error: ‘stderr’ undeclared (first use in this function)
main.c:82: warning: incompatible implicit declaration of built-in function ‘exit’
main.c:97: error: ‘NULL’ undeclared (first use in this function)
main.c:101: warning: incompatible implicit declaration of built-in function ‘exit’
main.c:113: warning: incompatible implicit declaration of built-in function ‘fprintf’
main.c:114: warning: incompatible implicit declaration of built-in function ‘exit’
main.c:117: warning: incompatible implicit declaration of built-in function ‘printf’
main.c:123: warning: incompatible implicit declaration of built-in function ‘printf’
main.c:133: warning: incompatible implicit declaration of built-in function ‘fprintf’
main.c:143: warning: incompatible implicit declaration of built-in function ‘printf’
main.c:145: error: ‘jmp_save’ undeclared (first use in this function)
main.c:150: warning: incompatible implicit declaration of built-in function ‘printf’
main.c:160: warning: incompatible implicit declaration of built-in function ‘fprintf’
main.c:166: warning: incompatible implicit declaration of built-in function ‘fprintf’
main.c:181: warning: incompatible implicit declaration of built-in function ‘snprintf’
main.c: In function ‘usage’:
main.c:195: warning: incompatible implicit declaration of built-in function ‘fprintf’
main.c:195: error: ‘stderr’ undeclared (first use in this function)
main.c:206: warning: incompatible implicit declaration of built-in function ‘exit’
main.c: In function ‘set_signals’:
main.c:219: error: ‘SIGFPE’ undeclared (first use in this function)
main.c:219: error: ‘SIG_ERR’ undeclared (first use in this function)
main.c:221: error: ‘SIGINT’ undeclared (first use in this function)
main.c:223: error: ‘SIGWINCH’ undeclared (first use in this function)
main.c: In function ‘load_rc’:
main.c:262: error: ‘FILE’ undeclared (first use in this function)
main.c:262: error: ‘fp’ undeclared (first use in this function)
main.c:263: error: ‘PATH_MAX’ undeclared (first use in this function)
main.c:274: warning: assignment makes pointer from integer without a cast
main.c:275: error: ‘NULL’ undeclared (first use in this function)
main.c:277: warning: incompatible implicit declaration of built-in function ‘snprintf’
main.c:282: warning: assignment makes pointer from integer without a cast
main.c: In function ‘fphandler’:
main.c:300: warning: incompatible implicit declaration of built-in function ‘printf’
main.c: In function ‘inthandler’:
main.c:311: warning: incompatible implicit declaration of built-in function ‘printf’
main.c: In function ‘alarmhandler’:
main.c:322: warning: incompatible implicit declaration of built-in function ‘printf’
main.c: In function ‘get_screen_size’:
main.c:332: error: storage size of ‘ws’ isn’t known
main.c:336: error: ‘TIOCGWINSZ’ undeclared (first use in this function)
main.c: In function ‘exit_program’:
main.c:364: warning: incompatible implicit declaration of built-in function ‘printf’
main.c:368: warning: incompatible implicit declaration of built-in function ‘exit’
make: *** [main.o] Error 1
```
```

spiral@spiral-desktop:~/Desktop/mathomatic-12.7.9$ make test
Testing Mathomatic...
time: cannot run ../mathomatic: No such file or directory
Command exited with non-zero status 127
0.00user 0.00system 0:00.00elapsed ?%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+70minor)pagefaults 0swaps
make: *** [test] Error 127
```
```

spiral@spiral-desktop:~/Desktop/mathomatic-12.7.9$ sudo make install
[sudo] password for spiral:
install -d /usr/local/bin
install -d /usr/local/man/man1
install -d /usr/local/share/doc/mathomatic
install -d /usr/local/share/doc/mathomatic/html
install -d /usr/local/share/doc/mathomatic/m4
install -d /usr/local/share/doc/mathomatic/tests
install -d /usr/local/share/doc/mathomatic/factorial
install -m 0755 mathomatic  /usr/local/bin
install: cannot stat `mathomatic': No such file or directory
make: *** [install] Error 1
spiral@spiral-desktop:~/Desktop/mathomatic-12.7.9$ 
```
I think I've followed the instructions right down to the 'T' but for some reason I cannot compile and install. Anybody know what the problem may be? :confused:

---

### Post by taurus on 2007-11-12
Did you install the build-essential package first before you tried to build it?

```
sudo apt-get update
sudo apt-get install build-essential
```

p.s.  If you get an error message when you run a command, no need to run the next two commands because they will not work.  Fix the problem and rerun the first command again.

---

### Post by bluehue on 2007-11-12
Thanks taurus! Worked like a charm! 

I've running gutsy for a little over a week and this is the first time I came across something I needed to compile from source and I had completely forgotten about the above two commands. Thanks again :)

---

