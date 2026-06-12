---
title: "Sudo on remote machine does not ask for password?"
date: 2006-07-08
forum: General Help
---

### Post by z-vet on 2006-07-08
Hi all. 
I have my and my mom's computers running Dapper, configured passwordless login with ssh and added myself to adm, sudo and admin groups on second machine to perform administration tasks. Everything looks fine, but today i noticed that when i connecting to second machine through ssh and run commands with sudo it doesn't ask me for password. I don't think it's normal (or it is?), so please help me to find out what is wrong and how to fix it. Thanks.

---

### Post by bforbes on 2006-07-08
Type whoami, make sure you're not somehow root.

---

### Post by z-vet on 2006-07-08
Nope, i am not root, whoami returned my regular user name.

---

### Post by bforbes on 2006-07-08
When you sudo directly on the second machine, does it ask for a password?

---

### Post by digby on 2006-07-08
Can you post the contents of /etc/sudoers from the remote machine?

---

### Post by z-vet on 2006-07-08
> **bforbes said:**
> When you sudo directly on the second machine, does it ask for a password?
Yes.

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

```

---

### Post by Anduu on 2006-07-08
Something similar happened to me a while back.

Remove yourself from the sudo group(ie under the sudo group properties you should not be listed...) and make sure under your user properties your main group is admin not sudo.

---

### Post by z-vet on 2006-07-09
> **Anduu said:**
> Something similar happened to me a while back.

Remove yourself from the sudo group(ie under the sudo group properties you should not be listed...) and make sure under your user properties your main group is admin not sudo.

Thank you very much, it works. :)

---

### Post by Anduu on 2006-07-09
Good stuff :KS

---

### Post by matthijskooijman on 2008-02-11
I've been suffering from the same problem on my Debian etch machine. Interestingly enough, the problem didn't occur on my Debian sid machine. This thread helped me solve the problem: I now use another group than sudo for granting users sudo rights.

Some after the act research shows that the Debian packages up to 1.6.8p12-4 are compiled with the --with-exempt=sudo option, causing users in the sudo group to be able to sudo without a password (Even when the sudo group is not directly used in the sudoers file...). Since there is no way of overriding this behaviour in the sudoers file and it really isn't documented, this is stupid.

Fortunately, as of 1.6.8p12-5, this compile option is removed and sudo behaves as expected. Of course, etch ships with -4, being one revision short of being fixed :-)

---

