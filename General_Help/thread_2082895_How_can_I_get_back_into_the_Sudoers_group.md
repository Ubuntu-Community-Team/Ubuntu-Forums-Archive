---
title: "How can I get back into the Sudoers group"
date: 2012-11-10
forum: General Help
---

### Post by antord on 2012-11-10
I think I have changed my group for my main user and now I cannot do sudo commands what shall I do?

 sudo usermod -G games anto is what I typed and now I think I don't have administrator rights..

Anyone got any ideas how to get back in?

Thanks

---

### Post by LordXandor on 2012-11-10
Have you tried using the GUI to modify your user account? It is under System Settings -> User Accounts I believe it is (I am currently in Windows so I cannot reference the exact actions at the moment). The GUI app should allow you to edit everything about your account.

---

### Post by mJayk on 2012-11-10
Can confirm the GUI method does work for giving you back your permissions.  I logged on with the incorrect account a while ago and couldn't work out why I had no sudo access fixed the problem(? was it a problem lol?) via the method above.

Cheers 

Matt

---

### Post by steeldriver on 2012-11-10
If you haven't logged out yet, then your original group memberships should still be in effect and you can re-add yourself - I'd recommend using gpasswd instead of usermod for exactly the reason you've just found out (for the record, the command you probably wanted is **[FONT=Courier New]usermod -[COLOR=Red]a[/COLOR]G games[/FONT]** - which appends the new group instead of replacing)

```
sudo gpasswd --add *user* sudo
```If it's too late for that, then you can boot into the recovery console, remount rw, and execute gpasswd from there

---

