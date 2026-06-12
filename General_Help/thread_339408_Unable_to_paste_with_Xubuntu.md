---
title: "Unable to paste with Xubuntu"
date: 2007-01-15
forum: General Help
---

### Post by sobepmp on 2007-01-15
I am using Xubuntu Edgy 64-bit.  I can copy but not paste.  I tried dragging and dropping files but that didn't work.  I searched Google and the forums but didn't find any answers.  I Just found out I can copy and paste to my home directory. but thats about it  I want to copy a Fluxbox style from my desktop to usr/share/fluxbox/styles.  Do I need to login as root or something?  With Dapper I didn't have any problems.

---

### Post by imon9 on 2007-01-15
yes, u can't paste to anything under system folder because u are a "user" not "root"
so u don;t have the permission to do so...

here is what i got as workaround, not the best, but worth a try

first, create a launcher at your desktop...

put this as the command: gksudo Thunar %F

when u launch thunar from this particular launcher, it will as for your user password. For there on, u will be able to do anything with filesystem

the reason this ezist is to protect you from messing with the system file

---

