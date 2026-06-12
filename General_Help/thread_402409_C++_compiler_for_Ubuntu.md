---
title: "C++ compiler for Ubuntu"
date: 2007-04-05
forum: General Help
---

### Post by nerdman978 on 2007-04-05
Does anyone know of a good C++ compiler for Ubuntu? I use DevC++ on Windows.

---

### Post by theeru on 2007-04-05
sudo apt-get install g++

That simple.

Now, if you're looking for an IDE, I recommend Eclipse. Otherwise, you can always just use a text editor such as emacs and compile from the shell

---

### Post by jdhore on 2007-04-05
or: sudo apt-get install build-essential

which will install gcc, cpp, c++, g++ and a few other i believe (it's a metapackage)

---

### Post by deadowl on 2007-04-05
Well, I wouldn't recommend Eclipse, especially since the version in the repositories is bugged to the point where I could no longer use it with the C++ plugin. It used to come in handy for when I coded in Java before it broke. Right now, however, on my system it's just one giant memory leak.

I would, however, recommend KDevelop.

---

### Post by WW on 2007-04-05
Lately I've been experiementing with Code::Blocks: [http://www.codeblocks.org/](http://www.codeblocks.org/)

I haven't used it enough to give it an endorsement, but it is probably worth checking out.  You can get the latest version as an Ubuntu package from the Code::Blocks web page.

---

