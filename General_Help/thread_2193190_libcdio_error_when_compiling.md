---
title: "libcdio error when compiling"
date: 2013-12-11
forum: General Help
---

### Post by adec2 on 2013-12-11
Hi I am getting this error when i do a compile

The following packages have unmet dependencies.
 libcdio-dev : Depends: libcdio13 (= 0.83-4ubuntu1) but 0.83-5~ppa+raring2 is to be installed
E: Unable to correct problems, you have held broken packages.

What does this mean exactly, all i know is i already have libcdio=dev installed

Thanks :)

---

### Post by steeldriver on 2013-12-11
That looks like a package manager error, not a compiler error - can you give us some more context about what you're trying to do / what commands you are using?

---

### Post by adec2 on 2013-12-11
i am trying to compile a program called mednafen

when i type ./configure i get this error

configure: error: *** libcdio not found

---

### Post by steeldriver on 2013-12-11
well it looks like you have a ppa that wants to install a newer version of libcdio13 which is not compatible with the available libcdio-dev from the main repository

---

### Post by adec2 on 2013-12-11
ah and how do i find out which one and what to do?

Edit, thanks to you steeldriver you inadvertently pointed me out in the right direction.
I now have it compiled by entering the command 

sudo apt-get install libcdio13=[COLOR=#000000][FONT=Verdana]0.83-4ubuntu1

then
sudo apt-get install libcdio-dev

now the compile ends correctly. Still going to route out the ppa that is offending and trying to install the other.

Is there a command to search for what ppa hold what files on my system?[/FONT][/COLOR]

---

