---
title: "logon scripts for tcsh -- setting environmental variables at login for tcsh"
date: 2007-05-07
forum: General Help
---

### Post by amicitas on 2007-05-07
I am having problems figuring out how to set environmental variables when using tcsh.

If I set my user shell to BASH then on login to GNOME or KDE Ubuntu reads /etc/profile and $HOME/.bash_profile just fine ([environment_variables]("https://wiki.ubuntu.com/environment_variables")).  

However when I set my user shell to TCSH I cannot get anything parsed on login.  I would have expected /etc/csh.login to be parsed and then $HOME/.login but neither of these seem to do anything.  


Does anyone know what is parsed at login with the user shell as /bin/tcsh, or how I could get one of these files to be parsed?

What I want to happen is for my ~/.login file to be sourced at login, but if I can find a global file then I can add in a line to source user files if they exist.

I have done a bunch of searching in the forums (and in google) but I can't seem to find any solutions that make sense to me.

Any help would be appreciated

ubuntu Feisty 7.04
kdm
(same behavior in GNOME or KDE)

- amicitas

---

### Post by amicitas on 2007-05-10
Bump.

Does anyone have any ideas on this? 
This is a rather important thing for me to get working.

Thanks in advance for any help here,

amicitas

---

### Post by stylishpants on 2007-05-10
Have you tried putting your modifications in ~/.tcshrc?  

Also, what syntax are you using to set your environment vars?  It's different from bash's syntax.  Please post your current ~/.profile.

In case you have not read it already, here is the straight dope on what files tcsh should read on startup: 
```
man tcsh | less -p 'Startup and shutdown$'
```

---

