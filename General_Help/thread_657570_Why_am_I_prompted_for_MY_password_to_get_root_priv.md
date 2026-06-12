---
title: "Why am I prompted for MY password to get root priviliges"
date: 2008-01-03
forum: General Help
---

### Post by Aereshaa on 2008-01-03
The title says it all. I have used other versions of linux before, and usually they ask for **root**'s password for **root**'s priviliges. I have never encountered this stuff before.:mad:

---

### Post by Kzin on 2008-01-03
This is fairly common, Slackware was the same... Its "sudo" not "su root".  Generally speaking, if root doesn't want to give out their password, and people still need admin access to do certain tasks, you can ensure the person doing the command is the person they say they are by asking them for their password.  This is logged as well.

HTH

---

### Post by Aereshaa on 2008-01-03
You misunderstand. If I'm logged in as Aereshaa, and I go to, say System/administration/users and groups, I get prompted for Aereshaa's password rather than root's password, as it should be.

---

### Post by taurus on 2008-01-03
Maybe you should read this link, [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).

Basically, you are running sudo/gksudo.

---

### Post by Kzin on 2008-01-03
hmmm
If you 
 ```
cat /etc/group
```
you should see Aereshaa in the admin group, because you are technically running sudo.

Let me know if I am wrong there ;-)

---

### Post by shad0w_walker on 2008-01-03
Obviously you missed the point of the reply. He told you why it is. It's so a user can be given admin privileges without being given the password of the root account. It's a security thing.

---

### Post by Kzin on 2008-01-03
> **taurus said:**
> Maybe you should read this link, [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).

Basically, you are running sudo/gksudo.

What he said.

---

### Post by Aereshaa on 2008-01-03
So, how do I set it so that if somebody tries to access root's priviliges, they are asked for root's password rather than their own?

---

### Post by shad0w_walker on 2008-01-03
If you don't want another user to have admin rights just take them from the admin group.

---

### Post by AlexThomson_NZ on 2008-01-03
Follow the link taurus sent you.

To do that, you can make it the user is not a sudoer (sudo visudo, and adjust accordingly), and create a root password (sudo passwd).

Then, you can use it like the other distros (redhat, etc). where you need to su - before doing any rooty stuff.

---

### Post by AndyCooll on 2008-01-03
> **taurus said:**
> Maybe you should read this link, [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).

Basically, you are running sudo/gksudo.

You really SHOULD read that link ...to the very end. It answers all the questions you keep asking (how to give others admin right, even how to re-enable the root password if you really must).

:cool:

---

