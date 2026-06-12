---
title: "'halt' and 'reboot' without sudo"
date: 2007-03-24
forum: General Help
---

### Post by Mateo on 2007-03-24
First, just a general curiosity question, why is it that you need root access to use the halt and reboot commands, when you don't need root access to do the same thing from the gnome-panel menus.

Also, is it possible to give my user permission to use halt and reboot commands without using sudo?

thanks.

---

### Post by mahiyar on 2007-03-24
Give the user the rights to administer the system i.e system>administration>user settings>"name of user">properties>user privileges>administer the system. But that will make the user almost "sudo".

---

### Post by lha on 2007-03-25
> **Mateo said:**
> Also, is it possible to give my user permission to use halt and reboot commands without using sudo?

thanks.

Almost.

> **mahiyar said:**
> Give the user the rights to administer the system i.e system>administration>user settings>"name of user">properties>user privileges>administer the system. But that will make the user almost "sudo".

I consider this to be exaggeration. A much better way is to use /etc/sudoers to give users and/or groups permission to sudoing to selected commands, like halt and reboot in this case. They still need to use sudo, but they do not need to enter a password. To get finally rid of sudo, you can create a simple script in /usr/local/bin that just executes "sudo halt" when called. The file /etc/sudoers must be edited with the command 'visudo'.

---

### Post by Mateo on 2007-03-25
i don't want to make my user have all root permissions, just to use halt and reboot without sudo.

i read the sudoer man page but don't understand it.  what would i do.  thanks.

---

### Post by aysiu on 2007-03-25
I also don't understand why a regular user would have privileges to do this through the GUI but not through the terminal. Seems weird.

Here's the workaround, though.

Edit the /etc/sudoers file with this command: ```
sudo visudo
``` Then, add in these lines: ```
ALL ALL = NOPASSWD: /sbin/shutdown
ALL ALL = NOPASSWD: /sbin/halt
```

---

### Post by Mateo on 2007-03-25
do you still have to type 'sudo' before the commands that way?  it's ok if so, just curious.

---

### Post by lha on 2007-03-25
> **Mateo said:**
> do you still have to type 'sudo' before the commands that way?  it's ok if so, just curious.
Yes, you do have to.

---

### Post by Mateo on 2007-03-28
Doesn't work. I have:

```
ALL ALL = NOPASSWD: /sbin/shutdown
```

in that file and I'm still asked for the password.

---

### Post by aysiu on 2007-03-28
> **Mateo said:**
> Doesn't work. I have:

```
ALL ALL = NOPASSWD: /sbin/shutdown
```

in that file and I'm still asked for the password.
What command are you using to reboot or halt?

---

### Post by Mateo on 2007-03-28
sudo shutdown -h now

---

### Post by aysiu on 2007-03-29
Not sure why that's not working, but one of these links may help you:
[HowTo: Add a shutdown button on the desktop](http://www.ubuntuforums.org/showthread.php?p=2040896)
[How to shutdown computer with normal rights..](http://ubuntuforums.org/showthread.php?t=161230)

---

