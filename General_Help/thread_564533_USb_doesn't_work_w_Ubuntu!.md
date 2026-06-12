---
title: "USb doesn't work w/ Ubuntu!"
date: 2007-10-01
forum: General Help
---

### Post by kris2pe on 2007-10-01
Using my Psp as a usb! 
I doesn't seemed to work in Ubuntu!

---

### Post by strabes on 2007-10-01
I googled "ubuntu psp usb" and here are three of the top results:

[https://help.ubuntu.com/community/PSP](https://help.ubuntu.com/community/PSP)
[http://ubuntuforums.org/showthread.php?t=273578](http://ubuntuforums.org/showthread.php?t=273578)
[http://ubuntuforums.org/showthread.php?t=167264](http://ubuntuforums.org/showthread.php?t=167264)

Please search these forums, the documentation, and google before posting.

---

### Post by kris2pe on 2007-10-01
Problem:
[https://help.ubuntu.com/community/PSP](https://help.ubuntu.com/community/PSP)
Poorly written guide
For example in the guide :
Then you need to compile and install the program:
qmake
In reality when you enter this in the terminal:
kris2pe@kris2pe:~/Desktop/qpspmanager-2.0.2/src$ qmake
Usage: qmake [mode] [options] [files]

   QMake has two modes, one mode for generating project files based on
some heuristics, and the other for generating makefiles. Normally you
shouldn't need to specify a mode, as makefile generation is the default
mode for qmake, but you may use this to test qmake on an existing project

Mode:
        -project       Put qmake into project file generation mode
                       In this mode qmake interprets files as files to
                       be built,
                       defaults to *.c; *.ui; *.y; *.l; *.ts; *.h; *.hpp; *.hh; *.H; *.hxx; *.cpp; *.cc; *.cxx; *.C
        -makefile      Put qmake into makefile generation mode (default)
                       In this mode qmake interprets files as project files to
                       be processed, if skipped qmake will try to find a project
                       file in your current working directory

Warnings Options:
        -Wnone         Turn off all warnings
        -Wall          Turn on all warnings
        -Wparser       Turn on parser warnings
        -Wlogic        Turn on logic warnings

Options:
         * You can place any variable assignment in options and it will be     *
         * processed as if it was in [files]. These assignments will be parsed *
         * before [files].                                                     *
        -o file        Write output to file
        -unix          Run in unix mode
        -win32         Run in win32 mode
        -macx          Run in Mac OS X mode
        -d             Increase debug level
        -t templ       Overrides TEMPLATE as templ
        -tp prefix     Overrides TEMPLATE so that prefix is prefixed into the value
        -help          This help
        -v             Version information
        -after         All variable assignments after this will be
                       parsed after [files]
        -cache file    Use file as cache           [makefile mode only]
        -spec spec     Use spec as QMAKESPEC       [makefile mode only]
        -nocache       Don't use a cache file      [makefile mode only]
        -nodepend      Don't generate dependencies [makefile mode only]
        -nomoc         Don't generate moc targets  [makefile mode only]
        -nopwd         Don't look for files in pwd [ project mode only]
        -norecursive   Don't do a recursive search [ project mode only]

It gives you this meaning the commands are lacking!
I also tried the pspvc guide! Nothing happened can't access on anything on it!

---

