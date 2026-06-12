---
title: "How to add an variable to the PATH?"
date: 2007-05-31
forum: General Help
---

### Post by fcastillo on 2007-05-31
I'm a newbie in Ubuntu, and i was wondering how could i add a variable to my path? I just have a problem that i need to run from anywhere, please help me

---

### Post by taurus on 2007-05-31
Edit ~/.bashrc

Applications -> Accessories -> Terminal
```
gedit ~/.bashrc
```
and add these two lines to it.

```
PATH=$PATH:/new_path:/even_newer_path
export PATH
```
Then, either log out and back it or rehash it with

```
source ~/.bashrc
```

---

### Post by fcastillo on 2007-05-31
can i add those lines anywhere in the file? or do they have to be in a specific position. And can i add other variables like that too, not only the PATH ones?
And how can i see what variables do i have running?

---

### Post by taurus on 2007-05-31
I usually add those two lines to the end of it.  

And what are the other variables do you have in mind?  Can you give an example what you intend to do?

---

### Post by fcastillo on 2007-05-31
This is want the program i installed told me to do:

```

Please put /opt/ns-allinone-2.31/bin:/opt/ns-allinone-2.31/tcl8.4.14/unix:/opt/ns-allinone-2.31/tk8.4.14/unix
into your PATH environment; so that you'll be able to run itm/tclsh/wish/xgraph.


IMPORTANT NOTICES:

(1) You MUST put /opt/ns-allinone-2.31/otcl-1.13, /opt/ns-allinone-2.31/lib, 
    into your LD_LIBRARY_PATH environment variable.
    If it complains about X libraries, add path to your X libraries 
    into LD_LIBRARY_PATH.
    If you are using csh, you can set it like:
                setenv LD_LIBRARY_PATH <paths>
    If you are using sh, you can set it like:
                export LD_LIBRARY_PATH=<paths>

(2) You MUST put /opt/ns-allinone-2.31/tcl8.4.14/library into your TCL_LIBRARY environmental
    variable. Otherwise ns/nam will complain during startup.

```

---

### Post by taurus on 2007-05-31
> **fcastillo said:**
> This is want the program i installed told me to do:

```

Please put /opt/ns-allinone-2.31/bin:/opt/ns-allinone-2.31/tcl8.4.14/unix:/opt/ns-allinone-2.31/tk8.4.14/unix
into your PATH environment; so that you'll be able to run itm/tclsh/wish/xgraph.


IMPORTANT NOTICES:

(1) You MUST put /opt/ns-allinone-2.31/otcl-1.13, /opt/ns-allinone-2.31/lib, 
    into your LD_LIBRARY_PATH environment variable.
    If it complains about X libraries, add path to your X libraries 
    into LD_LIBRARY_PATH.
    If you are using csh, you can set it like:
                setenv LD_LIBRARY_PATH <paths>
    If you are using sh, you can set it like:
                export LD_LIBRARY_PATH=<paths>

(2) You MUST put /opt/ns-allinone-2.31/tcl8.4.14/library into your TCL_LIBRARY environmental
    variable. Otherwise ns/nam will complain during startup.

```

You need to add these lines to your ~/.bashrc.

```

PATH=$PATH:/opt/ns-allinone-2.31/bin:/opt/ns-allinone-2.31/tcl8.4.14/unix:/opt/ns-allinone-2.31/tk8.4.14/unix
export PATH

export LD_LIBRARY_PATH=/opt/ns-allinone-2.31/otcl-1.13:/opt/ns-allinone-2.31/lib
export TCL_LIBRARY=/opt/ns-allinone-2.31/tcl8.4.14/library

```

---

