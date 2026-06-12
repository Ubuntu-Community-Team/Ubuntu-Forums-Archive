---
title: "Cpp Failed sanity test?"
date: 2007-01-20
forum: General Help
---

### Post by zerofool2005 on 2007-01-20
Im kinda new at compiling programs on Linux but when i try to compile gDesklets 0.35.3 I get this error

```
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

```
Has my computer gone mad?

---

### Post by Jasper84 on 2007-01-20
I probably cant answer this question myself, but more info is probably handy. What command did you use to start compiling? Does the gcc, g++ command at itself work? (on simple things like hello world.) (how much do you already know about programming?)
gcc g++ are C and C++ compilers, use sudo aptitude show `name` to see if they are installed. Then you could try (re)install them.  (sudo aptitude reinstall, sudo aptitude install or same with apt-get)

---

### Post by mcduck on 2007-01-20
Have you installed the 'build-essential'-package? Run 'sudo apt-get install build-essential', or use Synaptic to install it.

---

### Post by Pontiac on 2007-03-11
I scoured the net trying to find the solution to that exact same problem with the sanity check.  I ran the apt-get and now the install got further than before.

I'm gonna have to keep a notepad with these tricks. ;)

---

### Post by DuffyD on 2007-05-19
> **mcduck said:**
> Have you installed the 'build-essential'-package? Run 'sudo apt-get install build-essential', or use Synaptic to install it.

McDuck, you are the MAN!!!!  Why doesn't that get installed when you do the install?  Sheesh.

I was having the same issue with Audacity 1.3.3 (the 1.2.6 Ubuntu build is not built right as it's
missing several widgets) and that seems to have fixed it!

Thanks again!

---

### Post by RedSquirrel on 2007-05-20
> **DuffyD said:**
> Why doesn't that get installed when you do the install?  Sheesh.

That's how Ubuntu keeps the installation down to one CD--they don't install a bunch of stuff that most users won't want (compilers, development libraries, etc.). For those of us who do want those things, obtaining them is trivial. ;)

If you do a search on ubuntuforums, you'll find that questions about errors when compiling have been asked and answered quite a few times. 99.9% of the time, it's a simple matter of installing build-essential.

---

