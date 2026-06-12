---
title: "No password sudo"
date: 2006-12-24
forum: General Help
---

### Post by Sevoma on 2006-12-24
I would like to know what to add in the sudoers file with visudo to be able to use sudo/gksudo without being prompted for the password. I know of the risks; I am the sole user of the machine and I am willing to take them. Also, is there any way for it to take effect without a restart?

---

### Post by fragos on 2006-12-24
Perhaps you're new to Ubuntu.  I made the switch to Ubuntu from SuSE and at first found the sudo thing a bit wierd.  Noe that I'm used to it I'm no longer bothered.  Ubuntu only requires the password on a the first sudo.  Theirs a timer on it and it won't berequested again for a while.  You still neeed to enter sudo before the command.  I've added a Nautilus script which opens files as administrator which frequently means I don't have to go to the command line for priviledged access.  I vertualy never have to use gksudo ever.

---

### Post by Sevoma on 2006-12-26
I am not new to sudo. I have been using Ubuntu for over a year. I just want to set sudo so that it does not require a password ever. I am the only user and I know the security risks.

---

### Post by bodhi.zazen on 2006-12-26
In a terminal type sudo visudo

Add this line:

> %admin ALL=(ALL) NOPASSWD: ALL

---

### Post by fragos on 2006-12-26
> **bodhi.zazen said:**
> In a terminal type sudo visudo

Add this line:

That looks like a solution but you might want to limit to you and not all just in case.  Given the command, I would think that there's a way to do that.

---

