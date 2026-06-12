---
title: "Passwords"
date: 2007-05-10
forum: General Help
---

### Post by CM Xtasy on 2007-05-10
For Feisty, is there a way to disable having to put in passwords for administrative actions?

---

### Post by jjmatt on 2007-05-10
> **CM Xtasy said:**
> For Feisty, is there a way to disable having to put in passwords for administrative actions?

I think you have four options:

1) You can just log in as root. THIS IS VERY UNSAFE.
2) you can do something similar to: []("http://http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_have_Firestarter_start_without_the_root_password")
however replace /usr/sbin/firestarter with every app you want to use without a password, there's probably a way to set this the default for everything.
3)you could make a symbolic link to the app name (i.e. /usr/**s**bin/firestarter) to a place in your bin, ie. (/usr/bin/firestarter) and then if you wanted to just click a button for it, you could create a script and place it on your desktop. Although I'm not 100% sure if this would actually work.

```
sudo ln -s /usr/sbin/firestarter /usr/bin/firestarter
sudo chmod +x /usr/bin/firestarter
```

After thinking about it though, I think you could just change the permissions on the file you're activating to something like

```
sudo chmod 770 /usr/sbin/firestarter
```


4)I believe there's something called a keyring, which saves your passwords for a period of time, but I haven't been on my ubuntu box in a while, so I can't tell you if thats true, although i'm pretty sure if it doesnt come default, you can install a package that does that.

---

### Post by dreadlord_chris on 2007-05-11
> **CM Xtasy said:**
> For Feisty, is there a way to disable having to put in passwords for administrative actions?

If you really want to bypass this security feature permanently, that's your choice. I won't tell you how - but I will point you in the right direction. 

Yes, there is a way - that still (sorta) maintains, or at least approaches, the Ubuntu security model.
You will still be required to use **sudo** for Administrative tasks - you just won't be asked for a password. This requires editing the **sudoers** file.
```

man sudoers

```
will tell you everything you need to know.....

---

### Post by rich.bradshaw on 2007-05-11
If you do this, then it is trivial for someone to log on over the internet and take control of your computer if you run certain services.

I would not recommend it - your computer will not have pretty much the main benefit of using Linux!

What do you actually want to do? There may be a way to make your life easier. You probably noticed that by default your password as root is remembered for a few mins to avoid repeatedly punching it in.

---

