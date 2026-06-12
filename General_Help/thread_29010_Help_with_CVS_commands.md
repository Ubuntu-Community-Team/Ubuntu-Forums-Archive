---
title: "Help with CVS commands"
date: 2005-04-22
forum: General Help
---

### Post by derdewey on 2005-04-22
I've been trying to install a new build of kftpgrabber (version .5 has problems which the developpers said are fixed in the CVS).  I found the commands I want to use (I think, hehe).

cvs -d:pserver:anonymous@cvs.sf.net:/cvsroot/kftpgrabber login
hit enter for the password because there is none

so now I'm signed in using CVS...  I then want to get my hands on the code files.
cvs -z3 -d:pserver:anonymous@cvs.sf.net:/cvsroot/myproject co MODULE

where MODULE is the name of the branch I want to use.  OK, so I browse the CVS using the sourceforge web-interface because I don't know what the developpers called the module/branch/whatever it is I need.  I click around on files and I notice that some of the property pages make reference to the branch for the file.  Some pages call it MAIN or KFTPGRABBER_0_5 or whatnot.  So I try out this variations using

cvs -z3 -d:pserver:anonymous@cvs.sf.net:/cvsroot/myproject co MODULE

and changing module to MAIN of KFTPGRABBER_0_5... but it doesn't work. 

So if someone could help me determine what the branch or module I would be mighty grateful.

---

### Post by jdodson on 2005-04-22
sounds like you might get better help asking the project directly as they know more about is specifically than we would.  just a suggestion.

---

### Post by derdewey on 2005-04-22
This kind of information should be somewhat easy to find, right?  I'm guessing it says it somewhere what modules there are.  You know, because you request a module and the cvs daemon knows what to get.  So shouldn't I be able to look at the possible modules/builds/whatever?

---

