---
title: "How do I change my master password?"
date: 2015-09-25
forum: General Help
---

### Post by michael-piziak on 2015-09-25
Ubuntu 12.04 lts

How do I change my master password - for example, the password it asks for when doing a software update - ?

---

### Post by TheFu on 2015-09-26
Open a terminal.
type **passwd**
Enter the current password, followed by the new password you want, twice. There are prompts.

This changes the account login password which controls sudo as well. If you have auto-login enabled, that will not be changed.

---

### Post by michael-piziak on 2015-09-26
*passwd*: command not found

---

### Post by howefield on 2015-09-26
passwd is the correct command, might help for you to post the actual terminal output in full.

You can also change the password via System Settings > User Accounts. The screenshot is from 15.04, so is likely be slightly different to 12.04 but it should be obvious enough in how to change the password.

---

### Post by michael-piziak on 2015-09-26
my bad,
i had entered *passwd*
did it again with passwd and it works!

marking this as solved

---

### Post by TheFu on 2015-09-26
To mark a thread as solved, please use the "Thread Tools" menu above.
This helps both solution seekers AND helpers.

---

### Post by michael-piziak on 2015-09-26
yep i know how,
just forgot to

thanks for reminding me!

---

