---
title: "Installing Caprice32 emulator in Ubuntu"
date: 2017-08-13
forum: General Help
---

### Post by dalekky on 2017-08-13
I need some help building and installing Caprice32.

It is on Github here - [https://github.com/ColinPitrat/caprice32](https://github.com/ColinPitrat/caprice32)

Where do I start? Step-by-step instructions would be appreciated.

I understand that in order to create a deb package, I need the prerequisite tools listed here [https://github.com/ColinPitrat/caprice32/blob/master/INSTALL.md](https://github.com/ColinPitrat/caprice32/blob/master/INSTALL.md) but I am unsure how to obtain the prerequisites nor how to actually perform the build itself.

So if someone is keen to point out the step by step build instructions, please do so by posting in this thread.

I have got as far as typing into a terminal -

git clone [https://github.com/ColinPitrat/caprice32.git](https://github.com/ColinPitrat/caprice32.git)

What's next?

Thank you.

---

### Post by vocx on 2017-08-13
> **dalekky said:**
> I need some help building and installing Caprice32.

It is on Github here - [https://github.com/ColinPitrat/caprice32](https://github.com/ColinPitrat/caprice32)

Where do I start? Step-by-step instructions would be appreciated.

Asking for a step by step guide to do anything is a bit rude. You cannot expect to be spoon-fed all the time.

If you have a general problem we'll be happy to help you along the way with advice and tips, but you cannot simply say, "help me by doing this for me".

> 
I understand that in order to **create a deb package**, I need the prerequisite tools listed here [https://github.com/ColinPitrat/caprice32/blob/master/INSTALL.md](https://github.com/ColinPitrat/caprice32/blob/master/INSTALL.md) but I am unsure how to obtain the prerequisites nor how to actually perform the build itself.

You are a bit confused if you think a .deb package is necessary. Installing things, and creating a .deb package are two separate things. A .deb package is a way to distribute and share a precompiled program in various machines. That is, although nowadays many pieces of software come in a .deb package, you can always install the software directly by following the instructions of the original developer.

> 
So if someone is keen to point out the step by step build instructions, please do so by posting in this thread.

I have got as far as typing into a terminal -

git clone [https://github.com/ColinPitrat/caprice32.git](https://github.com/ColinPitrat/caprice32.git)

What's next?

Thank you.
Your question is not related to Ubuntu. Your question is about installing a particular piece of software. Therefore, I would suggest you ask the developer of the program itself. This should be the first point of contact. With many free software programs the documentation sometimes is not good enough so asking the developer himself is helpful. You may get a direct answer and even he will realize the installation instructions are not clear so he will take that as a suggestion to improve the documentation.

> 
I understand that in order to create a deb package, I need the prerequisite tools listed here [https://github.com/ColinPitrat/caprice32/blob/master/INSTALL.md](https://github.com/ColinPitrat/caprice32/blob/master/INSTALL.md) but **I am unsure how to obtain the prerequisites** nor how to actually perform the build itself.


**A minimum amount of knowledge of Linux systems is usually assumed** by developers. If you want to install things from source, you need to know a bit more about programming and compiling, otherwise it will be difficult for your to progress.

Whenever you are compiling something, the dependencies usually are in packages ending with "-dev", so if you need a library, say "SDL", you would search for a package named "libsdl-dev" or something similar.
```

aptitude search 'libsdl dev'

```
You can see there are many packages there, you probably need to install the main one, called "libsdl2-dev", which probably will pull other dependencies, also "-dev" packages. And you need to do this as well for "zlib", "libPNG", etc.

But again, you should first ask the developer, or their mailing list, IRC channel, or other medium of contact, before asking the Ubuntu forum users, who may not know that program at all.

---

### Post by dragonfly41 on 2017-08-13
Although I don't have your package installed, on looking at my Ubuntu 16.04 packages using Synaptic Package Manager I would hazard a guess that these dependencies are needed .. only SDL below is not installed for me .. others I see are already installed

**SDL ..**

libsdl2-2.0.0
libsdl2-dev

[B]
FreeType ..[/B]

libfreetype6
libfreetype6-dev

**zLib ..**

zlib1g
zlib1g-dev


**libPNG ..**

libpng12-0
libpng12-dev

---

