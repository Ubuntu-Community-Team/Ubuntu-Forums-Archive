---
title: "where to store a login skript"
date: 2008-06-26
forum: General Help
---

### Post by mo0on on 2008-06-26
Hi,

I need the place where I can store a login skript. The skript isn't only for one user but for all users, so the place should not be user specific.

Hope you can tell me where to store. ^^

bye

---

### Post by iaculallad on 2008-06-26
Store it at this location:

> /etc/init.d

And be sure to make it executable by:

```
chmod a+x /etc/init.d/your_script.sh
```

---

### Post by mo0on on 2008-06-26
If I store it at init.d it will be excecuted to early. 
The reason is that I first need the name of the user which is login in for the skript. So the earliest point to excecute is after the password asking of gdm.

---

### Post by brian_p on 2008-06-26
> **mo0on said:**
> Hi,

I need the place where I can store a login skript. The skript isn't only for one user but for all users, so the place should not be user specific.

Hope you can tell me where to store.

/usr/local/bin

---

### Post by Trail on 2008-06-26
Are you using gnome/kde/?

On kde for example, you can put that script into ~/Autostart and it will be executed after you log in through kdm. This *is* user specific, but if you store the script in /usr/local/bin, it would be easy to call it for every user you are interested it.

Gnome should have something similar, but I haven't used it lately.

---

### Post by mo0on on 2008-06-26
I'm using gnome.

I found that I can store a .desktop file in /etc/xgd/autostart but the files stored there dosn't look like shell skripts.

The skript I need to start looks like this:


#!/bin/bash

ln -s -d /freigabe/*/*/& /home/SCHULE/&/homedir


But for this it is important to know the username which is logging in.
Can I put it in /usr/local/bin an it will be excecuted?

Sorry for the questions but I really have no clue at all.

---

### Post by brian_p on 2008-06-26
> **mo0on said:**
> The skript I need to start looks like this:


#!/bin/bash

ln -s -d /freigabe/*/*/& /home/SCHULE/&/homedir


But for this it is important to know the username which is logging in.
Can I put it in /usr/local/bin an it will be excecuted?

Sorry for the questions but I really have no clue at all.


We'll call that script 'yourloginscript'. Put it in /usr/local/bin.

In /etc/profile have

```
tty -s
if [ $? -eq 0 ] ; then
  nohup /usr/local/bin/yourloginscript &
  /bin/rm -f $HOME/nohup.out
fi
```

I'm assuming gdm sources /etc/profile but I'm not at a Ubuntu machine so cannot test whether it does or not.

---

