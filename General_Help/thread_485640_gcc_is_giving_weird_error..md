---
title: "gcc is giving weird error."
date: 2007-06-27
forum: General Help
---

### Post by applegrew on 2007-06-27
When I am trying to compile a .cpp (C++) program using gcc I get the error
```
/tmp/cc4XWPWf.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```

while the same program compiles successfully without even a warning when g++ is used.:shock:

---

### Post by Ragazzo on 2007-06-27
gcc is for compiling C programs and g++ is for C++ programs. The .cpp file extension is used for C++ source code files.

---

### Post by applegrew on 2007-06-27
> **Ragazzo said:**
> gcc is for compiling C programs and g++ is for C++ programs. The .cpp file extension is used for C++ source code files.
As far as I know. gcc is now can be used as starting point for compiling programs in any language GCC supports. I have cygwin installed on my Windows box. I can use gcc and g++ there inerchangeably to compile c++ programs.

Infact when I tried compiling my this cpp program and I didn't have g++ installed then (only gcc was installed) then I got the error
```

gcc: error trying to exec 'cc1plus': execvp: No such file or directory

```

---

### Post by Ragazzo on 2007-06-27
> **applegrew said:**
> As far as I know. gcc is now can be used as starting point for compiling programs in any language GCC supports. I have cygwin installed on my Windows box. I can use gcc and g++ there inerchangeably to compile c++ programs.

Infact when I tried compiling my this cpp program and I didn't have g++ installed then (only gcc was installed) then I got the error
```

gcc: error trying to exec 'cc1plus': execvp: No such file or directory

```

You're right  that gcc recognizes .cpp files but it doesn't link it with the correct libraries.  From the man page:
```

       C++ source files conventionally use one of the suffixes .C, .cc, .cpp,
       .CPP, .c++, .cp, or .cxx; C++ header files often use .hh or .H; and
       preprocessed C++ files use the suffix .ii.  GCC recognizes files with
       these names and compiles them as C++ programs even if you call the com&#8208;
       piler the same way as for compiling C programs (usually with the name
       gcc).

       However, C++ programs often require class libraries as well as a com&#8208;
       piler that understands the C++ language---and under some circumstances,
       you might want to compile programs or header files from standard input,
       or otherwise without a suffix that flags them as C++ programs.  You
       might also like to precompile a C header file with a .h extension to be
       used in C++ compilations.  g++ is a program that calls GCC with the
       default language set to C++, and automatically specifies linking
       against the C++ library.  On many systems, g++ is also installed with
       the name c++.

```

---

### Post by applegrew on 2007-06-27
k. Thanks. :)

---

### Post by Qu4k3R on 2007-06-28
applegrew:
Have you solved it?

---

