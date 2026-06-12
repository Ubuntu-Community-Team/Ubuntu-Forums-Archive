---
title: "modifications to sudoers have no effect .."
date: 2007-04-24
forum: General Help
---

### Post by sveinn on 2007-04-24
Hello, 

Just upgraded to Feisty.

I've tried the two following modifications to /etc/sudoers in order to run firestarter and visudo direct off the command line:

   myusername ALL=NOPASSWD:/usr/sbin/firestarter

   myusername ALL=NOPASSWD:/usr/sbin/visudo

However, when I try to run visudo direct, Feisty replies (in the terminal)

   visudo: /etc/sudoers: Permission denied

and when I try firestarter, Feisty replies (in a dialog box)

   "Insufficient privileges: You must have root access to use Firestarter"

Seems like modifications to /etc/sudoers are not having effect. 

Any thoughts?

Sveinn

---

### Post by bapoumba on 2007-04-24
[http://www.die.net/doc/linux/man/man5/sudoers.5.html]("http://www.die.net/doc/linux/man/man5/sudoers.5.html")
> When multiple entries match for a user, they are applied in order. Where there are conflicting values, the last match is used (which is not necessarily the most specific match).

This could be one reason (and sorry, it's just a guess). The examples at the end of the link can give you ideas.
I do not know if the "spaces" are mandatory in the syntax (you do not have any).

---

### Post by zvacet on 2007-04-24
[http://www.psychocats.net/ubuntu/sudo]("http://www.psychocats.net/ubuntu/sudo")

---

### Post by hyperair on 2007-04-24
Those edits cause the sudo not to prompt for password when running those applications. This means that when you run sudo firestarter and sudo visudo it won't prompt for a password. On the other hand, you cannot run them directly because you lack the permissions to do so.

---

### Post by aysiu on 2007-04-24
You still have to run applications with *sudo* or *gksudo* , even if you are not asking for a password.

By the way, I'm not sure what this is: ```
visudo: /etc/sudoers: Permission denied
``` Isn't the command supposed to be ```
sudo visudo
```

---

### Post by sveinn on 2007-04-24
Hi, 

Thanks for the tips about having to use "sudo".

Tried that, but "sudo firestarter" and "sudo visudo" result in a prompt for a password. 

Also tried the following in "sudoers"

sveinn ALL=(ALL) NOPASSWD: /sbin/reboot

but reboot also requires a password.

So changes to /etc/sudoers still don't seem to have any effect!

Sveinn

---

### Post by aysiu on 2007-04-24
```
sudo visudo
``` *should* prompt you for a password--that's the proper command to edit the /etc/sudoers file.

I'm not 100% sure about this, but maybe spaces matter in terms of syntax? In other words, ```
myusername ALL=NOPASSWD:/usr/sbin/firestarter
``` might be different from ```
myusername ALL = NOPASSWD: /usr/sbin/firestarter
```

---

### Post by hyperair on 2007-04-24
My /etc/sudoers file looks like this: 

```

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
ALL     ALL=(root) NOPASSWD: /usr/bin/gtkwifi-settings-client

hyperair ALL = NOPASSWD: /sbin/tuncfg

```

The last line I just added based on your post for Hamachi's tuncfg and for testing purposes. It works for me.

---

