---
title: "logon or login script?"
date: 2007-05-10
forum: General Help
---

### Post by behrendtb on 2007-05-10
I got ubuntu installed, and got it connected to my Windows Active Directory server using [http://sadms.sourceforge.net/](http://sadms.sourceforge.net/).  I have no problem logging in using my windows users.

Now my question is, how can i set up login scripts like I have running in windows.   I want different shares mounted depending on who is login in.   It would also be nice to script different things like printers and such also.

-bj

---

### Post by amicitas on 2007-05-10
There are a couple files that are sourced on login (either to your desktop manager, or to a terminal).
[https://wiki.ubuntu.com/environment_variables]("https://wiki.ubuntu.com/environment_variables")

If you are using bash,  the global login file is /etc/profile, and the user login files are ~/.bash_profile

(note that .bash_profile is different from .bashrc in that .bash_profile is only sourced on login (or on the start of a login terminal).  .bashrc will be sourced for any kind of terminal startup.)

Now if you are not using bash, then these files are not sourced.  I do not know what the equivalents are for csh based shells (like tcsh).


amicitas.

---

