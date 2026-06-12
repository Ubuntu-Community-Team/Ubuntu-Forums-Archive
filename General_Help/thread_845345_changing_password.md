---
title: "changing password"
date: 2008-06-30
forum: General Help
---

### Post by gandalf458 on 2008-06-30
I recently changed the root password using

sudo passwd

but when I tried to change it again, the change appeared to be accepted but when I'm asked for the password it still only accepts the old password.

Any clues what's wrong please?

---

### Post by russlar on 2008-06-30
Apparently root is taboo 'round these parts, but I'll help you anyway. Are you getting prompted for a password at su or sudo? I've found that su prompts for the root passwd, but sudo prompts for your (the normal, non-root) user passwd.

---

### Post by gandalf458 on 2008-06-30
> **russlar said:**
> Apparently root is taboo 'round these parts, but I'll help you anyway.
Oops, sorry if I've posted in the wrong place - thanks for your help

> Are you getting prompted for a password at su or sudo? I've found that su prompts for the root passwd, but sudo prompts for your (the normal, non-root) user passwd.
In terminal when I enter sudo passwd I'm asked for my password, then I'm asked for the new Unix password (twice) and I'm informed the password has successfully been changed.

---

### Post by pmlxuser on 2008-06-30
just do passwd withou the sudo and then it will change completly.
then when you do sudo somthing the new password will be used as in all normal cases.

---

### Post by gandalf458 on 2008-06-30
Oh - I thought I had to use sudo. I didn't think I could change root password from a user log in.

Thanks G :)

---

### Post by chrisccoulson on 2008-06-30
I think you're confused. 'passwd' will change the password of the user who ran it (unless you specify a user). So, if you just run 'passwd', then it will change your own user password - that is all you're allowed to change. If you run 'sudo passwd', then it will change (or set) the root users password. However, the root account is disabled by default. The password you specify when using 'sudo' is your own user password, and not the root password.

---

### Post by gandalf458 on 2008-06-30
In that case I go back to my original question. I have managed to change the root password once but it doesn't seem to allow to change it again...

---

### Post by chrisccoulson on 2008-06-30
The root account is disabled by default. What are you having issues with? Under what circumstances are you being asked for the root password? You should never get asked for a root password unless you are specifically trying to [log in as the root user]("http://ubuntuforums.org/showthread.php?t=765414"). If you're talking about the password you use when prompted by sudo or any other administrative application, then this is just the same as your normal login password.

Have a look at [this]("https://help.ubuntu.com/community/RootSudo") for further explanation
> By default, the root account password is locked in Ubuntu. This means that you cannot login as root directly or use the su command to become the root user, however, since the root account physically exists it is still possible to run programs with root-level privileges. This is where sudo comes in; it allows authorized users (normally "Administrative" users; for further information please refer to AddUsersHowto) to run certain programs as root without having to know the root password.

This means that in the terminal you should use sudo for commands that require root privileges; simply prepend "sudo" to all the commands you would normally run as root. For more extensive usage examples, please see below. Similarly, when you run GUI programs that require root privileges (e.g. the network configuration applet), you will also be prompted for a password. Just remember, when sudo asks for a password, it needs **YOUR USER Password**, and not the root account password. 

---

### Post by chrisccoulson on 2008-06-30
> **russlar said:**
> Apparently root is taboo 'round these parts, but I'll help you anyway. Are you getting prompted for a password at su or sudo? I've found that su prompts for the root passwd, but sudo prompts for your (the normal, non-root) user passwd.

You're correct, 'su' will prompt for a root password. Because the root account is locked and there is no password, then you cannot use 'su' to get a root shell. To get a root shell:
```
sudo -s -H
```
The '-s' runs a shell and '-H' sets the HOME environmental variable to root. This is important, as without it, some utilities that you execute as root may overwrite preferences in your home folder with files that are owned by root and not writable by you.

---

### Post by gandalf458 on 2008-06-30
I AM confused now! I can't find where I am being asked for the root password.

---

### Post by chrisccoulson on 2008-06-30
> **gandalf458 said:**
> I AM confused now! I can't find where I am being asked for the root password.

Me too! Lol!

It should be nowhere, unless you are specifically trying to log in as the root user.

---

### Post by Gunman1982 on 2008-06-30
When you log in and you type in root instead of your normal username, thats where you need your root password. I still recommend that you don't do it, it messes more things up than it really solves, especially if you use it in the graphical login.

Just stick to sudo/gksu.

---

### Post by gandalf458 on 2008-06-30
Thanks guys!

---

