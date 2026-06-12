---
title: "Disabling certain shell commands?"
date: 2008-02-09
forum: General Help
---

### Post by linuxgeekery on 2008-02-09
Is there a way to do this?  Specifically, could you do it without removing it so other applications and the like could still use them, but you could not use them at the command line?

I know you could do something like "alias command='echo $deniedmessage''" or something like that, but anybody could just execute /usr/bin/command.

---

### Post by nemilar on 2008-02-09
You can assign the commands a group (if you just want it to be a single user, then use that user's group; otherwise, create a group, and add whoever you need to it), and then remove execute permissions on that file from group:


My group being nemilar:
```
chown :nemilar /usr/bin/firefox
chmod g-x /usr/bin/firefox

```

Which will prevent anyone in my group, nemilar, from running firefox (assuming that nemilar is not the owner of firefox, which should be root).

Chown changes owner in the format: chown user:group file  ; so we use :nemilar to specify the nemilar group (note the colon).  "chmod" changes permissions, and "g-x" stands for "for group, remove executable privileges".

Hope this solves your problem!

---

### Post by nemilar on 2008-02-09
Thinking about it, you might want to use:

```
chmod g-rx /usr/bin/command
```

instead, which will remove both read and execute privileges; this will prevent someone from just copying the file to their home directory and chmod +x'ing it so they can run it.

---

### Post by linuxgeekery on 2008-02-09
Thanks!

I've actually decided on another method – since the user is going to be a ssh-only user, I'm using jailkit to put the user into a chroot jail.

---

