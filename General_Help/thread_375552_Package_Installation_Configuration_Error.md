---
title: "Package Installation Configuration Error"
date: 2007-03-03
forum: General Help
---

### Post by Synteresis on 2007-03-03
Hello, 



1 week ago I erased XP completely and installed Ubuntu (6.10 ). 
The installation was successful and since then everything has appeared to run very nicely.

I have run into errors attempting to successfully install further software packages via the Synaptic Manager.  Recently for instance I tried to install gtkpod (disclaimer: received Ipod as unsolicited gift, use only for exercise!).  

Here is the error report from this installation:

This is Selecting previously deselected package libmp4v2-0.
(Reading database ... 214934 files and directories currently installed.)
Unpacking libmp4v2-0 (from .../libmp4v2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3_i386.deb) ...
Selecting previously deselected package gtkpod-aac.
Unpacking gtkpod-aac (from .../gtkpod-aac_0.99.4-0ubuntu1_i386.deb) ...
Setting up mzscheme (352-1) ...
Cataloging SLIB routines...
path->string: expects argument of type <path>; given "/usr/share/slib"
dpkg: error processing mzscheme (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of drscheme:
 drscheme depends on mzscheme (= 1:352-1); however:
  Package mzscheme is not configured yet.
 drscheme depends on mzscheme; however:
  Package mzscheme is not configured yet.
dpkg: error processing drscheme (--configure):
 dependency problems - leaving unconfigured
Setting up libmp4v2-0 (2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3) ...

Setting up gtkpod-aac (0.99.4-0ubuntu1) ...

Errors were encountered while processing:
 mzscheme
 drscheme
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up mzscheme (352-1) ...
Cataloging SLIB routines...
path->string: expects argument of type <path>; given "/usr/share/slib"
dpkg: error processing mzscheme (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of drscheme:
 drscheme depends on mzscheme (= 1:352-1); however:
  Package mzscheme is not configured yet.
 drscheme depends on mzscheme; however:
  Package mzscheme is not configured yet.
dpkg: error processing drscheme (--configure):
 dependency problems - leaving unconfigured


Errors configuring mzscheme and drscheme crop up every time I try to install a new package.  Not sure what's happening here- gtkpod for instance still works - but crashes frequently along with other choice programs. 

I'm trying hard to learn Linux like a 'responsible user'- like reading the online documentation, books and stuff.   I'm still pretty new to this stuff though, having been force-fed Microsoft all my life -- so sorry for the stupidity here. 

But if anyone knows where I can read about how to fix my problem, or is willing to tell me themselves I'd really appreciate it.  

Thanks a lot, 

Annie

---

### Post by john.nicholls on 2007-03-04
The Debian site has some good manuals on how dependencies are handled.

---

