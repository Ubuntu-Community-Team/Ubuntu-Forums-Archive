---
title: "[SOLVED] What is the default root Password?"
date: 2007-08-03
forum: General Help
---

### Post by Super TWiT on 2007-08-03
I was just wondering out of curiosity what the default root password is?  I know that if you type sudo in front of a command it would run it as root and that the password is your user password.  However, when I clicked on User and Groups I noticed that root was listed and I clicked on the profile.  I noticed that a password was already set and I have never set the root password before.  I am wondering what this password is and if someone knew this password would they have root user access?:confused:

---

### Post by badmadrabbit on 2007-08-03
Interesting question :D 

I tried su root but it's not the same as su sudo, you need to type in a password but it's not the user's password. Whereas sudo su and sudo su root is exactly the same.

I would guess there is not such a password....would be a flawless security hole if every Ubuntu installation could be accessed with the same root password ;-) :)

---

### Post by prodezigner on 2007-08-03
The default root password is *drumroll*... nothing. There isn't one.

SU and SUDO are two different command, SU lets you RUN as root for the session, SUDO is a temporary root.

If you try to SU, and use your password, you'll be denied. Because there isn't one defined.

To SET the root password click on System->Administration->Users and Groups->click on root->click Properties->AT THE BOTTOM... set your password manually, and confirm it. After you click OK reboot your system *not really needed, but just to make sure*.

Enjoy, hope this helped! :D

---

### Post by Total_Biscuit on 2007-08-03
> **Super TWiT said:**
> I was just wondering out of curiosity what the default root password is?  I know that if you type sudo in front of a command it would run it as root and that the password is your user password.  However, when I clicked on User and Groups I noticed that root was listed and I clicked on the profile.  I noticed that a password was already set and I have never set the root password before.  I am wondering what this password is and if someone knew this password wou ld they have root user access?:confused:
Coo, that question gets asked a lot in this forum (I just did a search).  The root account is disabled by default in Ubuntu so, despite the dots that appear in root's Users and Groups properties, there is no root password.  Take a look at root's entry in /etc/shadow to prove to yourself that there is no root password.

---

### Post by prodezigner on 2007-08-03
On a side note...

Use a strong root password, capital letters and numbers if ya wanna be UBER secure.

---

### Post by Super TWiT on 2007-08-03
That answers my question!  Thank you everybody who responded!:KS  This is just another example of how wonderful this community is!

---

### Post by rshields on 2007-08-03
There is an easier way. Type "sudo su" and enter your password. You are now root. Type "passwd" to set a password for root.

The reason it's not set is that there's no need to be root. You can do everything you need with sudo,

---

