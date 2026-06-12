---
title: "gnome-keyring-daemon AND evolution 3.20.5"
date: 2016-10-12
forum: General Help
---

### Post by cigtoxdoc on 2016-10-12
Gnome-keyring-daemon has stopped working correctly with evolution 3.20.5.  If I start from cold or warm boot, evolution keeps asking for the password for each e-mail account and never remembers the passwords.  Oftentimes, such delay causes communications with POP servers to timeout.  However, if I kill the gnome-keyring-daemon, it comes back asking for my system password, and then starts working correctly.  I have have reinstalled the program; however, that does not solve the problem.  This problem started about a week ago.  Everything is up-to-date and nothing is changed by running sudo apt-get update && sudo apt-get upgrade.

How does one fix this problem?

Thank you,

John

---

### Post by cigtoxdoc on 2016-11-02
I would appreciate help with this problem, which first surfaced around 6 Ocotber.  In order for evolution 3.22.5 to work correctly after a cold or warm boot, gnome-keyring-daemon most be stopped before opening evolution.  Once evolution is opened, another window opens asking for the user's password to unlock the keyring.  Once the password is entered and the keyring unlocked, evolution performs normally.  Based on comments I have received on [email]evolution-list@gnome.org[/email], this problem is restricted to Ubuntu.

Thank you in advance.

John

---

### Post by grist2 on 2016-11-22
I'm having this same issue. At least I now have a workaround.

---

### Post by cigtoxdoc on 2016-11-22
Hello grist2,

Thank you for your reply.  I am glad that I am not alone in recognizing this problem.  I have also had to teach my secretary on the workaround to deal with this problem.  I reported this to the evolution list (evolution-list@gime.org) and did not get replies that others are having the problem.  Believe this problem is unique to Ubuntu 16.04.   It started around October 5 or 6.  Perhaps one of the moderators will get involved and let us know how we should get the proper attention to this problem.


John

---

