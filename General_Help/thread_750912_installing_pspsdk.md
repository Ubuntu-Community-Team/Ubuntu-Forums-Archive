---
title: "installing pspsdk"
date: 2008-04-10
forum: General Help
---

### Post by juliopjuliop on 2008-04-10
ok so here i go, i am trying to follow this guide [http://www.ngine.de/index.jsp?pageid=4292]("http://www.ngine.de/index.jsp?pageid=4292")and it seems im such a noob becouse i cant even istall the first step. i have downloaded the sdk and when running ./configure it said i nee dev toolchain heres the link [http://ps2dev.org/psp/Tools/Toolchain]("http://ps2dev.org/psp/Tools/Toolchain") so now i download it and read the readme it says 
1) Set up your environment by installing the following software:

  autoconf, automake, bison, flex, gcc, make, ncurses, patch, subversion, texinfo, wget

 2) Add the following to your login script:

  export PSPDEV=/usr/local/pspdev
  export PATH=$PATH:$PSPDEV/bin

 3) Run the toolchain script:

  ./toolchain.sh

ive installed all dependacies and i just need to now were my login script is,is it this one /etc/login.defs?
and if so were do i add the line?

---

### Post by juliopjuliop on 2008-04-10
please i nead some help

---

### Post by dlevans on 2008-04-18
have you gotten it to work? i have KDevelop working and i can run C++ but i dont know how to make it a .pbp for the psp i have the toolchain but i donno what or if i need anything else

---

### Post by Llanowyn on 2008-04-26
I may be wrong, but I think your login script is .bashrc in your home directory.  I'm pretty sure it's hidden by default.  This could be totally different, but that's how it's done in cygwin.

---

### Post by brethren on 2008-05-29
follow the instruction i posted here
[http://ubuntuforums.org/showthread.php?t=810527&highlight=pspsdk](http://ubuntuforums.org/showthread.php?t=810527&highlight=pspsdk)

to install the psptoolchain under ubuntu

---

