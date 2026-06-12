---
title: "password problem"
date: 2006-12-13
forum: General Help
---

### Post by numbers1thru9 on 2006-12-13
I have a small problem with my ubuntu setup. I have it authenticating to AD for domain users. Well now my local account that was created during the install asks for my password twice now for everything. Does anyone know why?

---

### Post by numbers1thru9 on 2006-12-13
nvm i found the problem, since i added the line for AD authentication into /etc/pam.d/common-auth i needed to add use_first_pass to the end of the unix line.

---

