---
title: "Z shell: location of .zshrc"
date: 2006-11-27
forum: General Help
---

### Post by bloodyhobbit on 2006-11-27
I'm running Ubuntu Dapper Drake. Following an advice in "Running Linux", I decided to switch to zsh while I'm still a novice. So I installed zsh 4.2.5-23ubuntu3 with Synaptic, changed the shell to zsh with chsh. The problem is, I can't find my .zshrc, .zhenv etc. Z shell manual says the following:
> 
You'll see they [startup files] fall into two classes: those in the /etc directory, which are put there by the system administrator and are run for all users, and those in your home directory, which zsh, like many shells, allows you to abbreviate to a `~'. It's possible that the latter files are somewhere else; type `print $ZDOTDIR' and if you get something other than a blank line, or an error message telling you the parameter isn't set, it's telling you a directory other than `~' where your startup files live.

There are no startup files (.zshrc, .zshenv, .zprofile, .zlogin) in my home directory and
```

% print $ZDOTDIR

```
prints a blank line. I do, however, have the startup files in my /etc/ directory. There is also a .zshrc in /etc/skel/.

---

### Post by bloodyhobbit on 2006-11-27
I visited the zsh-lovers IRC channel and was told that > there's not going to be startup files in your home directory unless you create them. 

---

