---
title: "Quotes inside quotes"
date: 2008-05-23
forum: General Help
---

### Post by jmvidalvia on 2008-05-23
I have this command, that works:
```
sudo exim -bp | grep frozen | awk '{print $3}' | xargs exim -v -M
```
When I try to add an alias, as folows...
```
alias sendfrozen='exim -bp | grep frozen | awk '{print $3}' | xargs exim -v -M'
```
...alias is not accepted, as it understands the command ends at the second '
My question is: how can I substitute ' by a different sign?
Or, how can I solve it?
Thanks a lot!

PS: I tried ` and ´ with no success.

---

### Post by brownicb on 2008-05-23
alias sendfrozen="exim -bp | grep frozen | awk '{print $3}' | xargs exim -v -M"

or

alias sendfrozen='exim -bp | grep frozen | awk '\''{print }'\'' | xargs exim -v -M'

---

### Post by jmvidalvia on 2008-05-23
Thanks!
;)

---

