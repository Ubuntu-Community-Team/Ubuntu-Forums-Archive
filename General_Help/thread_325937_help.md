---
title: "help"
date: 2006-12-26
forum: General Help
---

### Post by Coop on 2006-12-26
Hello

I have ubuntu 6.10.

I have beryl and have it added to my session startup applications.

I only have one user account.

I applied some settings in beryl,and after I applied those settings my ubuntu was running perfectly.

After I logged out and logged back in again,when beryl loaded,ubuntu automatically logged out itself.

This happened more than once,so I restarted my computer and chose recovery mode,and the users and groups application said:```
The configuration could not be loaded

You are not allowed to access the system configuration.
```.

So I used deluser and adduser in the terminal to recreate my user account,and then I restarted and logged with my account and my account loaded,but when I click some things like the volume control button it says:```
No volume control GStreamer plugins and/or devices found.
```

How do I fix this problem?

I would prefer it if I didn't have to reinstall my ubuntu.

Please reply to me.
Regards Coop

---

### Post by Ecthelion on 2006-12-28
I see that I have a dir /home/ecthelion/.gstreamer-0.10
I suppose you had that dir too in your old user home dir, but you don't have it anymore in your new. (Is this correct?)
I see that when I change the name (to make the OS think it's gone), the dir gets created back when I klick on the volume control button.
So maybe just putting the dir back wouldn't help.

Try to reinstall the gstreamer plugins.

---

