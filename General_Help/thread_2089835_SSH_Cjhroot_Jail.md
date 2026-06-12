---
title: "SSH Cjhroot Jail"
date: 2012-11-30
forum: General Help
---

### Post by PinkFloyd102489 on 2012-11-30
Hello,

I'm trying to set up a chroot jail for a user in /var/jail, following this guide [http://allanfeid.com/content/creating-chroot-jail-ssh-access]("http://allanfeid.com/content/creating-chroot-jail-ssh-access").

I've got everything set up, but upon attempting to log in with the user, I get:

```
/var/jail/bin/bash: No such file or directory
Connection closed.

```

I've verified that /var/jail/bin/bash does exist, which is the bash that I want the user to utilize, so that they cannot escape the jail in any way. Everything in /var/jail/ is root:root, except for the users home directory which is owned by user:sshusers. I've also got the sshd_config configured to match the group and apply the chroot to /var/jail.

---

### Post by Lars Noodén on 2012-11-30
What login shell is your user trying to get? It should be relative to the jail.  It should be /bin/bash.

---

### Post by PinkFloyd102489 on 2012-11-30
> **Lars Noodén said:**
> What login shell is your user trying to get? It should be relative to the jail.  It should be /bin/bash.

I set the user's shell to /var/jail/bin/bash, since it resides within the jail.

---

### Post by Lars Noodén on 2012-11-30
Try setting it to /bin/bash because the chrooted user's account will not be able to see anything outside of the jail.  So even though it is really  /var/jail/bin/bash, for all practical purposes it will be /bin/bash because there is no  /var/jail/bin/bash inside the jail.

---

### Post by PinkFloyd102489 on 2012-11-30
Ok I'm able to get in now and unable to go any higher than /var/jail, so that's good.

The problem now is that the user is placed into /var/jail instead of /var/jail/home/user upon logging in.

According to /etc/passwd, the user directory is set correctly to user:x:1001:1001::/var/jail/home/user:/bin/bash, which is what it should be.

---

### Post by Lars Noodén on 2012-11-30
The same thing applies to the home directory as to the shell, nothing outside the jail will be accessible or even visible.  So if you want to use /var/jail/home/user as the home directory, it should be written as /home/user

---

### Post by PinkFloyd102489 on 2012-11-30
One last thing hopefully, lol.

Now, instead of getting a user@host prompt it has "I have no name!@host" prompt and attempting to use nano yields a "Error opening terminal: xterm" error.

---

### Post by Lars Noodén on 2012-11-30
Did you create /dev inside the jail and populate it with the devices you need?

---

### Post by PinkFloyd102489 on 2012-11-30
The guide I posted in the OP only has /dev/null, which I did add.

---

