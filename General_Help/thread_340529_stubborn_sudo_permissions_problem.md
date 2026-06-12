---
title: "stubborn sudo permissions problem"
date: 2007-01-17
forum: General Help
---

### Post by billyfalconer on 2007-01-17
I've used visudo to add a user to the "user privilege specification" stanza of /etc/sudoers, and the graphical user management utility shows the user to be part of the sudo group, but I'm still getting "sudo: must be setuid root" and "Su returned with error" messages for this user.

If I check the groups through the shell, I get: 

root@ubuntu:~# sudo adduser *username* admin
The user `*username*' is already a member of `admin'.

root@ubuntu:~# sudo adduser *username* sudo
The user `*username*' is already a member of `sudo'.

 Any suggestions? This is on an edgy install.

---

### Post by bodhi.zazen on 2007-01-17
What modifications did you make via visudo ?

---

### Post by billyfalconer on 2007-01-17
> **bodhi.zazen said:**
> What modifications did you make via visudo ?

All I did was add the user to the "user privilege specification" stanza (*username*    ALL=(ALL) ALL). I saved it with <ctrl>-O.  I understood visudo would convert  the .tmp file to the regular file after it quit, and it seems to have done so (the *username* line is in the file).

---

### Post by bodhi.zazen on 2007-01-17
I do not think you need to add the user name to visudo.

Just add the user to admin and sudo

And you should haev a line in visudo (/etc/visudoers)

%admin ALL=(ALL) ALL

or

user_name ALL=(ALL) ALL

should give access to your user, no ?

See here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_allow_more_sudoers](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_allow_more_sudoers)

Perhaps reboot ?

---

### Post by billyfalconer on 2007-01-17
> **bodhi.zazen said:**
> Just add the user to admin and sudo

I did that.

> **bodhi.zazen said:**
> And you should haev a line in visudo (/etc/visudoers)

%admin ALL=(ALL) ALL

or

user_name ALL=(ALL) ALL


I have both of those.

> **bodhi.zazen said:**
> should give access to your user, no ?

According to everything I've read, it would, but it doesn't.

> **bodhi.zazen said:**
> See here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_allow_more_sudoers](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_allow_more_sudoers)

I did everything there,  but nothing's changed.  That page did recommend adding the additional user to the end instead of the user privilege specification stanza, but that didn't work either.

> **bodhi.zazen said:**
> Perhaps reboot ?

That doesn't change anything.

---

### Post by bodhi.zazen on 2007-01-17
> **billyfalconer said:**
> That doesn't change anything.

hate it when that happens :(

My only thoughts,

Is the other users account working ? you did not deactivate it did you? Or expired password?

---

