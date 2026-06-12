---
title: "MathLM installation problem in Ubuntu"
date: 2007-06-28
forum: General Help
---

### Post by somitras on 2007-06-28
My office has purchased a 3 user license of Mathematica 5.2. I am trying to install the license manager software MathLM on a newly installed Ubuntu Machine. The software works fine till the end, but then the MathID is not displayed on the machine. Without this the license cannot work and Mathematica can't be installed. 

Could anyone please help solve this problem. What could be causing this issue ?


Here is the output of the installation:



#sh ./MathLMInstaller 

-------------------------------------------------------------------------
                       MathLM 5.2 Installer
-------------------------------------------------------------------------

You can use this installer to install MathLM for the first
time, or to install a new version when you already have a
previous version installed. To complete the installation, you
will need a MathLM password.

To receive a password, register your copy of MathLM by going to
register.wolfram.com. You can also find registration instructions
in the file SysAdminGuide.pdf on the MathLM CD, or on the web at
support.wolfram.com/networkmathematica/

./MathLMInstaller: 218: /media/cdrom/Unix/bin/Linux/mathinfo: Permission denied
To register and get a password you will need to supply the
following information:

  Machine name:  crypto
  MathID:        

Enter 'c' to continue or 'e' to exit the installer [c]: 

============

---

### Post by bindatype on 2007-12-19
I figure this guy found his answer already but for others reading this, he should have a license that includes:

Platform;Configuration;Processes;Version;MathID;Hostname;Password:Requestor;Email

and secured passwords for PC and Unix. There will also be a code that has the format Lnnnn-nnnn where n are numbers. If you don't have this then call Mathematica and get it. I've installed on 6.06 with success. Good luck.

---

