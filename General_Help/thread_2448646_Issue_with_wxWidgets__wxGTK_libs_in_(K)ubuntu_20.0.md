---
title: "Issue with wxWidgets / wxGTK libs in (K)ubuntu 20.04 Focal"
date: 2020-08-11
forum: General Help
---

### Post by Juhele on 2020-08-11
Hi,
I have a problem with SAGA-GIS application:
[https://sourceforge.net/projects/saga-gis/](https://sourceforge.net/projects/saga-gis/)

Before my upgrade to Kubuntu 20.04 I used SAGA 7.3 compiled from source tarball as repo only had quite old 2.x version (one of my few compilation but all went OK).

Unfortunately after upgrade to Focal I also got SAGA 7.3 from ubuntu repository and recently found out it does not work - I am unable to use the gui version. CMD seems to start OK:

```
juhele@Ono-Sendai-Cyberspace7:~$ saga_cmd
____________________________

   #####   ##   #####    ##
  ###     ###  ##       ###
   ###   # ## ##  #### # ##
    ### ##### ##    # #####
 ##### #   ##  ##### #   ##
____________________________

SAGA Version: 7.3.0


72 loaded tool libraries (682 tools):
```

but if I try to start the GUI in console it says:

```
juhele@Ono-Sendai-Cyberspace7:~$ saga_gui
saga_gui: error while loading shared libraries: libwx_gtk2u_adv-3.0.so.0: cannot open shared object file: No such file or directory
juhele@Ono-Sendai-Cyberspace7:~$ 
```

I tried to find a solution and finally tried compiling SAGA from source again, but I am unable to solve this:

```
checking whether g++ supports C++11 features with -std=gnu++11... yes
checking for local include/lib path... none
./configure: line 14693: wx-config: command not found
configure: error: SAGA requires a unicode build of wxGTK
```

I also asked SAGA devs and was told this:

> Hi Jan,
 both problems are related to the wxWidgets, i.e. the wxGTK libraries installed on your system.
 Version 7.3. from the repository is missing the  libwx_gtk2u_adv-3.0.so.0 library. It is one of the wxGTK libraries  required by SAGA. I don't know why this one is missing while others seem  to be installed on your system (otherwise saga_cmd would not run).  Maybe you could verify this with your package manager (note:  the "u" in  the library name stands for "unicode").
 Regarding your own build it is like the configure error messages  prints: you require a unicode build of the wxGTK libraries in order to  build and run SAGA. wxGTK can be build as unicode and non-unicode, and  maybe this is the culprit on your system: you seem to have a non-unicode  version installed. Maybe this is what Kubuntu 20.04 is delivering. If  there is no unicode wxGKT available, you would require to build wxGTK  yourself.
 Best regards,
Volker


Does that WxWidgets repo might have that library but no success. Does that mean I also have first compile WxWidgets and then SAGA? 

I am also thinkiug about kindly asking the maintainer for a fix - according to:
[https://launchpad.net/ubuntu/+source/saga/7.3.0+dfsg-3build5](https://launchpad.net/ubuntu/+source/saga/7.3.0+dfsg-3build5)
it should be "[Debian GIS Project]("https://launchpad.net/~pkg-grass-devel")"

Jan

---

### Post by Yellow Pasque on 2020-08-11
Did you ever remove the old version you built? It looks like it is trying to find the old version of wxwidgets (gtk2 version) and that was removed in 20.04, so you are probably trying to run the version you built locally. Confirm with:
```
which saga_gui
```

I just tested the repo version of saga_gui in my 20.04 VM and it started fine.

---

### Post by Juhele on 2020-08-11
Hmm,
you were right about that old version.

```
[FONT=monospace][COLOR=#000000]juhele@Ono-Sendai-Cyberspace7:~$ which saga_gui[/COLOR]
/usr/local/bin/saga_gui
juhele@Ono-Sendai-Cyberspace7:~$[/FONT]
```

so I performed purge of all SAGA packages via Muon and then deleted the SAGA files in [FONT=monospace]/usr/local/bin/[/FONT]

After that I installed SAGA from repo, but still having this issue:

```
[FONT=monospace]juhele@Ono-Sendai-Cyberspace7:~$ which saga_gui
/usr/bin/saga_gui
juhele@Ono-Sendai-Cyberspace7:~$ saga_gui
saga_gui: error while loading shared libraries: libwx_gtk2u_core-3.0.so.0: cannot open shared object file: No such file or di
rectory
juhele@Ono-Sendai-Cyberspace7:~$ 
[/FONT]
```

I will try to restart my PC whether it changes anything and will see.

---

### Post by Yellow Pasque on 2020-08-11
> then deleted the SAGA files in /usr/local/bin/

You need to remove all of the old files, probably by running 'sudo make uninstall' in the source directory where you ran 'sudo make install'

---

### Post by Juhele on 2020-08-11
@Yellow Pasque: Bingo! It works now. Thanks much. :D :D :D

---

### Post by Yellow Pasque on 2020-08-11
No problem. Please mark thread SOLVED (Thread Tools menu above first post).

---

