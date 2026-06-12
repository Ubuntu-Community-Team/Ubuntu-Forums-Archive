---
title: "Building a GCC Cross Compiler"
date: 2016-02-29
forum: General Help
---

### Post by jonathan90 on 2016-02-29
I'm trying to follow the [Bare Bones]("http://wiki.osdev.org/Bare_Bones") tutorial on the OS Dev wiki but I'm confused on how to [build the GCC cross compiler]("http://wiki.osdev.org/GCC_Cross-Compiler"). It says to install the source code for stuff like bintuils, GCC, GNU GMP etc, but most of it is already installed or can be installed from the software center. Do I need to install a second copy? It also said to install into $HOME/opt/cross, but I could only find /opt, and I'm assuming "cross" is a directory I'll have to make. I've never built anything through source code before, only installed from PPAs. I'm afraid to run the commands on the page since I'm not sure what's going on and I don't want to mess up my system. I'm doing this for a class project.

---

### Post by steeldriver on 2016-02-29
Are you sure your class project requires you to *build* the cross compiler? Pre-built cross compilers are available for many target systems

Anyhow, it's unlikely that the *source code* of things like binutils, gcc etc. is installed on your system already - only *binary* packages are installed by default on Ubuntu

You can install source code by enabling source (deb-src) repositories and then using (for example)

```

cd ~/opt/cross
apt-get source binutils

```

however this will download "patched" versions of the code equivalent to the current binary package for your system: you may want to get up-to-date generic versions of the source code (usually as "tarballs") directly from the maintainers' websites instead.
 
Yes you would need to create $HOME/opt/cross if that's where the instructions indicate - in fact that's safer than using /opt since it doesn't require root rights and doesn't risk messing with any of your system files.

---

### Post by jonathan90 on 2016-03-03
So my teacher is providing me with a finished version of the Bare Bones OS to run in virtual box, but in the meantime, I'm still trying to set up the cross compiler. I think the point of all that is to get the GCC to compile C code for the OS I'm building instead of Ubuntu on my own computer. It said that it needs to work for "i686-elf," and when I ran gcc -dumpmachine, it said "x86_64-linux-gnu." So could I copy my existing gcc somehow and just change the target OS?

---

