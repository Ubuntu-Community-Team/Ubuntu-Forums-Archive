---
title: "Alias expansion and tab completion together"
date: 2006-11-26
forum: General Help
---

### Post by glepore70 on 2006-11-26
In my .bashrc I have the following alias:
alias apt='sudo aptitude'
however, when I type apt upg[TAB], the auto completion fails to expand the command to "apt upgrade".  Auto completion also fails to supply package names when they are started (i.e. apt install linux-kern[TAB] doesn't list all available packages.)

In my .bashrc I reference the bash_completion file before the alias command.

Any ideas on how I can get auto-completion to work with an alias?

---

### Post by meng on 2006-11-26
I can't get auto-completion to complete:
"aptitude upg"
so this may be the problem rather than the alias for aptitude. Is it the same on your system, or no?

---

### Post by glepore70 on 2006-11-26
aptitude upg[TAB] properly expands to aptitude upgrade on my system.  The problem bugs me more when it doesn't expand package names.

---

### Post by Ramses de Norre on 2006-11-26
> **meng said:**
> I can't get auto-completion to complete:
"aptitude upg"
so this may be the problem rather than the alias for aptitude. Is it the same on your system, or no?

Then you should take a look in your .bashrc or .bash_completion because that works here perfect too. Even packages are auto completed.

---

### Post by meng on 2006-11-26
> **Ramses de Norre said:**
> Then you should take a look in your .bashrc or .bash_completion because that works here perfect too. Even packages are auto completed.
Thanks for the tip!

---

