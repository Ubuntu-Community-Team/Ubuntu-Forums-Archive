---
title: "Both Xubuntu and Ubuntu installed"
date: 2013-04-08
forum: General Help
---

### Post by Psil0cybin on 2013-04-08
If I download Xubuntu after Ubuntu, and use Xubuntu through the login manager..
Am i running two windows managers?
Like Sorry I dont know the proper definitions, but If I log into Xubuntu am i still loading gnome files? Or Can I rest easy knowing my computer is only loading files for xfce?
So my computer isnt loading files for no reason such as something along side with lightdm (maybe xfce doesnt use lightdm - I am unsure)?

When I type
> env | grep -i DESKTOP_SESSION
it says
> DESKTOP_SESSION=xubuntu

Also when I type
> cat /etc/X11/default-display-manager
I get
> **/usr/sbin/lightdm**
So does that mean **lightdm** is the only thing loaded?
so can I be rest assured that im not loading gnome files? (or is lightdm interchangeable and Im kinda asking a silly question?) - Everything is a learning experience. 
Thanks in advance, I know the answer might be straight forward, I just really want to double check, So I learn exactly what is happening with my Linux Box :-)
- Psil0

---

### Post by ibjsb4 on 2013-04-08
Both Xubuntu and Ubuntu use lightdm (display manager).

If you wish to remove ubuntu and just run xubuntu ..

[http://www.psychocats.net/ubuntu/purexubuntuprecise](http://www.psychocats.net/ubuntu/purexubuntuprecise)

---

### Post by Psil0cybin on 2013-04-08
If I decide not to remove Ubuntu, and keep both of them
Am I using anymore RAM on my computer? Or Is it just a preference and a memory issue(hard drive space)?
Thanks again

---

### Post by ibjsb4 on 2013-04-08
To me, its a preference.  With both installed you have a lot more baggage to carry around that I consider unnecessary.

To me, its makes better sense to me to install the xfce4 package (xubuntu) and not all the extras that come with the full blown install.

[ATTACH=CONFIG]241119[/ATTACH]

Edit: Another thought ..

You may like the classic desktop
```

sudo apt-get install gnome-session-fallback
```

Its like the old gnome2 desktop and runs in the ubuntu environment.

---

