---
title: "Is the a way to run a diagnostic on ubuntu"
date: 2007-11-28
forum: General Help
---

### Post by ameba on 2007-11-28
I'm

---

### Post by x64Jimbo on 2007-11-28
Don't you normally run diagnostics to determine the cause of an existing problem rather than to locate problems that you haven't yet found?  I mean, if it works, it works, right? What problems were you hoping to discover?

---

### Post by ameba on 2007-11-28
good

---

### Post by x64Jimbo on 2007-11-28
You can only damage your system by doing things as root. Handling tar files is the same as handling any other file. If you un-tar them, compile, and install them, then you might be asking for trouble. Ubuntu's package management system is second to none, IMO. There is very little need for you to ever compile anything at all in Ubuntu. That's why they leave the compilers out of the distro by default. You can install them, but they're not there to begin with because it's pretty much assumed that you won't have a need for them. 99.9% of the time, that's a correct and reasonable assumption.

---

### Post by jocko on 2007-11-28
Why would tarballs damage the system?
*.tar.gz or *.tgz is just an archive file format, like *.zip or *.rar and such.
If you get errors when unpacking a tarball it just mean something is wrong with the file.
Do you by any chance mean you worked with some program source code that was packed into a tarball?
That shouldn't *normally* damage your system in any way either. 
If you want to be sure you'll have to be more specific on exactly what you did and which errors you got.
Probably you got errors while compiling something (often done with the command "make") because you were missing some dependencies.
In that case I don't *think* there is any way you could have damaged anything.

---

### Post by jfinkels on 2007-11-28
> **ameba said:**
> good point! well the reason why i asked was when i tried work with tarball files i recieved some errors. Also, i heard that improperly handling tarball files can damage the system.

I assume you got errors when you ran "./configure" or "make" or perhaps when you ran an "install.sh" or something similar. Post the errors in a new thread, describing the package and what steps you have already taken, and you will get help on solving your problems.

---

