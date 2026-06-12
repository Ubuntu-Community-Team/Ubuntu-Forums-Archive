---
title: "Editing Startup Programs for Other Users as Root"
date: 2007-03-04
forum: General Help
---

### Post by evandec on 2007-03-04
When I log into my regular account my whole system freezes. I think it may be because either gdesklets or beryl is set to boot at startup. I can login as root no problem. 

Is it possible to edit the programs that launch at startup for other users from the root account?

---

### Post by chggr on 2007-03-04
> **evandec said:**
>  
Is it possible to edit the programs that launch at startup for other users from the root account?

Under the home directory of every user, there is a secret folder named .config. In that directory there is another one named autostart. Into autostart you will find some files concerning the programs that launch at startup

---

