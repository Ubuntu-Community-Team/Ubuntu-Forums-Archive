---
title: "Usernames without passwords"
date: 2007-12-27
forum: General Help
---

### Post by apastuszak on 2007-12-27
I have an Ubuntu Desktop computer running Gutsy.  My children use it to go to sites like pbskids.org and webkinz.com.  Though the 6 year old has no issues typing in his password, the 4 year old gets very frustrated and always needs help.

Is it possible to create a limited user account without a password in Ubuntu?  I know the better option for security is to give him a password, but if I make a simple password that anyone can guess, how is that really any better than a blank password?

Andy

---

### Post by p_quarles on 2007-12-27
I believe you can just use the administration tools to enable autologin for certain users. The details are discussed in this thread:
[http://ubuntuforums.org/showthread.php?t=453439](http://ubuntuforums.org/showthread.php?t=453439)

---

### Post by wh0rd on 2007-12-27
I don't think he means autologin. What I'm understanding is a request to have a user name similar to Windows XP's Guest login feature. Here's a dirty hack to get that working for any user:

[http://ubuntucat.wordpress.com/2007/07/31/creating-a-passwordless-account-in-ubuntu/](http://ubuntucat.wordpress.com/2007/07/31/creating-a-passwordless-account-in-ubuntu/)

---

### Post by oscarsfriend on 2007-12-27
I don't know about GNOME, but certainly KDE (using kdm login manager) allows for passwordless logins.  I know because I use it.  All the accounts I have set up to use this still have passwords (e.g. still need to type it in to unlock screen).  There is also a nice kubuntu theme for KDM that allows you to click an icon to login, from a list of icons for each user -- I have this combined with passwordless login on the family machine.

---

### Post by p_quarles on 2007-12-27
> **oscarsfriend said:**
> I don't know about GNOME, but certainly KDE (using kdm login manager) allows for passwordless logins.  I know because I use it.  All the accounts I have set up to use this still have passwords (e.g. still need to type it in to unlock screen).  There is also a nice kubuntu theme for KDM that allows you to click an icon to login, from a list of icons for each user -- I have this combined with passwordless login on the family machine.
Gnome can't do that by default, which is why I suggested autologin -- that may work just as well for these purposes. 

The link to aysiu's blog will also work, though, and I have to say that's a pretty clever hack.

---

