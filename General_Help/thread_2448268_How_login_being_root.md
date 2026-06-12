---
title: "How login being root ?"
date: 2020-08-05
forum: General Help
---

### Post by aug7744 on 2020-08-05
I has software that need login being root to be installed.
How login being root ?

---

### Post by maglin2 on 2020-08-05
[https://ubuntuforums.org/showthread.php?t=1486138](https://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by pbear42 on 2020-08-05
Consistent with the linked thread, you're premise is faulty.  You don't need to (and shouldn't) log in as root to install software.

The usual (and correct) method is simple: sudo apt install <commandname>.  

Sudo = root authority.  Requires your password.  Only works if you are member of the sudo group, which is the important thing.

---

### Post by aug7744 on 2020-08-13
"Sudo = root authority.  Requires your password.  Only works if you are member of the sudo group, which is the important thing."
How add my username in sudo group ?

---

### Post by CelticWarrior on 2020-08-13
> **aug7744 said:**
> 
How add my username in sudo group ?

You don't need to do that. The first configured user in the installation process is automatically in the group. Likewise, that user's password is the one you need for "sudo".

Do you need to add **another user** to sudoers? I don't think so but you tell us... IMO, this question betrays a false assumption that somehow you need to login as root. The Ubuntu's security model is explained here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Quoting:

> **By default, the root account password is locked in Ubuntu.**[COLOR=#333333][FONT=Ubuntu] This means that you cannot login as root directly or use the [/FONT][/COLOR]su[COLOR=#333333][FONT=Ubuntu] command to become the root user. However, since the root account physically exists it is still possible to run programs with root-level privileges. This is where [/FONT][/COLOR]sudo[COLOR=#333333][FONT=Ubuntu] comes in - it allows authorized users (normally "Administrative" users; for further information please refer to [/FONT][/COLOR][AddUsersHowto]("https://help.ubuntu.com/community/AddUsersHowto")[COLOR=#333333][FONT=Ubuntu]) to run certain programs as root without having to know the root password.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]This means that in the [/FONT][/COLOR][terminal]("https://help.ubuntu.com/community/UsingTheTerminal")[COLOR=#333333][FONT=Ubuntu] you should use sudo for commands that require root privileges; simply prepend [/FONT][/COLOR]sudo[COLOR=#333333][FONT=Ubuntu] to all the commands you need to run as root. For more extensive usage examples, please see below. Similarly, when you run GUI programs that require root privileges (e.g. the network configuration applet), use graphical sudo and you will also be prompted for a password (more below). Just remember, when sudo asks for a password, it needs [/FONT][/COLOR]**YOUR USER password**[COLOR=#333333][FONT=Ubuntu], and not the root account password.[/FONT][/COLOR]

---

