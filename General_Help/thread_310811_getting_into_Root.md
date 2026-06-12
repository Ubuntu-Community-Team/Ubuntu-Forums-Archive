---
title: "getting into Root"
date: 2006-12-01
forum: General Help
---

### Post by The Drew on 2006-12-01
Here is my problem:

I installed Ubuntu, and set the password for my user account.  Unfortunately, it is evidently not my root password.
Any way I can find out what my root password is?

---

### Post by bruenig on 2006-12-01
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

To sum that up use
```
sudo command
```
To run any command that needs root. Then provide your user password.

---

### Post by LLRNR on 2006-12-01
Hi and welcome !

By convention, you don't get a root password... you're just a simple user until you need to do some actions that require root privileges. For doing such actions, precede the command you input in the [terminal](http://www.psychocats.net/ubuntu/terminal) with the word "sudo" (more info [here](http://www.psychocats.net/ubuntu/permissions)).

LLRNR

---

### Post by The Drew on 2006-12-01
oh.  Thank You.

---

