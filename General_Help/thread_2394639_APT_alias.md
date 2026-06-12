---
title: "APT alias?"
date: 2018-06-19
forum: General Help
---

### Post by warmango on 2018-06-19
So what I want to do is have an alias so I can use PKG instead of APT, 

When I set the alias with
Alias pkg=apt 
It doesn't work and treats "pkg install whatever" as of I was running Apt without any arguments

---

### Post by ajgreeny on 2018-06-19
How have you created that alias? The way you have reported it will not work as you need the phrase ```
alias pkg='apt'
``` either in you .bashrc or .bash_aliases file.
More details please.

Is the alias really added to the system; check it with command **alias** which will list everything already setup.
Also bear in mind that if you are using a root terminal in order to avoid using sudo in the command any aliases set up as user will not work.

Perhaps your alias should be **alias pkg='sudo apt'** when you should just be asked for your password.

---

