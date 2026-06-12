---
title: "Root Password"
date: 2007-11-26
forum: General Help
---

### Post by mcedata on 2007-11-26
I've just installed (er, re-installed) Ubuntu. As the install started, I was asked for a username and a password, which I entered.  Once the install was complete, I tried to su to root, but the password was rejected. Is that password entered when you're asked for username and password also the root password? If not, how would I go about setting up a root password...or getting into root?
Thanks,

mcedata

---

### Post by PeterJS on 2007-11-26
Ubuntu does not set a root password by default, most things can be done through sudo, so it's not really needed. But if you really want to set up a root password you can run sudo passwd to set the root password.

---

### Post by anaconda on 2007-11-26
root password is disabled in ubuntu by default.(security reasons) use "sudo su" instead of "su" if you want to became root..

If you know what you are doing you can alse enable root user by giving root a password with:
sudo passwd

Your sudo password is the same as your password..

---

### Post by dabl on 2007-11-26
Here's what you need to understand:

[http://kubuntuforums.net/forums/index.php?topic=3089088.0](http://kubuntuforums.net/forums/index.php?topic=3089088.0)

:)

---

### Post by aysiu on 2007-11-26
Why don't you explain what you think you need a root account for? And then we can explain a better way to accomplish that task.

---

### Post by knutschr on 2007-11-26
Be aware that to be root in other ways than the sudo method is a secure way of screwing up your system unless you are absolutely sure of what you do!

---

### Post by mcedata on 2007-11-27
> **knutschr said:**
> Be aware that to be root in other ways than the sudo method is a secure way of screwing up your system unless you are absolutely sure of what you do!

Yeah, umm (blush)...found that out. <g>

Thanks, guys, for the help...it worked as usual. 

mcedata

---

