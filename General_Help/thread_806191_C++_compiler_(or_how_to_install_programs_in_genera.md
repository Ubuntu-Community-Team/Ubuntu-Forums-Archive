---
title: "C++ compiler (or how to install programs in general)"
date: 2008-05-24
forum: General Help
---

### Post by TheVirtualMember on 2008-05-24
Hey,

So I'm really new at Ubuntu (just got it today). and I wanted to know if anyone knew a good C++ compiler? More importantly, how would I go about installing it?

Gratias

---

### Post by Steve413z on 2008-05-24
```
sudo apt-get install build-essential
```"build-essential" package has a C compiler in it, and most of the libraries you will need

however the easiest way to install most programs in ubuntu is to just use the ubuntu repositories, most programs you need are included in the repositories.

(for example, the package "build-essential" is in the repository and can be installed with just one command)

---

### Post by amingv on 2008-05-24
Compiler for C++? Here:
```
sudo apt-get install build-essential
```

How to istall stuff? Here:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by ibuclaw on 2008-05-24
Also... If you don't mind me adding...

[LIST]
[*]Q1) My favoured C++ compiler is g++
[/LIST]
[LIST]
[*]Q2) To install it, open a terminal.
Type in:
```
sudo apt-get install g++
```
[/LIST]

And if you are looking for a top-notch IDE.

My favoured apps are:
[LIST]
[*]emacs ```
sudo apt-get install emacs22-nox
```
[/LIST]
[LIST]
[*][Code::Blocks]("http://www.codeblocks.org/") (Get deb files from site to install).
[/LIST]

Regards
Iain

---

### Post by TheVirtualMember on 2008-05-24
Um,when I execute this
```
sudo apt-get install build-essential
```

It doesn't work. I'm guessing I need to download something first?

---

### Post by Steve413z on 2008-05-24
> **TheVirtualMember said:**
> Um, where exactly would I execute that code?

And what are the repositories?


in the terminal'

Applications > Accessories > Terminal

however it's probably easier for you to use the add/remove software utility, under applications

---

### Post by amingv on 2008-05-24
> **TheVirtualMember said:**
> Um, where exactly would I execute that code?

And what are the repositories?

Also, the link I provided has a throughout explanation of it (and graphic methods to do it, if you prefer them).

---

### Post by Steve413z on 2008-05-24
> **TheVirtualMember said:**
> Um, where exactly would I execute that code?

And what are the repositories?


repositories are servers that have pre-made software packages for ubuntu on them.

Ubuntu has more than 24,000 software packages available, in the repositories installed by default. 

what program are you trying to install?

---

### Post by mali2297 on 2008-05-24
Check out the *Programming Talk* section, this  [thread]("http://ubuntuforums.org/showthread.php?t=689635") might interest you.

---

### Post by ByteJuggler on 2008-05-24
> **TheVirtualMember said:**
> Um,when I execute this
```
sudo apt-get install build-essential
```

It doesn't work. I'm guessing I need to download something first?

"It doesn't work" is not helpful.  What exactly happens and what error messages are you getting?  The instructions you've been given should work, that's why people suggested them.  You should not need to download anything manually, that's the whole point of that command, which will install all the "build-essential"s for you.

Let me reiterate the instructions in more detail:

1.) Open a terminal window, to do this click "Applcations"->"Accessorties"->"Terminal".  A black on white text mode termnal window pops up.

2.) Into the window type the command:
```
sudo apt-get install build-essential
```

The system asks for your password to confirm you really want to perform the installation.  The system downloads and installs a bunch of stuff, including the GNU C and C++ compilers.

That's it. You now have the basic command line driver C and C++ compilers installed.  If you want a graphical UI, then that needs to be installed separately.  There are several options.

If these instructions don't work for you, then post where it fails, and with what message and we'll try to help you.

---

### Post by TheVirtualMember on 2008-05-24
It said that it couldn't find build-essential. I tried

sudo apt-get update

and then

sudo apt-get install build-essential, and that worked.


I would prefer a GUI, what are the several options you mentioned?

---

### Post by Steve413z on 2008-05-24
theres two GUI's for package management

the easier one is ```
Applications > Add/Remove
```
the more advanced one is called synaptic
```
System > Administration > Synaptic Package Manager
```

---

### Post by TheVirtualMember on 2008-05-24
Um, I thought he meant GUI C++ code editors/compilers...

---

### Post by mali2297 on 2008-05-25
> **TheVirtualMember said:**
> I would prefer a GUI, what are the several options you mentioned?

Anjuta, Eclipse, Geany, KDevelop,...

---

### Post by Kamron on 2010-01-09
> **ByteJuggler said:**
> "It doesn't work" is not helpful.  What exactly happens and what error messages are you getting?  The instructions you've been given should work, that's why people suggested them.  You should not need to download anything manually, that's the whole point of that command, which will install all the "build-essential"s for you.

Let me reiterate the instructions in more detail:

1.) Open a terminal window, to do this click "Applcations"->"Accessorties"->"Terminal".  A black on white text mode termnal window pops up.

2.) Into the window type the command:
```
sudo apt-get install build-essential
```

The system asks for your password to confirm you really want to perform the installation.  The system downloads and installs a bunch of stuff, including the GNU C and C++ compilers.

That's it. You now have the basic command line driver C and C++ compilers installed.  If you want a graphical UI, then that needs to be installed separately.  There are several options.

If these instructions don't work for you, then post where it fails, and with what message and we'll try to help you.

Remember, you have to be connected to the net for sudo apt-get to work

---

