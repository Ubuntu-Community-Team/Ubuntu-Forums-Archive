---
title: "Having an issue with setting LS_COLORS"
date: 2020-05-14
forum: General Help
---

### Post by dawson-m-schaffer on 2020-05-14
I am running Ubuntu 20.04 LTS with Bash version 5.0.16(1)-release.  I have a simple setting in my .bashrc.

[SIZE=3]_Version 1 (with and without export)_[/SIZE]
# file colors
echo $LS_COLORS
LS_COLORS=$LS_COLORS'di=0;96:'

[SIZE=3]_Version 2 (with and without export)_[/SIZE]
# file colors
echo $LS_COLORS
LS_COLORS='0;96:'

I have restarted my terminal and no changes.  The LS_COLORS value does not change and remains the original value.  However is I use either of the statements at the bash prompt the file listings change.  I have searched ever way I can think of of the last couple of days to no avail.  I would appreciate any help anyone can provide.

---

### Post by coffeecat on 2020-05-15
Support, not chat.

*Thread moved to **General Help**.*

---

