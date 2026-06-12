---
title: "What's the root password after install?"
date: 2007-04-21
forum: General Help
---

### Post by dahouse on 2007-04-21
Hey guys,

I just converted to Kunbuntu after a very unfruitful flirtation with Gentoo. 

My question is as follows: I'm trying to gain super user access. When I installed Kubuntu, it asked me for a password and I used the same one I generally do. On my first login, I used it and it was great. When I'm using a terminal and use the SU command, what is the password needed? I mean, I used the one I entered during the installation and apparently, it's not the right one.

Can anybody clear this up for me?

---

### Post by kodoku on 2007-04-21
it should be the same thing..

do you get something like "su: authentication error"?

That's what I get when I try to su.

I'd say just stick with sudo

---

### Post by dahouse on 2007-04-21
welll I tried the same password but to no avail...

---

### Post by jubxie on 2007-04-21
i beleve you need to create one. 

"sudo passwd root" is how I do it.

---

### Post by BrokeBody on 2007-04-21
Type this in Konsole:

```

sudo passwd

```

The first time, you will enter your password. The second time, you will enter desired root password, and third time, you will have to reenter your new root password.

Afcourse, you can simply enter your password all three times, if you want root password to be same as your password. :p

---

### Post by kodoku on 2007-04-21
It seems like (k)ubuntu doesn't really like su.  It works with sudo right?

[Edit] Nevermind, I'm dumb.

---

### Post by dreadlord_chris on 2007-04-22
> **dahouse said:**
> Hey guys,

I just converted to Kunbuntu after a very unfruitful flirtation with Gentoo. 

My question is as follows: I'm trying to gain super user access. When I installed Kubuntu, it asked me for a password and I used the same one I generally do. On my first login, I used it and it was great. When I'm using a terminal and use the SU command, what is the password needed? I mean, I used the one I entered during the installation and apparently, it's not the right one.

Can anybody clear this up for me?

The security model for Ubuntu works a little differently than many other Linux distros
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)  << explains the Ubuntu way....

---

### Post by dahouse on 2007-04-22
thanks a millions guys.

I like su...

---

