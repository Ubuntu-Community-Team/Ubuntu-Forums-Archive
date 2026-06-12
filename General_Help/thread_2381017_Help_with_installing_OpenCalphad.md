---
title: "Help with installing OpenCalphad"
date: 2017-12-25
forum: General Help
---

### Post by befana on 2017-12-25
Hello!
I am trying to install [OpenCalphad]("http://www.opencalphad.com/downloads.html") on Xubuntu 16.04.3 LTS.
I am following the instructions given in the Install-OC-Linux.pdf file, but I don't know how to set a path and how to create an environment variable, so I can not execute all the necessary steps, namely:

	- “Make sure your PATH includes the directory with the GNUPLOT program. If you do
 not know how to set your PATH ask a local expert.”

and 

	- “Create an environment variable called OCHOME with the path to your OCHOME
 directory. If you do not know how create an environment variable please ask a local
 expert.”

Also, I don't know any local expert.
Any help will be appreciated.

---

### Post by Holger_Gehrke on 2017-12-25
If you installed gnuplot from the repositories (meaning through the "Software" application, through synaptic or with apt / apt-get) it got installed in /usr/bin and that directory is in the PATH. If you installed from source and didn't change the default directories through 'configure', the program should end up in /usr/local/bin after 'make install' and that too is in the PATH. So it probably isn't necessary to change the PATH. To check whether it's in the path, you can just enter 'gnuplot --help' in the shell. If this gives you a description of the command line options for gnuplot, than everything is OK.

Creating an environment variable is quite simple:
```
export OCHOME=/home/[COLOR=#ff0000]yourusername[/COLOR]/OCHOME
``` will set the variable OCHOME to the value after the '=' and make the variable available to programs started by the shell. Change the text in red to your username on your machine. If you want this variable to get set automatically, you can add this line to the file '~/.bashrc'.

Holger

---

### Post by befana on 2018-01-01
Holger_Gehrke,
Thank you for your comprehensive instructions.

I have installed OpenCalphad following your instructions, but unfortunately for me, now I can not start it.

---

### Post by Holger_Gehrke on 2018-01-01
Depending on whether you compiled the normal or the parallel version of OpenCalphad, you should have an executable file named either oc4a or oc4p in the directory where you compiled OC, probably ~/opencalphad-version4, so '~/opencalphad-version4/oc4a' entered in the shell should start it.

Holger

---

### Post by befana on 2018-01-02
I have compiled the normal version, and there is oc4A file in my opencalphad-version4 folder. I have watched the instructions video for installing OpenCalphad on Windows, and I know that oc4A is the file I have to run. But I can not start it neither via terminal nor by clicking on it.

---

### Post by dragonfly41 on 2018-01-02
Make the file oc4A executable using this command

```
cd ~/opencalphad-version4
chmod +x oc4A
```

---

### Post by befana on 2018-01-03
It is executable:

```
mariana@mariana-Inspiron-5520:~/opencalphad-version4$ sudo chmod +x oc4A
[sudo] password for mariana: 
mariana@mariana-Inspiron-5520:~/opencalphad-version4$ oc4A
oc4A: command not found
mariana@mariana-Inspiron-5520:~/opencalphad-version4$ oc4a
oc4a: command not found
mariana@mariana-Inspiron-5520:~/opencalphad-version4$ ls
changes.txt			   macros	      ocnum.mod
cmon1oc.mod			   Makefile	      ocnum.o
documentation			   Makefile-parallel  ocsmp.mod
general_thermodynamic_package.mod  manual	      pmain1.F90
GNU-GPL-v3.pdf			   matsmin.o	      pmain1-save.F90
gtp3.o				   metlib3.o	      pmon6.o
installation			   metlib.mod	      README.md
liboceq.a			   minimizer	      readme.pdf
liboceq.mod			   models	      readme.tex
liboceqplus.mod			   numlib	      smp2.o
linkmake.cmd			   OC3-commands.pdf   stepmapplot
linkoc				   oc4A		      TQ3lib-clean
linkocdate.F90			   ochelp.hlp	      TQ4lib
linkpara			   oclablas.mod       userif
lmdif1lib.o			   oclablas.o	      utilities
```

---

### Post by Holger_Gehrke on 2018-01-03
For security reasons Linux does not search the current working directory for executables by default (just imagine the ... hilarity ... if some joker left an executable script named 'ls'  in a directory ...). To run an executable file in the current directory you have to preface it with './'. So to execute oc4A in the current directory you have to type './oc4A' (note the capital 'A'; linux is case sensitive).

Holger

---

### Post by dragonfly41 on 2018-01-03
I have nil experience with this software
but from directory ~/opencalphad-version4
try launching ./oc4A .. instead of oc4A

[Later edit]
Sorry .. I did not see that Holger has answered.

---

### Post by befana on 2018-01-03
Thank you.
Obviously, I am a linux illiterate.

It runs with ```
./oc4A
``` .

Thread marked as solved.

---

