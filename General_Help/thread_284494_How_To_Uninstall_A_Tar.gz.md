---
title: "How To Uninstall A Tar.gz?"
date: 2006-10-25
forum: General Help
---

### Post by nikolaos on 2006-10-25
How can i uninstall a package i build from source (tar.gz)?
I tried to make unnsitall but it says that uninstall is not in the tree.
What sould i do?

---

### Post by bsussman on 2006-10-25
It like totally depends on what was in the original and how it built and installed itself.

Please provide the name of the package, and some details like where you got it so we might have a chance to help.

---

### Post by cwaldbieser on 2006-10-25
> **nikolaos said:**
> How can i uninstall a package i build from source (tar.gz)?
I tried to make unnsitall but it says that uninstall is not in the tree.
What sould i do?

Get the checkinstall package.  Build the package from source again, but instead of doing the "make install" step, do
```

$ sudo checkinstall -D 

```
Answer the prompts, and it will create and install a .deb package for you.  Now just uninstall the package with apt-get or synaptic.

It's a good idea to install source packages with checkinstall because it makes removing the package later easy.

---

### Post by bsussman on 2006-10-25
> **cwaldbieser said:**
> Get the checkinstall package.

That is a very cute solution.

First new thing I have learned about linux package building in a while!

---

### Post by ~LoKe on 2006-10-25
Or, enter the directory in which the program was compiled and type **make clean**.

---

### Post by bsussman on 2006-10-25
By convention, make clean only resets the source directories to their original state.  It does not uninstall anything.

---

### Post by nikolaos on 2006-10-25
thanks for all the info guys. And true make clean didn't uninstall anything. Is there another way except the synaptic one? (though it is just what i need)

---

### Post by bsussman on 2006-10-25
> **nikolaos said:**
> thanks for all the info guys. And true make clean didn't uninstall anything. Is there another way except the synaptic one? (though it is just what i need)

Sure - go through the makefile.  Identify the install target and see what it copies, to what locations and what scripts it runs.  Then reverse the process manually.

Frankly, letting checkinstall/synaptic do it is the way I would lean...

---

### Post by thephotoman on 2006-10-25
The easiest way is to cd into the directory where you put the compiled sources for the program and type sudo make uninstall at the terminal--if you didn't use checkinstall (which I don't always do).

If you did use checkinstall, just remove it like any other program: sudo apt-get remove *insert program name here*

---

### Post by pspotts on 2006-10-25
If you still have the tarry geezer's directory on your system, cd into it from a terminal and at a prompt do a sudo make uninstall. (As opposed to the "make install" you used at the end of the compile process to install the program). This should remove everything associated with the program...

---

### Post by nikolaos on 2006-10-26
i have the tar.gz directory but i can't cd into it. cd binutils-2.17.tar.gz doesn't work

---

