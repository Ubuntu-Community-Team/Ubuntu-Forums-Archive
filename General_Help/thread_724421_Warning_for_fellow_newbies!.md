---
title: "Warning for fellow newbies!"
date: 2008-03-14
forum: General Help
---

### Post by LeoSolaris on 2008-03-14
I am typing this as a warning to others. This falls under the category of mistakes titled "It seemed like a good idea at the time!"

That said:

DON'T ever, ever, ever, ever under any circumstances do what I just did a few minutes ago.

I went through the system admin to the users and decided, since I want to delete a few things from my trash that have are root only from a recent attempt at creating a customized Live CD, to change my normal user's directory to /root, just like the root admin's.

That causes an amusing heart attack when I logged out and tried to get back in. Amusing at least for anyone watching.

In short I had to reboot, start it up in recovery mode, log into the terminal root user on my computer, and manually alter the user account.

```
usermod -d {home directory needed, default is /home/username} {username}
```

I am very glad that I opted to buy that O'Reilly book now!

In short, never ever ever change your home directory unless you actually know what you're doing, and that it can actually be a home dir.

I hope that no one else managed to make as boneheaded a mistake as that, but if someone is thinking that it makes sense to alter the user home dir for just a bit to do something, I hope they hear the echoes of my screams!

Leo S.

P.S Anyone actually know a way to delete files from the command line as root so I can get rid of those pesky files? They are not super important, since they are sitting idle in the Trash, but they are kinda bothersome, and my O'Reilly book is not clear on the subject.

---

### Post by moore.bryan on 2008-03-14
the cli command is ```
sudo rm -rf <file you're trying to delete>
```

---

### Post by LeoSolaris on 2008-03-14
oh! There is a second one. I used ```
gksudo nautilus
```

I stumbled across it on another thread and forgot to update this one till just now.

Thanks!
Leo S.

---

