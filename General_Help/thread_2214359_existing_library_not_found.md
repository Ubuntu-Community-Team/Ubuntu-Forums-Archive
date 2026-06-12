---
title: "existing library not found"
date: 2014-03-31
forum: General Help
---

### Post by c3udio on 2014-03-31
Hi everyone!
I have the following problem and don't know how to fix it.
I needed to install a platform and when I tried to set additional options in order to visualise the output with openGL, running "make", I obtained the following error message (after some successfully built targets):

Linking CXX shared library ../../../outputs/library/Linux-g++/libG4OpenGL.so
/usr/bin/ld: cannot find -lX11_Xmu_LIBRARY
collect2: ld returned 1 exit status

However I'm pretty sure that all the library and packages are already installed (I checked it several times). I tried to create a symbolic link, typing something like this:

 sudo ln -s /usr/lib/lX11_Xmu_LIBRARY.so /usr/lib/lX11_Xmu_LIBRARY.so

But it doesn't work anyway...


Could anyone help me?

Thanks,
Chad

---

### Post by steeldriver on 2014-03-31
Hello and welcome to the forums

The name 'X11_Xmu_LIBRARY' doesn't look like a real library name - it looks like a placeholder or variable name that has not been correctly assigned / expanded by the configure or make process, perhaps because the actual library wasn't found.

You could try making sure that the **libxmu-dev** package is installed and then re-running the configuration step. If you want more help it would be a good idea to post the details of the thing you're trying to compile (where you obtained it, how you configured the build etc.)

---

