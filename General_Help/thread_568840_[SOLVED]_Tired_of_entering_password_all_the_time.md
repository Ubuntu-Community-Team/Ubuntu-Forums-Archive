---
title: "[SOLVED] Tired of entering password all the time"
date: 2007-10-06
forum: General Help
---

### Post by Sockerdrickan on 2007-10-06
Hi where do I change the value for how many minutes should pass by without using something as sudo before I have to enter the password again?

---

### Post by HermanAB on 2007-10-06
Try 'sudo -i'.  Otherwise see /etc/sudoers.

Cheers,

Herman

---

### Post by Happy_Man on 2007-10-06
It's in the file /etc/sudoers. EDIT THE FILE WITH EXTREEEEME CAUTION.

---

### Post by yuku-aki on 2007-10-06
You could just enable your root account and use it the original way.

When you're doing lots of things that require sudo and a password, it's nice to be able to just log in as root in a terminal (su, then the password you use for sudo).  You can start applications from there just by typing their name, usually.

Then when you want to logout, you just enter "exit" or alt+F4 the window, and you're no longer root!

Text from:  [http://linuxpoison.wordpress.com/2007/09/24/how-to-enable-the-root-account-in-ubuntu/](http://linuxpoison.wordpress.com/2007/09/24/how-to-enable-the-root-account-in-ubuntu/)

How to enable the root account in Ubuntu
September 24th, 2007 &#8212; Nikesh

As you have noticed during the Ubuntu installation there was no question about the root password, as you might have been used to see during other Linux distribution installation process. This is why the root account is inactive and can&#8217;t be used (no password configured) until we will setup a proper password for it. To do this, we simply need to run:

sudo passwd root

This will ask for a new root password and once you confirm it, you can start using the root account to login.

In case you will want to disable back the root account, just lock the root account by running:

sudo passwd -l root

---

### Post by aysiu on 2007-10-06
Another vote for ```
sudo -i
``` The other methods are way too much trouble (manually editing /etc/sudoers or enabling the root account) by comparison.

---

### Post by Sockerdrickan on 2007-10-06
Ok nice :D

---

### Post by leg on 2007-10-06
Why not just sudo su and keep the terminal open as long as you need it.

---

### Post by aysiu on 2007-10-06
> **leg said:**
> Why not just sudo su and keep the terminal open as long as you need it.
That's essentially the same as ```
sudo -i
```

---

### Post by RedSquirrel on 2007-10-06
In my opinion,

```
sudo -i
```is preferable because that will give you root's environment. From the sudo man page, for the '-i' option:

> sudo attempts to change to that user’s home directory before running the shell.  It also initializes the environment, leaving TERM unchanged, setting HOME, SHELL, USER, LOGNAME, and PATH, and unsetting all other environment variables...


At the end of the day, I just stick with the conventional way of doing things with sudo. It takes some getting use to but I'm pretty comfortable with it now. ;)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Sockerdrickan on 2007-10-07
Yes the sudo -i seems like the best :D

---

