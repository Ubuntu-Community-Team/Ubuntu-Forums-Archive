---
title: "Recover /etc/dconf/profile/user"
date: 2018-12-13
forum: General Help
---

### Post by farooqte96 on 2018-12-13
I accidentally deleted file /etc/dconf/profile/user from from Ubuntu 16.04 and now on reboot system logs me out immediately just after logging in. It's sudo command results into following error message:

-bash: /usr/lib/command-not-found: /usr/bin/python3: bad interpreter: permission denied.

Is there anyone who can help me to get out of this problem? Thanks

---

### Post by Frogs Hair on 2018-12-13
I hate offer only the manual as a _starting_ point. Please wait for a user with specific knowledge of this problem.   

```
man dconf 
```

[http://manpages.ubuntu.com/manpages/xenial/man1/dconf.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/dconf.1.html)

---

### Post by freemedia2018 on 2018-12-13
This is fascinating stuff. To the user: don't fret, you may have hosed your installation but at worst you can probably do ANY of the following:

1. Install a different desktop and use that instead of GNOME (listing all the options I can think of, alright?)
2. Backup all your files and reinstall Ubuntu (but I'd try option #1 first)
3. Fix GNOME installation (for that you'll have to wait until someone figures out how) or:
4. Go for #1 and use that to accomplish #3 by removing GNOME and then reinstalling it.

Apparently dconf is the new settings registry for GNOME these days. I'm still happy with config files, you know. 

Perhaps there's an automatic backup. If so, perhaps someone can tell you how to restore it.

The reason you don't have to worry is that you should still be able to get into your system via an Ubuntu Live DVD. Or USB.

Which you might need, as it seems your Python permissions are affected. Somehow. That's very odd, with or without GNOME.

Decide what you want to first-- If my goal were to restore GNOME, I'd first install a lighter desktop (you can have more than one) So that Ubuntu can at least start up.

Great thing about this OS is how many ways there are to fix it. But don't just try a bunch of random stuff-- that makes it harder to fix it and harder for people to help.

Figure out what you want to do, first, if possible.

With your GNOME registry gone, your only hope of getting GNOME working is probably either a dconf settings backup (if there's a feature to make that happen automatically) or reinstalling GNOME altogether.

Until Ubuntu can boot properly you'll need your Live DVD (or USB) to get into your system.


I always leaned towards XFCE, personally. It was Xubuntu (07.04) that finally got me away from Windows.


The part where it can't run Python is weird, though. To me, that should work no matter what the status of GNOME is. Out of curiosity, are you sure that's all you deleted?

---

### Post by mc4man on 2018-12-13
Typically there would be no such file (user) in /etc/dconf/profiles/ Did you do something not mentioned to create this file?
By default in Ubuntu /etc/dconf/profile would only contain a file named ibus with this content
```
user-db:user
system-db:ibus
```
If ibus isn't in there try creating it  from a tty or the grub recovery (at recovery menu run a fsck 1st, then go to root shell prompt, ect.

Or if needed for some unexplained reason create a file named user with what's in link in 1st reply..

---

