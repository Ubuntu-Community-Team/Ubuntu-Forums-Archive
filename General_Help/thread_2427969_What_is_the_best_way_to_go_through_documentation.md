---
title: "What is the best way to go through documentation?"
date: 2019-09-27
forum: General Help
---

### Post by lengthofdepth on 2019-09-27
I recently had to install freeglut3, while the official website does have have documentation with regard to the library, it doesn't specify how to compile (g++ linking).

I had to google search for an answer, but how could I have figured out that the libraries I needed to link (lGL, lGLU, lglut) through documentation?

Is the logic as follows:

1) Install library (All libraries installed in some location?)
2) Look for files pertaining to the library downloaded?
3) Link the files

---

### Post by Skaperen on 2019-09-27
what you are saying is that without google the documentation in its current form is not complete?

---

### Post by lengthofdepth on 2019-09-27
> **Skaperen said:**
> what you are saying is that without google the documentation in its current form is not complete?

No not necessarily, I'm relatively new to this and would just like to understand in general, how to go about learning to use certain aspects of command line. I gave that as an example because it was something I was struggling with.

---

### Post by Skaperen on 2019-09-28
the best way to learn something new is to find a tutorial.  written ones can be in plain text, html, and pdf form.  a few are in chm and other formats.  there are lots of video tutorials on just about every subject on youtube.  i'm sure there are audio ones, too.  once you read/watch/hear the tutorial a couple times, go try it yourself.  if it's something you can do many times, do that.

---

### Post by mc4man on 2019-09-28
> **lengthofdepth said:**
> I recently had to install freeglut3, while the official website does have have documentation with regard to the library, it doesn't specify how to compile (g++ linking).

I had to google search for an answer, but how could I have figured out that the libraries I needed to link (lGL, lGLU, lglut) through documentation?

At the risk of misunderstanding you, in the  freeglut3 source there is a file named README.cmake
Read it.

---

### Post by Artim on 2019-09-28
How did you install freeglut3?  It's in the Ubuntu repositories already, and there's no need to compile it.  Apt usually handles all the dependency issues automagically.

```

sudo apt-get install freeglut3

```

---

### Post by lengthofdepth on 2019-09-29
> **Artim said:**
> How did you install freeglut3?  It's in the Ubuntu repositories already, and there's no need to compile it.  Apt usually handles all the dependency issues automagically.

```

sudo apt-get install freeglut3

```

There was no problem installing it, I just wasn't sure how to compile programs written using it. I had to Google how to compile it, but was wondering where I could find documentation about compiling it without googling.

---

### Post by CatKiller on 2019-09-29
> **lengthofdepth said:**
> There was no problem installing it, I just wasn't sure how to compile programs written using it.

As a general rule, if you want to include a library in programs you're compiling yourself, you will also need the header files for that library. For Ubuntu, those are generally separate -dev packages; in this case it would be **freeglut3-dev**. For simply using the library with pre-compiled binaries, those header files are unnecessary, so they are not installed by default.

---

### Post by TheFu on 2019-09-29
Most end-users on Ubuntu don't need to compile anything. If you do, there is probably an easier solution.  If you want to learn to be a programmer with a compiled language, that's very different than just learning to use the shell.  Be certain you fully understand the different between ../ and /etc/ and ~/ and ~/bin/  and ~root/  relative and absolute paths are important.

If you want to learn to use the shell/CLI/Terminal efficiently, then learning things in a specific order is recommended since every skill is built on prior skills.  Starting from the beginning and working through a reputable command line book, in order, is the most efficient.  When you are new, googled answers are dangerous.  As a LUG organizer and former Linux teacher, I'm asked all the time, how to learn Linux. I wrote an article about how to achieve it: [https://blog.jdpfu.com/2014/12/28/learning-linux](https://blog.jdpfu.com/2014/12/28/learning-linux)
Some other links: [https://blog.jdpfu.com/2017/09/12/linux-command-line-or-shell-resources](https://blog.jdpfu.com/2017/09/12/linux-command-line-or-shell-resources)

At my LUG, a number of people have worked through the first 250 pages of TLCL - that's a book - which gets them a basic background so we can discuss more intermediate things.  When they get that far, I send them here: [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)  Why wait?  Because they don't have the background in the beginning.  A few weeks of doing things the hard way will make learning the shell tricks be understood and "stick" better.

Learning Unix/Linux command lines is like learning a new language.  Just like a new language, it takes a few hours every day and about 6 months. 

And until the basic shell stuff is mastered, doing the compiler stuff seems like black magic, when it really isn't all that hard.  As for 1-way to compile things, I have bad news.  That doesn't exist.  There are about 5 major ways for a C/C++ program to be compiled, but their are 20 sometimes used ways beyond those 5.  It comes down to reading the documentation provided with the project website and project files to figure it out.

Sorry, ran out of time to proofread this. Hope it isn't too jumbled.

---

### Post by lengthofdepth on 2019-09-30
> **Artim said:**
> How did you install freeglut3?  It's in the Ubuntu repositories already, and there's no need to compile it.  Apt usually handles all the dependency issues automagically.

```

sudo apt-get install freeglut3

```

I was referring to compiling my own programs.

How does one know to compile with these flags (-lfreeglut -lglu32 -lopengl32), where do I get such info without googling?

g++ main.cpp -o main -lfreeglut -lglu32 -lopengl32

---

### Post by lengthofdepth on 2019-09-30
> **TheFu said:**
> Most end-users on Ubuntu don't need to compile anything. If you do, there is probably an easier solution.  If you want to learn to be a programmer with a compiled language, that's very different than just learning to use the shell.  Be certain you fully understand the different between ../ and /etc/ and ~/ and ~/bin/  and ~root/  relative and absolute paths are important.

If you want to learn to use the shell/CLI/Terminal efficiently, then learning things in a specific order is recommended since every skill is built on prior skills.  Starting from the beginning and working through a reputable command line book, in order, is the most efficient.  When you are new, googled answers are dangerous.  As a LUG organizer and former Linux teacher, I'm asked all the time, how to learn Linux. I wrote an article about how to achieve it: [https://blog.jdpfu.com/2014/12/28/learning-linux](https://blog.jdpfu.com/2014/12/28/learning-linux)
Some other links: [https://blog.jdpfu.com/2017/09/12/linux-command-line-or-shell-resources](https://blog.jdpfu.com/2017/09/12/linux-command-line-or-shell-resources)

At my LUG, a number of people have worked through the first 250 pages of TLCL - that's a book - which gets them a basic background so we can discuss more intermediate things.  When they get that far, I send them here: [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line)  Why wait?  Because they don't have the background in the beginning.  A few weeks of doing things the hard way will make learning the shell tricks be understood and "stick" better.

Learning Unix/Linux command lines is like learning a new language.  Just like a new language, it takes a few hours every day and about 6 months. 

And until the basic shell stuff is mastered, doing the compiler stuff seems like black magic, when it really isn't all that hard.  As for 1-way to compile things, I have bad news.  That doesn't exist.  There are about 5 major ways for a C/C++ program to be compiled, but their are 20 sometimes used ways beyond those 5.  It comes down to reading the documentation provided with the project website and project files to figure it out.

Sorry, ran out of time to proofread this. Hope it isn't too jumbled.

Thank you for the detailed response, I am familiar with the basics of Linux commands, but I was referring to compiling my own programs, and not understanding what flags to use with the g++ or gcc compiler, man gcc/g++ doesn't help with external libraries like freeglut. While I was reading the documentation of freeglut, I didn't find anything about what flags to use. So I was wondering how I would go about finding that information, methodically rather than googling it.

---

### Post by TheFu on 2019-09-30
> **lengthofdepth said:**
> Thank you for the detailed response, I am familiar with the basics of Linux commands, but I was referring to compiling my own programs, and not understanding what flags to use with the g++ or gcc compiler, man gcc/g++ doesn't help with external libraries like freeglut. While I was reading the documentation of freeglut, I didn't find anything about what flags to use. So I was wondering how I would go about finding that information, methodically rather than googling it.

You'd need to find the build method for the library, if the documentation doesn't specify the specific options.  But 
```
g++ main.cpp -o main -lfreeglut -lglu32 -lopengl32 
```
isn't using any special options. That line just compiles 1 file and links that file with 3 non-default libraries which would need to be in *standard locations* to be found.  The standard locations can be configured in a few different ways, usually the LD_LIBRARY_PATH would control the order of the directory search.

-lfreeglut really means look for a file named libfreeglut.so or libfreeglut.a somewhere in the directories in the LD_LIBRARY_PATH.  It is extremely common for a link statement to specify other library paths using a -L option.  I would always have -L ../lib on my link line, so my libraries would be used before any system-installed libraries.  Also, libc is automatically included by every C compiler I've ever used on any platform.  libstdc++ is not - or at least it wasn't many years ago when my projects were switching over to using the STL.

Any C or C++ programmer should understand these things, though Windows-only programmers might not. Every other platform works in a similar way with pretty much any C or C++ compiler.  These options are not specific to gcc or g++.

-g or -ggdb or -Wall or any architecture specific compile/link options are also common.  Any competent C/C++ programmer should know these options too.

IMHO.

But really, if a program/library is supposed to be compiled by end users, then it should have a Makefile, use automake, or autoconf to build the project so very little C-specific knowledge is needed.

---

### Post by TheFu on 2019-09-30
Which libraries should you include?  That depends on which methods/functions you are calling.  When you determine which functions/methods to be used, you'll need a header file and you'll need to look for which library that header file is connected with.

Someone else was asking when did apache need to be configured to use php.  My answer was, if you want your website to use php and wrote php code, then you should configure apache with php.  If you don't write any php, then you don't need php configured in apache.  
The same answer applies for this. When you use a specific function that is outside the core libc functions, you'll know it. If you don't, that's a failure to understand.  It is possible to use some tools to see which files and functions and methods are inside any library on a system.  nm and ar come to mind, but the library should have 1 or more header files, so if you use any functions/methods from a header, then the library for that header should be linked.

---

### Post by lengthofdepth on 2019-09-30
> **TheFu said:**
> You'd need to find the build method for the library, if the documentation doesn't specify the specific options.  But 
```
g++ main.cpp -o main -lfreeglut -lglu32 -lopengl32 
```
isn't using any special options. That line just compiles 1 file and links that file with 3 non-default libraries which would need to be in *standard locations* to be found.  The standard locations can be configured in a few different ways, usually the LD_LIBRARY_PATH would control the order of the directory search.

-lfreeglut really means look for a file named libfreeglut.so or libfreeglut.a somewhere in the directories in the LD_LIBRARY_PATH.  It is extremely common for a link statement to specify other library paths using a -L option.  I would always have -L ../lib on my link line, so my libraries would be used before any system-installed libraries.  Also, libc is automatically included by every C compiler I've ever used on any platform.  libstdc++ is not - or at least it wasn't many years ago when my projects were switching over to using the STL.

Any C or C++ programmer should understand these things, though Windows-only programmers might not. Every other platform works in a similar way with pretty much any C or C++ compiler.  These options are not specific to gcc or g++.

-g or -ggdb or -Wall or any architecture specific compile/link options are also common.  Any competent C/C++ programmer should know these options too.

IMHO.

But really, if a program/library is supposed to be compiled by end users, then it should have a Makefile, use automake, or autoconf to build the project so very little C-specific knowledge is needed.

> **TheFu said:**
> Which libraries should you include?  That depends on which methods/functions you are calling.  When you determine which functions/methods to be used, you'll need a header file and you'll need to look for which library that header file is connected with.

Someone else was asking when did apache need to be configured to use php.  My answer was, if you want your website to use php and wrote php code, then you should configure apache with php.  If you don't write any php, then you don't need php configured in apache.  
The same answer applies for this. When you use a specific function that is outside the core libc functions, you'll know it. If you don't, that's a failure to understand.  It is possible to use some tools to see which files and functions and methods are inside any library on a system.  nm and ar come to mind, but the library should have 1 or more header files, so if you use any functions/methods from a header, then the library for that header should be linked.

Great, thank you for the detailed response, it clarified it for me.

---

