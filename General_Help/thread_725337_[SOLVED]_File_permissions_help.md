---
title: "[SOLVED] File permissions help"
date: 2008-03-15
forum: General Help
---

### Post by Nerrep on 2008-03-15
I'm attempting to get CVS set up on my webserver at the moment, but fear I will run into problems I've enjoyed in the past with file permissions.

Namely, I'll create a group 'cvsusers', and add the requisite people to it. I'll then create /var/cvsroot, and set cvsusers as the group.

My problem is now this: How do I ensure that all files created under /var/cvsroot have their group set to cvsusers (and their permissions set to 774)?

Thanks for any help.

---

### Post by Nerrep on 2008-03-15
Sorry, this one seems to have dropped off, so bump :)

Thanks,

---

### Post by Nerrep on 2008-03-16
> **Nerrep said:**
> Sorry, this one seems to have dropped off, so bump :)

Thanks,Anyone?

---

### Post by fsmithred on 2008-03-16
Pretty sure you'd do

chmod 2774 /var/cvsroot

which makes the directory sgid, so that any files created there inherit the group ID of that directory.

---

### Post by Nerrep on 2008-03-16
It appears that: 

```
find /cvs -type d -exec chmod g+s {} \;
``` 

Does the trick.

EDIT: Thanks fsmithred - managed to eventually track it down before I saw your message! I think they both do pretty much the same thing?

---

