---
title: "Lost password to su command"
date: 2013-01-09
forum: General Help
---

### Post by ruwan2 on 2013-01-09
Hi,
I install Ubuntu 12 in my desktop PC. I did not set up account password. There is no login asking me each time turn on the computer. But there is a password every time I run to su in a terminal.  I remember that yesterday I can enter my long time using password for su command.

Today I cannot enter su in the terminal. It is not like I misremember the password. I have tried to recover account password after entering the recover mode. I run 
ls /home 
command in a terminal. There is no account info echoed.

Now, I have no idea what my su password is, or how to reset that password.

It is really bizarre to me. I do not thing I use other password in this Ubuntu PC.

Could you help me to enter su?

Thanks a lot.

---

### Post by Wim Sturkenboom on 2013-01-09
_su_ will prompt your for the root password (if no username is specified); in ubuntu (and a number of other distros), the root account as such is disabled so you can't log in as root. You need to use _sudo_ (e.g. _sudo -i_)and provide your normal user password.

---

### Post by grahammechanical on 2013-01-09
When we install Ubuntu we are required to give a user name and password. We are also given the option to log in to Ubuntu automatically. If we choose that option Ubuntu will load straight to the desktop. We will not get a log in screen.

But that user name and password will still be important. We will be using Ubuntu as a standard user. When we try to do anything that requires administrator privileges then we will be asked to authenticate. That is when we enter the password.

We do not use su in Ubuntu. If a command requires administrator privileges then we prefix the command with sudo and we are asked to enter our password. The administator privileges expire when the task is complete or  few minutes have passed by.

This explains the use of sudo in Ubuntu

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Regards.

---

