---
title: "Adding user to sudo group is ineffective"
date: 2021-02-12
forum: General Help
---

### Post by John Nagle on 2021-02-12
Setting up a new Ubuntu 20.04 LTS system. 

I want to allow SOMEUSER to make "sudo" commands. So I log in as "user", and enter
**sudo usermod -aG sudo SOMEUSER**

and it seems to work. If I enter **groups** I get

**SOMEUSER: SOMEUSER sudo**

OK, fine. Then I switch users to USER and have a new GUI environment.
I try **groups** there. I get

**SOMEUSER: SOMEUSER**

No "sudo".  I try logging out of SOMEUSER and logging back in. Doesn't help.

It's consistent. 

Running as "user", I see SOMEUSER in "sudo". Running as SOMEUSER, I don't.

SOMEUSER can't make "sudo" commands. "Not in the sudoers groups".

OK, what changed?   (And is there a current GUI for this?)

---

### Post by tea for one on 2021-02-12
> **John Nagle said:**
> And is there a current GUI for this?

Settings > Users > Unlock > Add User > Standard or Administrator

I've not had any need to use it but it may answer your question.

---

### Post by John Nagle on 2021-02-12
Had to log out and log in again before the change took effect.

---

### Post by TheFu on 2021-02-12
> **John Nagle said:**
> Had to log out and log in again before the change took effect.

That's to be expected.  It is how the entire session sees group changes.
However, you could have used the **newgrp** command inside 1 terminal to see the update too - for that terminal window and all child processes.

---

