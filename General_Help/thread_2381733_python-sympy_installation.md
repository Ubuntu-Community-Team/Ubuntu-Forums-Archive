---
title: "python-sympy installation"
date: 2018-01-04
forum: General Help
---

### Post by asb3 on 2018-01-04
I'm running octave 4.2.1 on Ubuntu 16.04.  
I want to install the symbolic manipulation library.
I'm running python 2.7.12.
To install sympy I ran
>sudo apt-get install octave liboctave-dev python-sympy

I then ran gnu-octave and typed the following commands at the prompt:


>> pkg install -forge symbolic
>> pkg load symbolic
>> syms x
OctSymPy v2.6.0: this is free software without warranty, see source.
Initializing communication with SymPy using a popen2() pipe.
error: SymPy is installed but is too old (sympy-0.7.6.1 found, 1.0 required)
error: called from
    assert_have_python_and_sympy at line 44 column 7
    python_ipc_popen2 at line 78 column 5
    python_ipc_driver at line 59 column 13
    python_cmd at line 164 column 9
    valid_sym_assumptions at line 38 column 10
    assumptions at line 82 column 7
    syms at line 97 column 13

How do I install a newer version of SymPy?

---

### Post by Xian on 2018-01-04
The version of python-sympy that you need is not available in 16.04.

You'd need to build the package locally and install the correct version.

[img]https://i.imgur.com/yPM4cBJl.png[/img]

---

