---
title: "Cannot Open Firestarter With a Text Editor"
date: 2008-06-14
forum: General Help
---

### Post by Ivan_B on 2008-06-14
This is what I get when I try to open Firestarter with Gedit:

"Could not open the file /usr/sbin/firestarter.
gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again."

How could I fix that? Any help is appreciated, thanks! :D

---

### Post by Ivan_B on 2008-06-14
Following this tutorial: [http://www.howtoadvice.com/AutoFirestarter/](http://www.howtoadvice.com/AutoFirestarter/) , I type

"export EDITOR=gedit && sudo visudo"

and this is what happens in Terminal (not the expected outcome)

"# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
Type  :quit<Enter>  to exit Vim"

---

### Post by prshah on 2008-06-14
> **Ivan_B said:**
> This is what I get when I try to open Firestarter with Gedit:



/usr/sbin/firestarter is an executable (binary) file. You cannot open it with gedit.

---

### Post by Ivan_B on 2008-06-15
So following this tutorial:

[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

if its not the binary executable file im supposed to edit, which one am i suposed to?

EDIT: Okay stupid me. But here's a new question. That pathway does not work: /etc/sudoers, why? :(

EDIT: Okay found it, but tells me i dont have an appropriated program to open it..?

---

### Post by Ivan_B on 2008-06-15
Okay I tried opening with Gedit, but it tells me i don't hav enough privileges..wtf?

---

### Post by nikgare on 2008-06-15
What you want to do doesn't really make sense - there is no point in opening up the executable in gedit.

What do you want to do - configure the firewall?

Nik

---

### Post by Ivan_B on 2008-06-15
Yeah I'm stupid, I was trying to edit the wrong file. Here's what I'm trying to follow:

[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

I'm stuck right now because I can't open the /ect/sudoers/ file with gedit, it tells me I don't have enough permissions. :(

---

### Post by nikgare on 2008-06-15
Why don't you just run Firestarter from 

System->Adminstration->Firestarter

This runs the gui which help you set up a very basic firewall which is sufficient for most desktop users. There are other guis available via synaptic eh shorewall, ebox ...
You don't need firestarter to load automatically when you log in, it is just a gui frontend for iptables.
AFAIK iptables is started the sametime that the networking os started, so as the fiewwall will always be working when the network is up.


Nik

---

### Post by Ivan_B on 2008-06-15
Okay so what you're saying is that the firewall automatically starts when the OS is booted and that Firestarter is just a nice visual for it (GUI) that is not mandatory to protect my system?

---

### Post by nikgare on 2008-06-15
Yes!
You only have to run Firestarter (or similar program) for the config of a the firewall.

---

