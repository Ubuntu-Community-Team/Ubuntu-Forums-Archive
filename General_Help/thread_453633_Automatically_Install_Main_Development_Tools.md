---
title: "Automatically Install Main Development Tools"
date: 2007-05-24
forum: General Help
---

### Post by Millenniumman on 2007-05-24
I like Ubuntu a lot better than RedHat/CentOS in most ways, but I really liked the "everything" install option available on CentOS. Doing that, there was almost nothing I needed to add. Ubuntu, on the other hand, is initially missing a lot.

Is there any "one-click" (i.e., not hunting down every package as I need it) method to get the equivalent of RedHat's everything install? 

Failing that, is there any such way to get all of the basic dev tools and libraries for c/c++/X11/motif .

---

### Post by vigleik on 2007-05-24
I would like this too. One meta-package that depends on all the development tools one is likely to need. And I'm talking much more than jus build-essential. Does this exist? It shouldn't be hard to make.

---

### Post by onbongos on 2007-05-24
what is the answer to "all the development tools one is likely to need"? if you need something you're unlikely to have needed how do you install it? it's not hard

---

### Post by threadmetal on 2007-05-24
"All the development tools one is likely to need" is too vague to package, even if you specify a programming language. If what you truly want is everything and its mother, including the kitchen sink and garden gnomes, then you're looking for a bloatware distribution, a market Ubuntu does not usually attempt to satisfy.

On the other hand, for your "failing that" request, I find "sudo apt-get install g++" gets me started quite nicely.

I'm not sure of the package names for the X11 and motif libs, but they aren't hard to find: if you can't find them using google, use synaptic (see <rant> below).

Never mind, thought I'd be kind and do the research for you:
"sudo apt-get install xorg-dev"
"sudo apt-get install libmotif-dev"

Using synaptic:

<rant>
As for "one-click" -- a lot of people complain that linux is difficult because we insist on using the command line.. I'm sorry.. When you know (or can easily find) the package name, I find the one-step answers above to be simpler than:

1) Click System->Administration->Synaptic Package Manager
2) Click Search, enter "((name or keyword of package))"
2a) ... here's hoping you used good search terms and found specific and correct results ...
3) Right-click the appropriate search result 
4) Select "Mark for Installation"
4a) Give consent for any dependencies to be satisfied
5) Click "Apply"

If you already know the package name, I don't really see how the pretty buttons and scrollbars make this task easier. Even if you don't know the name, you can usually find it with google --  faster than using synaptic, if your browser is already open.
</rant>

---

### Post by Millenniumman on 2007-05-24
I don't mind if it is a third party thing. 

I'll attempt to clarify what I meant: all of gcc, gdb, glibc, make/autoconf, bison/lex, python, perl, tcl, php, ruby, emacs, vim, and a few things I probably forgot. In addition to that, the libraries with development packages for all of the main gui toolkits, or at least the ones already on your system (in that case, just the development packages). 

An example which isn't as "bloated" as CentOS is the non OS X specific tools in the development tools for Mac OS X. They're pretty comprehensive without being huge.

I did not necessarily mean "one-click" as gui thing. What I meant was a simple one "thing" solution.  Not hunting down needed packages as they are needed.


> "sudo apt-get install xorg-dev"
"sudo apt-get install libmotif-dev"
I'm pretty sure that won't work. The libmotif-dev package is missing something necessary (it might be libxp, it is definitely party of lesstif). Now, that's not a huge problem to fix, and maybe I expect too much, but it seems that "sudo apt-get install guidevlibs" would be a lot better.

---

### Post by takeawaydave on 2007-05-26
.

---

### Post by takeawaydave on 2007-05-26
.

---

### Post by cmnorton on 2007-09-22
[QUOTE=threadmetal;2714605]

...
On the other hand, for your "failing that" request, I find "sudo apt-get install g++" gets me started quite nicely.

...

Is libncurses considered part of installing g++, or is it separate?

Does your sudo-apt-get install g++ include "essential" development tools?

Thanks.

---

### Post by nick_h on 2007-09-22
or even:
```
sudo apt-get install build-essential
```
which should give you gcc, gdb, glibc, make/autoconf, bison
I think phython and perl are probably installed by default.
vim and emacs have packages of the same name.

---

