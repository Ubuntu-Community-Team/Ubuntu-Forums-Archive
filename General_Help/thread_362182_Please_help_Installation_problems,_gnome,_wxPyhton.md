---
title: "Please help: Installation problems, gnome, wxPyhton, ..."
date: 2007-02-15
forum: General Help
---

### Post by FrancisA on 2007-02-15
Hi, I don't know, where to begin. 

Many questions, so I restrict myself at first for more or less to headlines .

I have installed from live cd Ubuntu edgy (6.10?).
Is that a so called developer version?

Only now, I'm confronted with several problems.

First: I cannot install several packets, that are listed in synaptic manager.
There are unresolved conflicts or conflicts, which can't be solved.
For example I tried to install the build-essentials. But that failed with 
this conflicts, after that also the g++ package (the same).

Second: I cannot compile any program, it fails even at the ./configure files.

Third: 
What is gail (gnome access Interface Library)? at all.
Reason: If i used wxPython (last release 2.8.1.1 Unicode, there are several tracebacks
or better assertions, which say:
CRITICAL **: gail_menu_item_ref_child: assertion `(i >= 0)' failed,

The same program run on other platforms from other users using the same wxPython
unicode build (I asked for that)

For example:
[http://aspn.activestate.com/ASPN/Mail/Message/wxpython-users/3398038](http://aspn.activestate.com/ASPN/Mail/Message/wxpython-users/3398038)

I would be curious, if any other person have the same problems, so I'm not 
alone with that, and searching for a solution would be easier.
In addition, google could not help me much with that errror message followed
by a crash (segmentation fault).

Fourth: 
Is it possbile to re- or make a kind of "replace" install to another stable gnome version?

I can deliver more accurate information, if they are required.

Shall I split my questions in several threads?
Basically the most important things are for me:

I have installed Ubuntu for the sake of knowing linux better, want to more 
independant of MS and third and most important point, that I can testing,
bug fixing and enhance our project DrPython on Linux and Windows.

([http://sourceforge.net/projects/drpython/](http://sourceforge.net/projects/drpython/)) 

Many thanks in advance for the time being.

---

### Post by zvacet on 2007-02-16
Do you have all repositories open?Go to system administration software repository.Check every box in ubuntu6.10,and in internet updates.Close and reload.After that go to[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Basic_Compilers_.28build-essential.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Basic_Compilers_.28build-essential.29")
You can not compile because you don´t have compilers installed.It make sense does it?

---

### Post by FrancisA on 2007-02-16
> **zvacet said:**
> Do you have all repositories open?Go to system administration software repository.Check every box in ubuntu6.10,and in internet updates.Close and reload.After that go to[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Basic_Compilers_.28build-essential.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Basic_Compilers_.28build-essential.29")
You can not compile because you don´t have compilers installed.It make sense does it?

Hello,

I cannot quite follow with "Do you have all repositories open?" :confused: 

I will follow the instructins with software repository.

I have installed gcc (which is installed by default), but not g++.

Thank you for the present.

BTW: The output was:

Die Ausgabe ist:
sudo apt-get install build-essential:
```
  
root@franz-desktop:~# apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  build-essential: Depends: libc6-dev but it is not going to be installedor
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages
root@franz-desktop:~# 

```

---

