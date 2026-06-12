---
title: "sudo vs su"
date: 2007-12-19
forum: General Help
---

### Post by dennis grollo on 2007-12-19
Is there a way to have Ubuntu use the Debian su and su - instead of the sudo command.
I guess I have always used su and sudo seems a bit cumbersome.
I have tried to search  the web and forums but do not find any info regarding this. I have always gone on the assumption that with linux if the user knows how just about anything is possible.
Thanks

---

### Post by bernied on 2007-12-19
In my experience, all you have to do is give the root user a password. The root account is already there. So just do this:
```
sudo passwd
```
The first request for a password is asking for your normal user password, the next is the new root password, then a repeat of the root password, for verification.

---

### Post by scxtt on 2007-12-19
there's no real sense in giving the "root" account a password ... just do something like **sudo su -** or **sudo -s** and you'll be root for as long as you need ...

fact of the matter is, why make another password to remember (even if your sudo access user and root p/w are the same) -- you still have to enter it once, so why not just use a p/w that's already in place ...

i guess there's the "i want to login to a GUI as root" crowd ... anyone who "needs" to use root that much would already know why it isn't necessary (or a great idea) ...

for all those individuals who say "1st thing i do is enable the root account", well the 1st thing i do w/ a distro that uses "root" is setup sudo :-p

---

### Post by LaRoza on 2007-12-19
The Ubuntu wiki address sudo: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Whiffle on 2007-12-19
```

sudo passwd root

```

will allow you to set a password for root.  Its the first thing I do on an ubuntu system, sudo is really annoying.

---

