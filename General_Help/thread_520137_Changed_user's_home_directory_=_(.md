---
title: "Changed user's home directory = :("
date: 2007-08-07
forum: General Help
---

### Post by Tyco22 on 2007-08-07
I accidentally changed my home directory from /home/tyler to /home/Tyler while using ubuntu. 

So now when it loads I get the .dmrc error and see that its trying to load from /home/Tyler which does not exists....

Is there any way to change my user account so it looks for /home/tyler again instead of the other folder?

Thanks.

btw.... I cant boot all the way to desktop but I can load the failsafe terminal... I already tried the chown and chmod articles on here but they do not apply to this problem...

---

### Post by merlinus on 2007-08-07
You might try this:

Rebooting the system in single user mode.

Hit e on the grub screen.

Choose the line that says something like

/boot/vmlinuz-2.6.20-15-generic root=UUID=d63fb4e2-0eb8-47f8-9b7c-734b78cf18b8 ro quiet splash

and hit the e key to edit

At the end of everything put -s so it looks like

/boot/vmlinuz-2.6.20-15-generic root=UUID=d63fb4e2-0eb8-47f8-9b7c-734b78cf18b8 ro quiet splash -s

and hit b to boot

The system should boot in single user mode. Then type in passwd and set a new password.

From there you should be able to change the directory name:

```

sudo rename whatever someother

```

-merlin

---

