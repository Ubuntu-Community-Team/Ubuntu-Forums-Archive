---
title: "run rfkill without special permissions"
date: 2013-03-10
forum: General Help
---

### Post by Binary-Synapse on 2013-03-10
Hello.

I have an Ubuntu 12.04LTS system on which I would like to run the following commands without sudo prefix, or elevated permissions:

rfkill is currently installed, and I can issue commands like "rfkill list all" without sudo prefix or elevated permissions (just the way I want).

But even so, I cannot issue the following commands:
rfkill block wifi
rfkill unblock wifi

I can only issue them if I use the sudo prefix (which I don't wan't to type).

Notes:
1 - rfkill is installed in /usr/sbin/rfkill 

2 - My $PATH is currently like this:
```
/usr/local/bin:/usr/bin:/usr/sbin:/bin:/usr/local/games:/usr/games
```

3 - sudoers is currently like this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults   env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root   ALL=(ALL) ALL

# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
john ALL=NOPASSWD:/usr/sbin/rfkill
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d
```

Can someone help?

Thank you

---

### Post by Nr90 on 2013-03-10
I guess you could create a bash alias

---

### Post by Cheesemill on 2013-03-10
The order of lines in a sudoers file is very important.

At the moment your rfkill line states that you want to be able to run 'sudo rfkill' without entering a password, but this behaviour is then being overwritten by the next line which states that anyone in the sudo group can use sudo, but they have to enter a password.

Move your rfkill line to the bottom of the sudoers file and you should get the behaviour you're after.

Also bear in mind that this entry in the sudoers file won't mean that you can run rfkill without using sudo. You will still have to use the command 'sudo rfkill' you just won't be prompted for a password.

Edit - Also I think you are missing a space in your rfkill line, it should read...
```
john ALL=NOPASSWD: /usr/sbin/rfkill
```

---

### Post by Binary-Synapse on 2013-03-10
Hello Cheesemill.

The entry order has been corrected, like this:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root  ALL=(ALL) ALL

# Allow members of group sudo to execute any command
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
john ALL=NOPASSWD: /usr/sbin/rfkill

#includedir /etc/sudoers.d
```

Like you said it runs without asking me for a password, if I run it like this:
sudo rfkill block wifi

But if I run it like this:
rfkill block wifi
It returns:
```
Can't open RFKILL control device: Permission denied
```


But surely there must be a way to bypass this, right?
I need to run that command without "sudo" prefix.

---

### Post by Cheesemill on 2013-03-10
The rfkill command needs low-level access to your networking hardware so no, it can't be run without sudo.

You could always add an alias to your ~/.bashrc file, for example...
```
alias rfkill='sudo rfkill'
```

This way whenever you issue the command 'rfkill' the actual command being run would be 'sudo rfkill'.

---

### Post by mikewhatever on 2013-03-10
Add the following to the .bashrc file in your home folder:

```
alias rfkill='sudo rfkill'
```

Save and exit, then tun **source .bashrc** to reload. Now 'rfkill' will mean 'sudo rfkill' when you run it.

---

### Post by Binary-Synapse on 2013-03-10
It worked perfectly with the alias!

Thank you all for helping me out.

Regards...

---

### Post by Binary-Synapse on 2013-03-11
Hello.


Sorry for reopening this, but... just to have a better grasp of things...

> The rfkill command needs low-level access to your networking hardware so no, it can't be run without sudo.

Are you sure?

I also have a Debian 7.0 system and I now noticed that it doesn't require sudo prefix.
I can issue the command:
rfkill block wifi

And in Debian it works prefectly. It doesn't require a password, and I don't even need the sudo prefix!
But I dont know where the difference is (sudoers, permissions, etc... are equal in both OS).

Could it be something else in the OS?

---

### Post by Binary-Synapse on 2013-03-12
Well... I don't care.
The bash alias worked perfectly, so I will leave the rest for the experts :)
Thank you!

---

