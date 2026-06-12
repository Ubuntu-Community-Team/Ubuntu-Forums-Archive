---
title: "How to use packages"
date: 2007-10-19
forum: General Help
---

### Post by Jordanwb on 2007-10-19
I'm pretty new to Linux itself. So my question is pretty simple: Are packages the Linux version of a Windows Installer?

---

### Post by Shiva88 on 2007-10-19
In a very general sense, yes.  As a technical matter, I suppose, they're different, but from a practical end-user point of view, they're basically the same thing.  They're both a means of installing new software.

A package is basically the program you're installing, along with a list of the other software that program needs to have available in order to run (which are called dependencies).  When you install a package, your computer installs all of the dependencies, as well as the main program itself.   

I'm only a few steps removed from newbism myself, so that may not be entirely accurate, but it's generally true.  I'm sure someone with more knowledge than I will be along shortly to correct me if I'm wrong :)

---

### Post by Jordanwb on 2007-10-19
All right thanks.

---

### Post by kolinab on 2007-10-19
Jordanwb,

There's lots of different ways to install software in Ubuntu. Usually I use the graphical package manager you're describing. There's also the Add/Remove dialog in the system menu. But don't forget the command line - it's easy too and very useful. Check this page for a primer on how that works:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Most of the time I like using the 'synaptic package manager' because I can search for words in the descriptions of the packages. I don't know how to do that from the command line although I'd bet money that it's possible!

K

[edit] 

also I just found this old link someplace, it's maybe a little old but i don't think it's too out of date . . .

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Shiva88 on 2007-10-23
> **kolinab said:**
> Jordanwb,

Most of the time I like using the 'synaptic package manager' because I can search for words in the descriptions of the packages. I don't know how to do that from the command line although I'd bet money that it's possible!




I'm pretty sure that sudo apt-cache search SEARCHSTRING will search the package descriptions too.

Not quite as nice as the functionality provided by synaptic, but if you just need to search in order to find the proper package name for a given piece of software it can be helpful.  The biggest problem with it is that it often returns a long list of packages, which require you to pipe the output through less or grep in order to find what you're looking for.

There's probably a better solution yet that I'm just not aware of.... perhaps someone else can enlighten us? :)

---

