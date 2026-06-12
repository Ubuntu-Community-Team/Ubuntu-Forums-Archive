---
title: "How to Make It Where I No Longer Need To Type Sudo"
date: 2015-12-23
forum: General Help
---

### Post by Darth4212 on 2015-12-23
I am currently running Ubuntu 15.10 Wily Werewolf and tend to use the terminal alot and having to constantly type ```
sudo
``` before certain commands. Is there a program that makes it where I no longer need to type it. Or is there some command to run in the terminal if so list all of the commands.

---

### Post by egeezer on 2015-12-23
sudo -i

---

### Post by Darth4212 on 2015-12-23
wait does this make it only for that terminal session or is it applied forever?

---

### Post by deadflowr on 2015-12-23
sudo -i only works for the length of the terminal session, or when you exit sudo -i.

Two things to be aware of:
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
and
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by egeezer on 2015-12-23
Your choice - you can Exit back to normal user status any time in that session, or leave it running in the background until you restart/shutdown/logout.

---

### Post by kurt18947 on 2015-12-23
Is this for one program or multiple? I had one program that I used frequently as a desktop user. The program required sudo privileges so I had to switch users, type the command using sudo then switch back. What a pain. I found a way to run that one program as an unprivileged user. I can't find the instructions I used but this may give you an idea:

[https://unix.stackexchange.com/questions/18830/how-to-run-a-specific-program-as-root-without-a-password-prompt](https://unix.stackexchange.com/questions/18830/how-to-run-a-specific-program-as-root-without-a-password-prompt)

---

### Post by leunam12 on 2015-12-24
Why don't you want to type sudo? it's only four letters. The only way to do what you request is to be logged in a s root all the time (not recommended). You can change your sudoers file so you don't have to enter a password anymore or buy a fingerprint scanner (cheap) if the problem is typing your password.

---

### Post by buzzingrobot on 2015-12-24
> **kurt18947 said:**
> Is this for one program or multiple? 

"sudo -i" effects that terminal session.  Anything you execute in that terminal after that will execute with raised privileges. Which is worth remembering.

> I had one program that I used frequently as a desktop user. The program required sudo privileges so I had to switch users, type the command using sudo then switch back...

The default user created by the installer can use "sudo".

---

### Post by Darth4212 on 2015-12-26
I just want to know if there is a way.

Or is there a way to make it where I can type something other than sudo but it has the same effect?

---

### Post by pqwoerituytrueiwoq on 2015-12-26
alias can do that
```
echo "alias admin='sudo'" >> ~/.bashrc
```
that will make it so you can type [FONT=courier new]admin apt-get install life[/FONT]

---

