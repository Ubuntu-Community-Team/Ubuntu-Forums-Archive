---
title: "gnome-keyring when tunneling SSH"
date: 2019-01-02
forum: General Help
---

### Post by stonefish2 on 2019-01-02
Hi All,

I use evolution on Ubuntu 18.04 in a desktop environment and it stores my passwords and certificates used for accessing multiple SMTP and IMAP servers when I access the desktop via GDM.
However when I tunnel evolution via SSH it prompts me for my passwords. I assume that passwords are managed in Gnome-keyring however how do I make this unlock when I access evolution via SSH and X-forwarding. 

I would prefer to continue to use X and SSH however I would like applications to actually work.
auth     optional  pam_gnome_keyring.so
session  optional  pam_gnome_keyring.so auto_start 

However this didn't make things work automagically. Suggestions would be appreciated.

---

