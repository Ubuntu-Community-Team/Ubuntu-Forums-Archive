---
title: "How to install program with sudo"
date: 2008-06-05
forum: General Help
---

### Post by mbirkett on 2008-06-05
I recently went to the ATI website to download some drivers for my graphics card, i downloaded it and tried to install it but it tells me i need su privleges. i know how to bring up the x terminal but i do not know hot to install from it or navigate to the desktop path name, anyhelp is good help
mike

---

### Post by Het Irv on 2008-06-05
One extremely easy way to run a program as sudo in the terminal is to type sudo and then drag and drop the file into the terminal.

The standed way to run it would be:
```
cd ~/Desktop
sudo 'program'
```

~/ is the equivaliant of typing /home/'name'

---

### Post by mbirkett on 2008-06-05
I opened the x terminal and typed sudo and then draged the program installer in the x terminal, everything starts to load up and look good then i get the "need super user priv" error

---

### Post by Sealbhach on 2008-06-05
Try

sudo su


.

---

### Post by mbirkett on 2008-06-05
hey the sudo su worked thank you i really appreciate the help
mike

---

### Post by tedrogers on 2008-06-05
Or run as root terminal. I think this will work.

```
gksu /usr/bin/x-terminal-emulator
```

You can do a lot of damage in here though, so be careful with what you type.

---

### Post by bodhi.zazen on 2008-06-05
> **Sealbhach said:**
> Try

sudo su


.

```
sudo -i
```

---

### Post by Sealbhach on 2008-06-06
> **bodhi.zazen said:**
> ```
sudo -i
```

Just wondering...

is that the same command as "sudo su" or is there a difference?


.

---

### Post by bodhi.zazen on 2008-06-06
> **Sealbhach said:**
> Just wondering...

is that the same command as "sudo su" or is there a difference?


.

There is a very minor difference, although the effect is the same, ie a root shell.

sudo -i == running sudo with the -i flag (or option).

man sudo :
> The -i (simulate initial login) option runs the shell specified in the passwd(5) entry of the user that the command is being run as. The command name argument given to the shell begins with a `-' to tell the shell to run as a login shell. sudo attempts to change to that user's home directory before running the shell. It also initializes the environment, leaving TERM unchanged, setting HOME, SHELL, USER, LOGNAME, and PATH, and unsetting all other environment variables. Note that because the shell to use is determined before the sudoers file is parsed, a runas_default setting in sudoers will specify the user to run the shell as but will not affect which shell is actually run.

=================

sudo su == use sudo to run the command su, or switch user.

man su > su is used to become another user during a login session. Invoked without a username, su defaults to becoming the super user.

... <clip> ...

The current environment is passed to the new shell. The value of $PATH is reset to /bin:/usr/bin for normal users, or /sbin:/bin:/usr/sbin:/usr/bin for the super user.

==================

I prefer sudo -i is preferable as it simulate a log-in shell and sets environmental variables ($HOME , $SHELL, etc) to root (rather then your user).

I came form a rpm system and sudo took an adjustment (usually people who sudo su are more familiar with su). sudo -i is similar to su -

---

