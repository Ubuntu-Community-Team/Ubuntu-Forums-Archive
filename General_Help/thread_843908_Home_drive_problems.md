---
title: "Home drive problems"
date: 2008-06-28
forum: General Help
---

### Post by MadeOfEyelashes on 2008-06-28
I attempted to place my home drive onto a separate partition, however it didn't work...

I followed the psychocats guide exactly as followed ([http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome))

However when I boot up Ubuntu(8.04) I get this error:

Users $HOME/.dmrc is ignored
File should be owned by user and have 644 permissions

I push okay then a few seconds later I get this error:

Couldn't locate file /home/nate/.ICEauthority

Help?

---

### Post by Forlong on 2008-06-29
Boot regularly until you reach GDM (login screen) and choose the Terminal session.

Log in with your problematic user.

You will be prompted the same error but you will be able to use a terminal-only session afterwards.

There you run those commands:
```
sudo chown -R $USER:$USER $HOME
```
```
chmod -R u+rwX $HOME
```
```
exit
```

Then try loggin into your regular GNOME session.

---

