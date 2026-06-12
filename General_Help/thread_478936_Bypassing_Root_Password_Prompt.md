---
title: "Bypassing Root Password Prompt"
date: 2007-06-19
forum: General Help
---

### Post by Sonofmoog on 2007-06-19
I have edited /etc/sudoers to add $USER with a NOPASSWD stanza.  Yet, I have two problems:

1) None of the applications I launch from the taskbar with *sudo <appname> * will open.  They just .. die.

2) When I switch to *gksu appname*, I still get asked for a password

Is there an ironclad, foolproof way to bypass the prompt for password to get root privileges in Ubuntu?  

I am well aware of all the reasons why one should not do this.  They do not apply to me in my present circumstances

---

### Post by Happy_Man on 2007-06-19
You could unlock the root account.... I'm not sure how to do that. But if the reasons against do not apply..... *shrugs*

---

### Post by Qu4k3R on 2007-06-20
> **Sonofmoog said:**
> I have edited /etc/sudoers to add $USER with a NOPASSWD stanza.  Yet, I have two problems:

1) None of the applications I launch from the taskbar with *sudo <appname> * will open.  They just .. die.

2) When I switch to *gksu appname*, I still get asked for a password

Is there an ironclad, foolproof way to bypass the prompt for password to get root privileges in Ubuntu?  

I am well aware of all the reasons why one should not do this.  They do not apply to me in my present circumstances

Have you edited the sudoers file with visudo ?
Could you "cat" or show the sudoers file ?
Thanks

---

### Post by Sonofmoog on 2007-06-20
> **Qu4k3R said:**
> Have you edited the sudoers file with visudo ?
Could you "cat" or show the sudoers file ?
Thanks

Thanks for replying ..

Yes to the first question .. 

Here is my /etc/sudoers.  (I have removed the #comments from the file .. )

> Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
reb     ALL=(ALL) NOPASSWD: ALL


# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by Sonofmoog on 2007-06-20
> **Happy_Man said:**
> You could unlock the root account.... 

Thanks for the reply.
The root account is unlocked

---

### Post by Qu4k3R on 2007-06-21
This sudoers file has sudo passwords disabled.

> 
# Defaults

Defaults        !lecture,tty_tickets,!fqdn,insults

# User privilege specification
root    ALL=(ALL) ALL
reb   ALL=(ALL) NOPASSWD:ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%reb ALL=(ALL) NOPASSWD:ALL


Be sure about the usernames.
Maybe you need to add your username to root and admin's group.

---

### Post by Bachstelze on 2007-06-21
The sudoers file works only for sudo. There is no way to "bypass" the password prompt for gksudo - that I know of.

---

### Post by neptho on 2007-06-21
> **Sonofmoog said:**
> I2) When I switch to *gksu appname*, I still get asked for a password

From the man page:

```
gksu  is a frontend to su and gksudo is a frontend to sudo.  Their pri&#8208;
       mary purpose is to run graphical commands that need  root  without  the
       need to run an X terminal emulator and using su directly.

       Notice  that  all the magic is done by the underlying library, libgksu.
       Also notice that the library will decide if it should use su or sudo as
       backend  using the /apps/gksu/sudo-mode gconf key, if you call the gksu
       command. You can force the backend by using the gksudo command,  or  by
       using the --sudo-mode and --su-mode options.
```

Use 'gksudo' instead.

---

### Post by Sonofmoog on 2007-06-21
My thanks to all for your responses.  I'm finally in business, but not really quite sure how I did it .. (I get that a lot in Linux ..)  I think adding my name to the admin group then putting this into /etc/sudoers is what did the trick:

> %admin ALL=(ALL) NOPASSWD:ALL

---

