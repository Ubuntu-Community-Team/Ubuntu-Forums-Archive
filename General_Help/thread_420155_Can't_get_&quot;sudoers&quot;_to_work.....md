---
title: "Can't get &quot;sudoers&quot; to work...."
date: 2007-04-23
forum: General Help
---

### Post by yarrowfish on 2007-04-23
IDoes anyone know how to setup the sudoers file so that I don't have to type in a password when using "sudo". I thought I knew myself, but it doesn't work. I added the line 

yarrowfish  ALL=NOPASSWD: ALL

Here is how it looks.

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
yarrowfish  ALL=NOPASSWD: ALL


# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


/yarrowfish

---

### Post by zvacet on 2007-04-23
[http://ubuntuforums.org/showthread.php?t=373885&highlight=visudo]("http://ubuntuforums.org/showthread.php?t=373885&highlight=visudo")

---

### Post by lakersforce on 2007-04-23
Its not recommended though. I would advise you not to set it up, unless you really know what you are doing!!! If you are a linux guru, then by all means continue. If you are a newbie to linux STOP what you are doing. You can always open up a temporarely sudo session by typing:
```
sudo -i
```

---

### Post by aysiu on 2007-04-23
I agree with lakersforce.

If you find yourself typing *sudo* ten times, just use *sudo -i* instead. *sudo -i* essentially logs you in as root.

You should be prompted for your password only every fifteen minutes, though.

What are you doing that you have to *sudo* things every twenty minutes, many times a day?

---

### Post by yarrowfish on 2007-04-24
Hi guys!

I appreciate your help in this question, but is the syntax correct in my sudoers file? Because that still doesn't work for me. 

I know that it isn't the most secure way of working....but anyway I would like to know how to do it.


Thanks for you help

/yarrowfish

---

