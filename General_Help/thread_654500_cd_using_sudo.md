---
title: "cd using sudo"
date: 2007-12-31
forum: General Help
---

### Post by jrz on 2007-12-31
Helping a friend, we cd'd to /etc and tried to cd to firestarter which we could not and ls -la displayed it's permissions as 700, so we ttried to 'sudo cd firestarter' and received the following response:
sudo:  cd:  cd cannot be found
Any explanation as to why?

A get around 'sudo -s' allowing us to become root permits cd to be found and allows us to 'cd firestarter'.

---

### Post by ray bot on 2007-12-31
When you use sudo, you temporarily become root for that one command, but you go right back to being yourself afterwards.  Using sudo cd to enter a directory that your normal user account is not allowed to access would cause problems, because as soon as you would go into that directory, you'd no longer have permission to be there.

---

### Post by jrz on 2007-12-31
We appear to retain root permissions for a length of time after the initial sudo, allowing us to continue sudoing commands without need of the password. I would expect to be able to access the directory but not be able to do anything further without using sudo each time. Are you certain this is meant to be this way? We wished to make a backup of a file within that directory prior to making any changes to it from a new firestarter installation.

Just to confirm what you say I will try doing a 'sudo ed /etc/firestarter/{filename}' next time I have access to the computer. If you're correct that should give an explanation of how to accomplish what we wish to do.

---

### Post by zvacet on 2007-12-31
You will become root by typing in terminal

```
sudo -i
```

and if you want to change permissions read [this](https://help.ubuntu.com/community/FilePermissions).
Make copy of that file(folder) just in case.

---

### Post by mcduck on 2007-12-31
> **jrz said:**
> We appear to retain root permissions for a length of time after the initial sudo, allowing us to continue sudoing commands without need of the password. I would expect to be able to access the directory but not be able to do anything further without using sudo each time. Are you certain this is meant to be this way? We wished to make a backup of a file within that directory prior to making any changes to it from a new firestarter installation.

Just to confirm what you say I will try doing a 'sudo ed /etc/firestarter/{filename}' next time I have access to the computer. If you're correct that should give an explanation of how to accomplish what we wish to do.

You don't actually get root permissions for any longer than what it takes to execute the command that had 'sudo' in it.

Sudo remembers your password for 15 minutes so you don't have to type it again, but you are still running with your normal user's permissions, not root's, and you need to still add 'sudo' to every command that needs root permissions.

---

### Post by geirha on 2007-12-31
cd is not an executable, it's a shell builtin. sudo requires an executable to run, but there's no cd in /bin or /usr/bin or wherever, so you definantely need a root shell to cd into a directory only root has access to.

```

$ type -a cd
cd is a shell builtin
$ type -a echo
echo is a shell builtin
echo is /bin/echo

```

---

