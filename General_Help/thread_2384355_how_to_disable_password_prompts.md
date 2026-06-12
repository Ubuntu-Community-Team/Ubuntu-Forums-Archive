---
title: "how to disable password prompts"
date: 2018-02-06
forum: General Help
---

### Post by christon74 on 2018-02-06
Good morning again fellow Ubunters:)

I am the only person living here in this small flat, and of course, I am the only one who uses this computer. And I have always considered password prompts as slightly unnerving. Why should I need a password when I have almost no concern about privacy?
So I have tried to remove all password prompts by editing the sudoers file  (sudo visudo). And again, I boobed and must have completely muddled up things, because when I checked if I had indeed removed the password, here is what the terminal window returned: 

```
christophe@christophe-ESPRIMO-E5731:~$ sudo visudo
>>> /etc/sudoers: syntax error near line 27 <<<
sudo: parse error in /etc/sudoers near line 27
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin
christophe@christophe-ESPRIMO-E5731:~$ sudo su
>>> /etc/sudoers: syntax error near line 27 <<<
sudo: parse error in /etc/sudoers near line 27
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin
christophe@christophe-ESPRIMO-E5731:~$ 
```

Ouch! How do I put things back in right order now?

---

### Post by TheFu on 2018-02-06
Boot from a live-CD/flash drive, mount the storage, edit the file (correctly this time) and reboot back into the normal system.

visudo is pretty clear when it doesn't like something. It provides a warning, which should be fixed.

Putting the version of the file back from a backup would be easiest, BTW.

If you use LVM and/or encryption (LUKS/dm-crypt), then things are a little harder.

---

### Post by sisco311 on 2018-02-06
You can use pkexec:
```
pkexec visudo
```

This is the content of the default sudoers file:
```
#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset
Defaults	mail_badpass
Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
```

---

### Post by HermanAB on 2018-02-06
The problem is that although you are the only keyboard user, other services can potentially connect to your computer over the network.  In that case, the password system is a basic line of defense.  Linux systems are valuable for spammers and other malware operators, since they are usually good quality and on decent network connections.  A computer without passwords will eventually fall victim to malware.

---

### Post by christon74 on 2018-02-07
Hello HermanAB, Sisco and TheFu, good morning:)
Herman, are you serious, can somebody else take control of your computer from a distant place? 
Well, alright then, I am changing my password.

---

### Post by TheFu on 2018-02-07
Any computing device that has networking can be taken control over remotely by a number of different methods.  If you don't run any network services on the machine, then tricking the user into doing something, like opening a webpage or email is usually necessary on Linux.  On Windows, there have been successful attacks by just getting someone to view an image file or icon.

After the attacker gets in, if there isn't a sudo passphrase required, they own the machine, completely.  You can solve this by creating a different account that doesn't have sudo permissions and using that all the time. It is a good security practice.

I find having ssh access to all my linux systems very handy, indispensable, so it isn't in my thought process NOT to have sshd running and secured on each machine.  Not all of my systems are directly available on the internet, but they are just 1 ssh hop away from a system that is.  ssh is an amazing tool with some pretty great capabilities.

---

### Post by christon74 on 2018-02-08
Hello Herman.OK. I have never even tried to have distant access to my own PC. (using a smart phone?) I only have an old hp laptop (or notebook) hp nc 4200 and a not so old Fujitsu-Siemens. Anyway, I have successfully changed my too short password and the one I have set is deemed "fair".

---

