---
title: "problems starting administrative applets"
date: 2006-07-13
forum: General Help
---

### Post by weejie526 on 2006-07-13
Hello,
I'm having problems opening some of the Administration applets. I think thats what they're called. If you go to the toolbar at the top of the screen they're under the System menu. Anyway, when I click on some of the options like Networking, or Update Manager or Users and Groups, I get something on the taskbar on the bottom of the screen that says "Starting Networking" and it never starts, just kinda sits there for about 10 seconds then goes away. Can anyone help? Could it be a rights issue? If so, does anyone know how to start them at the command line? Thanks in advance.

---

### Post by mlind on 2006-07-13
> **weejie526 said:**
> Hello,
I'm having problems opening some of the Administration applets. I think thats what they're called. If you go to the toolbar at the top of the screen they're under the System menu. Anyway, when I click on some of the options like Networking, or Update Manager or Users and Groups, I get something on the taskbar on the bottom of the screen that says "Starting Networking" and it never starts, just kinda sits there for about 10 seconds then goes away. Can anyone help? Could it be a rights issue? If so, does anyone know how to start them at the command line? Thanks in advance.

If you launch update-manager from terminal, does it report any errors?

```

sudo update-manager

```

---

### Post by weejie526 on 2006-07-13
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

---

### Post by weejie526 on 2006-07-13
i get this error when i start network-admin

Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by mlind on 2006-07-13
Could you check that you're memnber of admin group: type **groups** on terminal.

Also check that your /etc/sudoers looks like
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
%admin ALL=(ALL) ALL

```


As well as you're the owner of ~/.Xauthority file.

---

### Post by weejie526 on 2006-07-13
below the line is what is in my sudoers file. i am a member of admin, but i don't know where that /.Xauthority file is

---------------------------------------------------------------------------
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
%admin ALL=(ALL) ALL

---

### Post by mlind on 2006-07-13
> **weejie526 said:**
> below the line is what is in my sudoers file. i am a member of admin, but i don't know where that /.Xauthority file is


~/ means your $HOME directory. Type *ls -l ~/.Xauthority* to see the permissions.

---

### Post by weejie526 on 2006-07-13
-rw------- 1 lou lou 115 2006-07-13 19:24 /home/lou/.Xauthority


thats what i got. thanks for you help so far btw.

---

### Post by mlind on 2006-07-14
> **weejie526 said:**
> -rw------- 1 lou lou 115 2006-07-13 19:24 /home/lou/.Xauthority


thats what i got. thanks for you help so far btw.

Everything looks like it should so far. Could you try creating another user for test purposis that has 'admin' privileges and see if administravite apps work.

---

### Post by weejie526 on 2006-07-14
Hey mlind,
thanks for all your help. i'm pretty sure i fixed the problem. turns out i somehow became the owner of the /etc/sudoers file instead of root. i did su root at the command line, typed the password, then executed "chown root.root /etc/sudoers" and then set the level to 440. and now i can sudo just fine. thanks again for all your help.

---

