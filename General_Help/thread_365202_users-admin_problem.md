---
title: "users-admin problem"
date: 2007-02-19
forum: General Help
---

### Post by scooper86 on 2007-02-19
I am having the wierdest problem, when I run users admin with gksu it doesnt ask for a password, and I get the error 
"GnomeUI-WARNING **: While connecting to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."
 I therefore cannot add any users, whenever I try, the users are not saved, and disappear when I reload the program. I have ran it with sudo, gksudo and from a root terminal.
Any Ideas.
This is a completely fresh install of ubuntu btw, and the only thing I did out of the ordinary was create an /etc/skel to stop me having to set up everything individually for each user.
when I add a user through the terminal with useradd it creates no home folder so this isn't really a solution for me.

---

### Post by sdide on 2007-02-19
Hey,

useradd -m -d /home/<username> -c "<full_user_name>" <username>

---

