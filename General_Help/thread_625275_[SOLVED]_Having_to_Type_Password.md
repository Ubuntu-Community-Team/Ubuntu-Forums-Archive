---
title: "[SOLVED] Having to Type Password"
date: 2007-11-27
forum: General Help
---

### Post by Sam Plamondon on 2007-11-27
In Ubuntu 7.10, is there a way to stop from having to type in your administrative password to do administrative tasks while logged in as a user?  I am the only person who uses my computer, and I have no need for this extra little security.  It is just a little annoying.  I would rather just have to type in my password once, at the login screen.

---

### Post by Takster on 2007-11-27
maybe this will help.
[https://help.ubuntu.com/community/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d](https://help.ubuntu.com/community/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d)

---

### Post by Sam Plamondon on 2007-11-27
Interesting... this does not get rid of my problem, but apparently I am using "root" unnecessarily and dangerously.

---

### Post by scott_g on 2007-11-27
Hi,

Although this isn't recommended because of security risks, it is possible.  As per: [http://ubuntuforums.org/showthread.php?p=116697](http://ubuntuforums.org/showthread.php?p=116697) (which actually has the oposite problem...), you can disable the prompt by doing the following:

1. Type:

```

sudo gedit /etc/sudoers

```

2. Add/edit the last line of the code to look like:

```

*username* ALL=NOPASSWD: ALL

```
(where *username* is your username)

That should do it.  Again, its not recommended, but its your computer....

Scott

---

### Post by bodhi.zazen on 2007-11-27
IMO, best thing to do is to use sudo

If you use :

```
sudo -i
```

You will be asked for you password a single time, then you will be root.

Log out of the terminal when finished.

This preserves security yet allow you to do multiple admin tasks without editing config files or compromising security.

Well, it is a suggestion :twisted:

---

### Post by Sam Plamondon on 2007-11-28
From the many recommendations, I have decided to leave the password on.  Thanks for all the help, though!

---

### Post by bodhi.zazen on 2007-11-28
> **Sam Plamondon said:**
> From the many recommendations, I have decided to leave the password on.  Thanks for all the help, though!

\o/

---

