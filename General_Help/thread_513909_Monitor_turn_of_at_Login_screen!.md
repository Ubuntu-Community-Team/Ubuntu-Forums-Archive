---
title: "Monitor turn of at Login screen!"
date: 2007-07-31
forum: General Help
---

### Post by maduranga on 2007-07-31
Hello, I just installed Ubuntu Studio. But when I try to start the newly installed system, at the loging screen monitor turns of. Is that something related with the screen resoution? if it is the problem, how can i lower of change the resolution in text mood?



Maduranga

---

### Post by shavenlunatic on 2007-07-31
yepp.. possibly you resulution, possibly your monitor is set up as a second display (my TV goes black while i'm at the login screen)

at the login screen, hit CTRL+ALT+F2 and hopefully it will take you to a text-based login screen.

Log in and you will get a terminal

```
sudo nano /etc/X11/xorg.conf 
```

have a browse around there, I can't remember exactly which line (I'm sure someone will post) as I'm at work on an XP PC, but you can change available resolutions in there.

Good luck

---

### Post by Alexander2007 on 2007-07-31
> **maduranga said:**
> Hello, I just installed Ubuntu Studio. But when I try to start the newly installed system, at the loging screen monitor turns of. Is that something related with the screen resoution? if it is the problem, how can i lower of change the resolution in text mood?



Maduranga

At the text login screen, enter your user name and password. Then type: ```
sudo dpkg-reconfigure xserver-xorg
```

---

