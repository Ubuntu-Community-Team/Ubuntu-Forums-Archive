---
title: "Process Terminated with status 255 (0 minutes, 0 secs)"
date: 2014-04-02
forum: General Help
---

### Post by zinat on 2014-04-02
Hi m trying to create a simple hello world plugin in codeblocks but its not showing any output.. **I am using codeblocks version 13.12 and OS ubuntu 12.04..**

-------------- Build: default in test  (compiler: GNU GCC Compiler)---------------

g++  -I/usr/local/include/codeblocks -I/usr/local/include/codeblocks/tinyxml  -I/usr/local/include/codeblocks/scripting/include  -I/usr/local/include/codeblocks/scripting/bindings  -I/usr/local/include/codeblocks/scripting/sqplus  -I/usr/local/include/codeblocks/wxscintilla/include  -I/usr/lib/i386-linux-gnu/wx/include/gtk2-unicode-release-2.8  -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__  -pthread -ansi -fPIC -g -g -fPIC  -c "/home/sakina/Downloads/test/test  /test.cpp" -o .objs/test.o
g++ -shared  .objs/test.o  -o libtest.so  -L/usr/local/lib -lcodeblocks   -L/usr/lib/i386-linux-gnu -pthread  -Wl,-Bsymbolic-functions -Wl,-z,relro  -L/usr/lib/i386-linux-gnu    -lwx_gtk2u_richtext-2.8 -lwx_gtk2u_aui-2.8 -lwx_gtk2u_xrc-2.8  -lwx_gtk2u_qa-2.8 -lwx_gtk2u_html-2.8 -lwx_gtk2u_adv-2.8  -lwx_gtk2u_core-2.8 -lwx_baseu_xml-2.8 -lwx_baseu_net-2.8  -lwx_baseu-2.8  -g  
Output file is libtest.so with size 155.44 KB
Running target post-build steps
zip -j9 test.zip manifest.xml
  adding: manifest.xml (deflated 53%)
zip -j9 test.cbplugin libtest.so test.zip
  adding: libtest.so
 (deflated 62%)
  adding: test.zip (deflated 13%)
Process terminated with status 0 (0 minute(s), 1 second(s))
0 error(s), 0 warning(s) (0 minute(s), 1 second(s))
 
-------------- Run: default in test  (compiler: GNU GCC Compiler)---------------

Checking for existence: /home/sakina/Downloads/test/test /libtest.so
Executing: codeblocks  (in /home/sakina/Downloads/test/test /.)
[COLOR=red]Process terminated with status 255 (0 minute(s), 0 second(s))[/COLOR]


I even tried running the debugger it gives:


Building to ensure sources are up-to-date
Selecting target: 
default
Adding source dir: /home/sakina/Downloads/test/test /
Adding source dir: /home/sakina/Downloads/test/test /
Adding file: codeblocks
Changing directory to: "/home/sakina/Downloads/test/test /."
Set variable: LD_LIBRARY_PATH=.:/usr/local/lib:/usr/lib/i386-linux-gnu:/usr/lib/i386-linux-gnu:

[debug]Command-line: /usr/bin/gdb -nx -fullname  -quiet  -args codeblocks
[debug]Working dir : /home/sakina/Downloads/test/test 

Starting debugger: /usr/bin/gdb -nx -fullname  -quiet  -args codeblocks
done

[debug]Reading symbols from /usr/bin/codeblocks...(no debugging symbols found)...done.
[debug](gdb) 
[debug]> set prompt >>>>>>cb_gdb:

Registered new type: wxString
Registered new type: STL String
Registered new type: STL Vector
Setting breakpoints

[debug]>>>>>>cb_gdb:
[debug]> show version

Reading symbols from /usr/bin/codeblocks...(no debugging symbols found)...done.

[debug]GNU gdb (Ubuntu/Linaro 7.4-2012.04-0ubuntu2.1) 7.4-2012.04
[debug]Copyright (C) 2012 Free Software Foundation, Inc.
[debug]License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
[debug]This is free software: you are free to change and redistribute it.
[debug]There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
[debug]and "show warranty" for details.
[debug]This GDB was configured as "i686-linux-gnu".
[debug]For bug reporting instructions, please see:
[debug]<http://bugs.launchpad.net/gdb-linaro/>.
[debug]>>>>>>cb_gdb:
[debug]> set confirm off

Debugger name and version: GNU gdb (Ubuntu/Linaro 7.4-2012.04-0ubuntu2.1) 7.4-2012.04

[debug]>>>>>>cb_gdb:
[debug]> set width 0
[debug]>>>>>>cb_gdb:
[debug]> set height 0
[debug]>>>>>>cb_gdb:
[debug]> set breakpoint pending on
[debug]>>>>>>cb_gdb:
[debug]> set print asm-demangle on
[debug]>>>>>>cb_gdb:
[debug]> set unwindonsignal on
[debug]>>>>>>cb_gdb:
[debug]> set print elements 0
[debug]>>>>>>cb_gdb:
[debug]> set disassembly-flavor intel
[debug]>>>>>>cb_gdb:
[debug]> catch throw
[debug]Catchpoint 1 (throw)
[debug]>>>>>>cb_gdb:
[debug]> source /usr/local/share/codeblocks/scripts/stl-views-1.0.3.gdb
[debug]>>>>>>cb_gdb:
[debug]> directory "/home/sakina/Downloads/test/test /"
[debug]>>>>>>cb_gdb:
[debug]> run
[debug]/usr/bin/codeblocks: symbol lookup error: /usr/bin/codeblocks: undefined symbol: _ZN7Manager7isBatchE
[debug][Inferior 1 (process 4948) exited with code 0177]
[debug]>>>>>>cb_gdb:

[Inferior 1 (process 4948) exited with code 0177]

[debug]> quit

[COLOR=red]**Debugger finished with status 0**[/COLOR]



help....

---

### Post by coldcritter64 on 2014-04-02
See if this next link addresses your problem :  [http://www.unixmen.com/fix-process-terminated-status-255-codeblocks/](http://www.unixmen.com/fix-process-terminated-status-255-codeblocks/)

I just googled part of the error output you posted "Process terminated with status 255", 2nd result down on the google search. 

From the link supplied above,
> **Question**: Any I compile codes in Code::Blocks if get this &#8220;**Process Terminated With Status 255 (0 minutes, 0 seconds)**&#8220;
**Answer: **Code::Blocks displays or outputs your compiled codes with **xterm. **Xterm is not installed.

You may need to check if xterm is installed, according to that link. Good luck.

---

### Post by zinat on 2014-04-02
Sir i had tried this earlier before posting it on forum, but its still giving the same error

---

### Post by steeldriver on 2014-04-02
A couple of things that may be causing issues:

1. your working directory name appears to have a trailing space (*Changing directory to: "/home/sakina/Downloads/test/test /."*). Unless the name is quoted everywhere it may cause errors

2. you appear to be trying to execute a shared library - normally libraries would not be executable, you would need to write a test program that links to the library and calls functions from it

---

