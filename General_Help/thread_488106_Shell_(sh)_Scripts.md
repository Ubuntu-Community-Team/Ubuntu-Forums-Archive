---
title: "Shell (sh) Scripts"
date: 2007-06-29
forum: General Help
---

### Post by africantiger on 2007-06-29
I am new to Ubuntu (just installed over my Fedora Core 6) but I am having a problem running a shell script that runs just fine in FC6. 
It is the install.sh for the AventailConnect VPN client. I am getting syntax errors that makes no sense. Has anyone seen an issue like this before? To run the script I type the following:

sudo sh install.sh

which comes back with:

[: 24: ==: unexpected operator
install.sh: 30: function: not found
install.sh: 36: Syntax error: "}" unexpected


This runs fine under Fedora, it is just a sh script.

Help,


Africantiger...

---

### Post by tronica on 2007-06-29
I think its telling you that there is errors on those line numbers. I would open it up in gedit and turn on line numbering and see whats on those lines.

---

### Post by stylishpants on 2007-06-30
Instead try this:

```
sudo bash install.sh
```


"sh" is actually a symlink to "bash" on many systems, but in Feisty it's a link to "dash".

---

### Post by clakomy on 2008-05-09
> **stylishpants said:**
> Instead try this:

```
sudo bash install.sh
```


"sh" is actually a symlink to "bash" on many systems, but in Feisty it's a link to "dash".


Thank you for the solution! It worked like a charm.

---

