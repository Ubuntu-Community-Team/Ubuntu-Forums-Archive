---
title: "Bash"
date: 2007-03-12
forum: General Help
---

### Post by JELO on 2007-03-12
Hi guys,
I'm currently going through a book on bash.  I got to changing variables and what not.  Upon messing with the PS1 variable I came across this
${debian_chroot:+($debian_chroot)}\u@\h:\w\$
I understand the things after the brackets but i'm not sure about the debian_chroot part.  Does this deal with security?  I somewhat understand the concept of chrooting an app but i'm not sure exactly what purpose this was serving.
Thanks

---

### Post by Mr. C. on 2007-03-12
Its just a variable.  That parameter expansion allows the prompt to contain either that value, or the user's name, etc.

Check the various shell startup scripts to see where it is defined (eg. /etc/bashrc /etc/defaults/bash, ...)

MrC

---

