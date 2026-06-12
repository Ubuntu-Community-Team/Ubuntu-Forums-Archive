---
title: "err probably a stupid question, but"
date: 2007-07-10
forum: General Help
---

### Post by DirtyDawg on 2007-07-10
Err probably a stupid question, but, i just downloaded and installed with no problems except,
when i do an su, to install an app, it obviously asks for the password...
I assume im automatically in user login and not root, but is there a default login + pass for root,
my own doesnt work, pls help, cheers.

---

### Post by az on 2007-07-10
> **DirtyDawg said:**
> Err probably a stupid question, but, i just downloaded and installed with no problems except,
when i do an su, to install an app, it obviously asks for the password...
I assume im automatically in user login and not root, but is there a default login + pass for root,
my own doesnt work, pls help, cheers.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The root account is not used.

---

### Post by DirtyDawg on 2007-07-10
Thanks for the info :)

---

### Post by Tyche on 2007-07-10
> **DirtyDawg said:**
> Err probably a stupid question, but, i just downloaded and installed with no problems except,
when i do an su, to install an app, it obviously asks for the password...
I assume im automatically in user login and not root, but is there a default login + pass for root,
my own doesnt work, pls help, cheers.

There is a way to force it.  In a terminal, at the prompt, type:
>> sudo passwd

It will ask you for your password (It is asking for you Super User password).  Enter one
It will ask you to confirm it.  Enter it again.

Now you can su without problems (this includes those programs that insist that you do not have the correct password when it asks for a root password.

Craig
Tyche

---

