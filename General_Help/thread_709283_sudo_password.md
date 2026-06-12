---
title: "sudo password"
date: 2008-02-27
forum: General Help
---

### Post by nicoseb on 2008-02-27
Hi there,

It's been like 2 or 3 month (since I'm working under hardy) that I'm trying to get rid off sudo asking for password on my account.
I activated the root account (do not use it but it is just for the sake of it :)), changed my /etc/sudoers like this:

> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

Defaults        !lecture,tty_tickets,!fqdn,insults

# Uncomment to allow members of group sudo to not need a password
%sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification
nico         ALL =(ALL) NOPASSWD: ALL
# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


My user name is nico, I'm part of "sudo" and "admin" groups...
But that just doesn't do it.... I know some will tell me "careful with the root account and stuff..." but it is just that I'm always running my upgrades in a terminal (like everyday) and that is just so annoying to type my password for my account each time!!!!

So if someone knows why /etc/sudoers is overpassed by something else (I think there's something about pam) and how to change this that would be just very helpful and appreciated!!

thanks guys

---

### Post by irishgoth8822 on 2008-02-27
i think you need a couple more lines in that file, but as to specifically what, i probably won't say since i got shouted down for trying to do exactly what youre doing ;)

just poke around the forums, there is at least one thread that i found that gave me the solution.

---

### Post by nicoseb on 2008-02-27
Ahaha, fair enough.

I had been googling a few times and "foruming" (cool that's a new word) as well but didn't find anything hence my post :p

Anyway thanks I'll give it a shot!

---

### Post by bodhi.zazen on 2008-02-27
If you want root access, open a terminal and :

```
sudo -i
```

For graphical applications, use gksu

```
gksu nautilus
```

If you want to config sudo, well I am a strong believer in reading on this one :

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)

Don't take the "lack of support" on this lightly, there is a reason why seasoned users are strongly advising against these methods and it really is unnecessary.

IMO entering a password is a small price to pay for security.

---

### Post by aysiu on 2008-02-27
You can also extend the timeout on *sudo* from 15 minutes to something longer.

Why are you using root so much that a password bothers you? Do you have an extremely long (20-character or more) password?

---

### Post by nicoseb on 2008-02-27
Well, I know about the security and stuff but no one else is using my lappy apart from me and if that would happen I wouldn't care for my distro to be killed... there's way more important things lol

Anyway yes my password is quite long and I'm using sudo like 10 times a day for a purpose or another because I don't want to open my session as root...

A mysterious helper came to me and that is now working... I'm a free sudo user now!!!!

thanks guys :)

---

