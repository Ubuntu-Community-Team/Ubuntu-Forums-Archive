---
title: "XP refugee seeking help to compile source for subversion..."
date: 2007-11-05
forum: General Help
---

### Post by sonnychee on 2007-11-05
Hey Guys,

I'm trying my hand at compiling the source for Subversion on Gutsy Gibbons 7.1 (I'd install the binaries but I couldn't locate any).  I've executed the following commands in turn (providing the root password when prompted).

> sudo ./configure
> sudo make
> sudo make install

None of the commands returned any error messages.... in fact they returned no messages at all.  According to the Subversion install notes, the last step should have created the Subversion client in /usr/local/bin .. but that folder is empty.

With no messages echo'ed to the console, I'm at a loss on how to proceed... Anyone have any ideas?  Would really appreciate any help at all.

Sonny.

---

### Post by kbracer on 2007-11-05
Subversion appears to be available for Gutsy...

[http://packages.ubuntu.com/gutsy/devel/subversion](http://packages.ubuntu.com/gutsy/devel/subversion)

Yo should be able to install it through the package manager. If you have looked and couldn't find it then you may need to enable some additional repositories (third-party?).

---

### Post by ddrichardson on 2007-11-05
Svn is available, the doc-team uses it -```
sudo apt-get install subversion
```Your problems stem from the use of sudo - you only need it for the make install, the configure and make should be done locally.

---

### Post by sonnychee on 2007-11-05
> **kbracer said:**
> Subversion appears to be available for Gutsy...

[http://packages.ubuntu.com/gutsy/devel/subversion](http://packages.ubuntu.com/gutsy/devel/subversion)

Yo should be able to install it through the package manager. If you have looked and couldn't find it then you may need to enable some additional repositories (third-party?).

Thanks for the suggestion and pointer to the binaries!  This is prolly a case of RFM... but if you wouldn't mind... how do I enable additional repositories for the package manager (apt-get or aptitude)?

Sonny.

---

### Post by sonnychee on 2007-11-05
Thanks for the pointer... I tried your supplied command 

> sudo sudo apt-get install subversion

... and nothing happened... nothing error messages, nothing echo'ed to the console.  

I also tried executing the ./configure and make commands without sudo.  In the first case, I got the error  message that gcc could not create executables and in the second case, make complained it had no targets.  My userid does not have install priviledges on my puter I presume...

Any other ideas?

Sonny.

---

### Post by ddrichardson on 2007-11-05
Just the one sudo will suffice ;-) you're redirecting sudo to sudo.


Looks like you don't have the required compilers installed - what was the exact op of ./configure

---

### Post by sonnychee on 2007-11-09
Thanks for the help guys.  

I enabled the 'partner' repositories by uncommenting a couple of lines in /etc/apts/sources.list. Once that was done sudo apt-get install subversion worked like a charm.

Sonny.

---

### Post by PhilOSparta on 2007-11-09
I followed all the steps and found that subversion was a command line application.
Doing a search for a GUI, I found rapidsvn in the repositories.  Try it.

Phil

---

