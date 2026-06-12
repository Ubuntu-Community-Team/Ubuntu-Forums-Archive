---
title: "Python opengl games problem"
date: 2007-12-24
forum: General Help
---

### Post by the_darkside_986 on 2007-12-24
I am running Gutsy, and everytime I try to play a Python game that uses python opengl bindings, the performance is terrible and renders the game unplayable.

Yes, I have my graphics card driver set up and real openGL games such as Sauerbraten work just fine. But games like Frets on Fire, which I installed from the package manager, are too slow and choppy to play.

Is python and its opengl module implemented *that* badly or is there some kind of shared library path error somewhere?

---

### Post by the_darkside_986 on 2007-12-24
er... I'm not dissing python, I like the language and I am learning it actually, but I can't get python-opengl applications to run fast, but I do want this to work. Maybe it just isn't meant to be, and maybe graphics rendering code will always have to be written in unreadable and unmaintainable low-level languages :(

I could try Psyco, the python J-I-T compiler but the home page claims that the memory footprint of Psyco is large.

---

### Post by the_darkside_986 on 2007-12-24
I have diligently been trying to solve this problem, and I thought that the problem might be that the binary packages were linking statically to libMesaGL instead of nvidia opengl, because that's what it looks like. HOWEVER I cannot find any Makefile or *.so files inside the source code package, the only thing I see is *.py (python) source files.

But really, there has to be a simple linkage or installation problem, because if python-opengl were really like this, then nobody would be trying to write python opengl apps. 

By the way, does there exist anywhere in the universe a PCI-express graphics card that has open source 3D drivers?

---

### Post by lx73 on 2008-01-12
the version of pyopengl that gutsy ships with has known performance problems. Try to downgrade to version 2.

---

### Post by the_darkside_986 on 2008-01-13
oh well  I solved it by using the Frets on Fire tarball package from the official website. It contains its own *.so file of each library it uses.  I hope they fix this issue in Hardy Heron because heavy utilization of shared libraries is one of the many strengths of a typical Linux distro. In Windows, everyone just throws whatever non-win32 library they use into the executable package and it wastes harddrive space and memory. but thanks anyway.

---

