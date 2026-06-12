---
title: "Using passwd"
date: 2014-04-25
forum: General Help
---

### Post by cranerja on 2014-04-25
I'm writing a script to setup multiple computers. I want to create the user and set the password automatically but passwd uses a prompt. Is there anyway to set the  password in a single line?

---

### Post by cranerja on 2014-04-25
Nevermind I didn't search hard enough.

echo username:password | sudo chpasswd

---

