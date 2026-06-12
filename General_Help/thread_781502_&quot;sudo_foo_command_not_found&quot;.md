---
title: "&quot;sudo: foo: command not found&quot;"
date: 2008-05-04
forum: General Help
---

### Post by TeeAhr1 on 2008-05-04
I've added some functions and aliases to my ~/.bashrc, but I get the above error if I try to run them with sudo. /etc/sudoers has not been changed, I thought that the line "%admin ALL=(ALL) ALL" meant any member of the admin group could run anything using sudo. Does this not apply to commands and functions created by the user? How do I add these functions to the sudo list?

Thx, as always,
-p.

---

### Post by angry_johnnie on 2008-05-04
Why don't you just incorporate sudo into the aliased command?
For instance **alias foo='sudo foo'**

---

### Post by Monicker on 2008-05-04
Did you reload your .bashrc after making the changes?  You can try "source .bashrc" or log out and log back in.

---

### Post by TeeAhr1 on 2008-05-05
Monicker: I did re-source the .bashrc.

angry_johnnie: It works when I incorporate sudo into the alias, but I don't want to do that.

-p.

---

### Post by SEMW on 2008-05-05
```
alias sudo="sudo "
```
Add it to .bashrc.  It then makes the other aliases you've defined worked when run with sudo.

Don't know why it works, but it does. ([source](https://lists.ubuntu.com/archives/ubuntu-users/2005-June/039274.html)).

I've just added this to the [https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux](https://help.ubuntu.com/community/SwitchingToUbuntu/FromLinux) community documentation page.  The default behaviour is really quite bad: especially since .bashrc comes with a selection of commented out de-dangerising aliases (e.g. alias rm="rm -i"), the fact that they don't apply to sudo'd commands by default, and there is no indication of this, IMHO qualifies as a bug.

---

### Post by maniacmusician on 2008-05-05
> **SEMW said:**
> ```
alias sudo="sudo "
```
Add it to .bashrc.  It then makes the other aliases you've defined worked when run with sudo.

Don't know why it works, but it does.
ah, beat me to it.

---

### Post by pterosky on 2011-12-13
Logging out and in fixed it, thanks Monicker!

---

### Post by nothingspecial on 2011-12-13
[attach]209036[/attach]

---

