---
title: "Run a program on boot using a specific user"
date: 2008-07-07
forum: General Help
---

### Post by Hopworks on 2008-07-07
I've never explored this possibility, but I would like to run a program with parameters as a specific user on boot. Could someone help me with this?

Currently, when my machine boots, I use putty from my Windows laptop to login as another user from root, then start hellanzb using the command line
hellanzb -D
then I logout and I'm back as root.

I'd like to automate that on boot, for that specific user.

Is that possible? How can I do that? Is it by editing the .bashrc file?

Thank you for your time!

Hop

---

### Post by sdennie on 2008-07-07
I don't completely understand your setup (specifically why you would be logged in as root) but, you can use su to run what you want:

```

su name_of_the_user -c "/path/to/program/to/run

```

Rather than putting that in a .bashrc, I recommend making an alias and putting it your .bashrc.  Something like this:

```

alias do_the_thing="su name_of_the_user -c '/path/to/program/to/run'"

```

---

### Post by Hopworks on 2008-07-07
I am a bit new to ubuntu, although I've been playing with it for some time. I found that if I login as my regular created user, I run into a few obstacles doing some things that need root access that the sudo thing doesn't resolve. I'm SURE it's probably something permission-based with files and folders I created as root, and I'll get my head around that eventually.

Thank you for your fast response! It gives me something to work with. I'll have to research what you offered so I can understand it as opposed to just doing it. That's the only way I'll learn about this wonderful OS.

Hop

---

### Post by bodhi.zazen on 2008-07-07
you can also sudo.

sudo -u user <command>

You can put that command into /etc/rc.local

```
sudo -u user hellanzb -D
```

Change "user" to the user you want to run hellanzb -D :twisted:

---

### Post by bodhi.zazen on 2008-07-07
> **Hopworks said:**
> I am a bit new to ubuntu, although I've been playing with it for some time. I found that if I login as my regular created user, I run into a few obstacles doing some things that need root access that the sudo thing doesn't resolve. I'm SURE it's probably something permission-based with files and folders I created as root, and I'll get my head around that eventually.

Thank you for your fast response! It gives me something to work with. I'll have to research what you offered so I can understand it as opposed to just doing it. That's the only way I'll learn about this wonderful OS.

Hop

In Ubuntu you should not log in as root. Log in as a user and use sudo.

For a root terminal :

```
sudo -i
```

For graphical root powers use gksu

```
gksu nautilus
```

Note: KDE uses kdesu rather then gksu.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

