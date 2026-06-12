---
title: "How do I login as root? [Resolved]"
date: 2007-05-13
forum: General Help
---

### Post by Dimension7 on 2007-05-13
I added another user in Ubuntu.  After logging in thru this username and password, how do I login as root or enter to the administration priviledges without having to switch to my username?

For example I want to "sudo" a command, it prompts me for password, but neither the new account's password nor my account's password works.  Is this possible?

---

### Post by floke on 2007-05-13
When you created the new user, did you give them administrative privilges? New users created do not have admin privileges by default.

---

### Post by joe.turion64x2 on 2007-05-13
You set up a root password, didn't you?

---

### Post by aysiu on 2007-05-13
> **joe.turion64x2 said:**
> You set up a root password, didn't you? Completely unnecessary.

> **Steve.K said:**
> When you created the new user, did you give them administrative privilges? New users created do not have admin privileges by default. Logged in as *oldusername*, issue this command to make sure the new users is able to *sudo*: ```
sudo adduser *newusername* admin
``` Then log in as *newusername* and run your regular *sudo* commands.

---

### Post by Dimension7 on 2007-05-13
Thanks guys for your replies.

Steve.K, you are correct admin priviledge is not enabled by default.
(Duh, I should have check that first before posting, sorry.)

---

