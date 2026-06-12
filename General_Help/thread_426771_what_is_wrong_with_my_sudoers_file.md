---
title: "what is wrong with my sudoers file?"
date: 2007-04-28
forum: General Help
---

### Post by glenmo on 2007-04-28
i think i'm doing it all right, and i can start firestarter without entering a password, but synaptic keeps asking me for my password...
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

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL
hansolo 	ALL=NOPASSWD:/usr/sbin/firestarter --start-hidden
hansolo 	ALL=NOPASSWD:/usr/sbin/synaptic

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

hansolo is my user, and there is a tab character after the username before 'ALL'...

---

### Post by aidanr on 2007-04-28
are you starting it from the menu? remember to modify the menu entry and remove "gksudo"

---

### Post by Sef on 2007-04-28
Do it this way from the Terminal: ```
gksudo gedit /etc/sudoers
```

---

### Post by glenmo on 2007-04-28
aidanr:
thanks for the suggestion -- if i start it without gksu, i get the message about starting without administrative privileges... 

sef:
don't i HAVE to use visudo to edit sudoers file?  and once i have it open in gedit, what do you suggest?

---

### Post by glenmo on 2007-04-28
that's really weird... when i do what sif said, i get:

GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


and it opens sudoers in gedit... but when i save it tells me i can't do it... read only filesystem

---

### Post by aidanr on 2007-04-28
try doing it like [this]("http://snippets.dzone.com/posts/show/838")

---

### Post by taurus on 2007-04-28
Actually, it is recommended you use visudo whenever you edit /etc/sudoers because it can check the syntax for you.

```
sudo visudo
```

---

### Post by glenmo on 2007-04-28
now it looks like this:
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

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL
hansolo 	ALL=(ALL) ALL, NOPASSWD:/usr/sbin/firestarter
hansolo 	ALL=(ALL) ALL, NOPASSWD:/usr/sbin/synaptic

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

but it still doesn't work... and i used visudo to edit

---

### Post by glenmo on 2007-04-28
i got it:
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

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL
hansolo 	ALL=(ALL) ALL, NOPASSWD: /usr/sbin/firestarter
hansolo 	ALL=(ALL) ALL, NOPASSWD: /usr/sbin/synaptic

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

this works -- i had to put the gksu back in to the menu link -- gksu is what gives me the admin rights to do stuff in synaptic -- without it i didn't have any rights... 

and it's pretty finicky with the spaces, i think...  if i don't have a space between NOPASSWD: and /usr/sbin/synaptic, it breaks...  

thanks for your help

---

### Post by glenmo on 2007-05-06
well... actually no...

it doesn't work.

don't ask my why... maybe i was hallucinating when it worked before... but it doesn't work now...

has anyone actually gotten synaptic to run on their machine without the need for a password?

---

### Post by ramjet_1953 on 2007-05-06
It's not a good idea to continually run firestarter, anyway.

Remember, firestarter is NOT a firewall, it is a configuration tool for iptables, which in it's standard state is perfectly secure anyway.

Having firestarter open continually is a grave security risk, as it is running in root mode.

Regards,
Roger :cool:

---

### Post by yarrowfish on 2007-05-06
Hi Glenmo!

Try putting the two lines at the end of the file instead. Like this:



# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL


# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

hansolo 	ALL=(ALL) ALL, NOPASSWD: /usr/sbin/firestarter
hansolo 	ALL=(ALL) ALL, NOPASSWD: /usr/sbin/synaptic

---

### Post by asipi on 2007-05-07
is user hansolo the member of the admin group? if not, so put him into...

---

### Post by dagnabit dang doohickey on 2007-05-07
```
hansolo   ALL=(ALL) ALL, NOPASSWD: /usr/sbin/synaptic, /usr/sbin/firestarter
```

[Sudoers Manual]("http://www.gratisoft.us/sudo/man/sudoers.html")

Edit: Assuming hansolo is a member of the admin group, this should be all you need:
```
hansolo   ALL= NOPASSWD: /usr/sbin/synaptic, /usr/sbin/firestarter
```

---

### Post by xangel on 2008-07-11
This is an old thread, but in case others come across the same problem:

On one occasion I found that sudoers discriminates between spaces and tabs. I believe tabs can break it and only spaces are OK, though I do not know the exact specification.

---

