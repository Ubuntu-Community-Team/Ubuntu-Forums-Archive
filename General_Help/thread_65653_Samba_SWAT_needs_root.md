---
title: "Samba SWAT needs root?"
date: 2005-09-14
forum: General Help
---

### Post by marcw on 2005-09-14
After installing and activating samba and SWAT, I find that logging in to SWAT with my normal UID that I don't have available to me several SWAT icons.  I know this because I have run SWAT on other machines.  I'm fairly certain that I don't see these other icons because I'm not authenticating into SWAT with a root login.  And I can't, of course, because Ubuntu doesn't use root.

What should I do?  Thanks!

---

### Post by NewbieNik on 2005-10-17
Run firefox as root

"Sudo firefox"

Firefox then passes those credentials to swat. Should work fine! (Fingers crossed)

---

