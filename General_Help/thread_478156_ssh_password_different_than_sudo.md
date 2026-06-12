---
title: "ssh password different than sudo?"
date: 2007-06-19
forum: General Help
---

### Post by everdred on 2007-06-19
Was just wondering if there was any way to set up Ubuntu so that I could use a password other than my sudo-root one for the purposes of ssh'ing into my computer. 

While I suppose I could just enable root and use an unprivileged account for my regular user, I'd rather not, as I quite like sudo and would like to keep everything to one account. Just looking for a way to set a completely different password for ssh'ing in.

---

### Post by Bachstelze on 2007-06-19
No. Both *ssh* and *sudo* use your account. And one account has one password. What's the point of having two different passwords anyway ?

---

### Post by Kodfish on 2007-06-19
you want "ssh -l $name-to-login-as $target" were name is your name

---

### Post by Qu4k3R on 2007-06-19
I believe you can.

I would add a root-user (so you can get a new password to get root permissions) and then I would add another user (without root access), then login via SSH with that user username and password.

Then I would use sudo with that user-ssh you have created, the password would be a root-user password.

I haven't tried, but maybe this helps:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo)

It is like you login to another computer. You have you account (not root) and the root account of that computer.
If you login with a non-root accound, you can get root-access if you know root-password.

---

### Post by anaconda on 2007-06-19
I would simply add a new user, who doesn't have sudo rights.

then you can ssh to that username, and if you need sudo rights you can su to your normal user..

---

### Post by Qu4k3R on 2007-06-19
> **anaconda said:**
> I would simply add a new user, who doesn't have sudo rights.

then you can ssh to that username, and if you need sudo rights you can su to your normal user..

:D

---

### Post by everdred on 2007-11-15
Seems I forgot to enable alerts for the thread and never came back to it.

Thank you all for the responses.

---

