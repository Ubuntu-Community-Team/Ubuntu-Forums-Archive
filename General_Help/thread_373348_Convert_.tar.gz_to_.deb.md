---
title: "Convert .tar.gz to .deb"
date: 2007-03-01
forum: General Help
---

### Post by dnccnd on 2007-03-01
Hi!

I am having some problems getting Noteedit and Canorus to start. I have read this thread [http://www.ubuntuforums.org/showthread.php?t=204907&highlight=noteedit](http://www.ubuntuforums.org/showthread.php?t=204907&highlight=noteedit) but didn't manage to fix the problem. It seems there are some problems with these music notation programmes.

I found out that the version of Noteedit that can be installed through Synaptic is the 2.8.0 version, but from the homepage of Noteedit I have downloaded the 2.8.1 version which, I thought, might fix my problem. This version is though a .tar.gz file. Can I install it somehow on ubuntu, maybe by converting it to a .deb file? I think I did something similar when I installed Skype.

Thanks for any help!

---

### Post by Maestro23 on 2007-03-01
You are trying to install/compile from source.  You need to use the [COLOR="Red"]tar[/COLOR] command on that file. Read the section at the bottom of the link(Installing from source).

[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

*Note, compiling from souce is not recommended if you are new to linux.

Good luck.

---

### Post by dnccnd on 2007-03-01
Thanks Maestro23!

I am having some problems though. In the page you gave me these are the instructions:

1. Download the source code (to ~/src), usually in archive format (.tar, .tar.gz, .tgz, .tar.bz, etc).
2. Extract the code from the archive.
    * Use the above modification to ~.bashrc or Archive manager.
3. cd into the extracted directory.
4. Compile and install: 

Code:

./configrue
make
sudo checkinstall

First, I guess that the right command is ./configure. And up to here everything works. Then when I type "make" I get this error:

make: *** No targets specified and no makefile found. Stop.

Should I specify a target? Which one? Is this the right command?

Thanks for your help!

---

### Post by taurus on 2007-03-01
Was there any error message when you ran ./configure?  What's the output of this command in the directory where you want to build it from source?

```
ls -la
```
Also, you should look at either INSTALL or README for further info on how to build it.

---

