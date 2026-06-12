---
title: "How to Change Auto Login"
date: 2015-07-11
forum: General Help
---

### Post by Rick St. George on 2015-07-11
How do we change Auto Login to Manual ... or vice-versa?

Thanks,
Rick

---

### Post by Bucky Ball on 2015-07-11
You search for 'autologin xubuntu' and find [this]("http://askubuntu.com/questions/530072/how-to-auto-login-in-xubuntu") from [here]("https://duckduckgo.com/?q=autologin+xubuntu"). ;)

There's two ways of going about it outlined there. Presuming they're still applicable. Easiest:

Settings> Users and Groups> Password> Asked on login> Change.

---

### Post by Rick St. George on 2015-07-11
> **Bucky Ball said:**
> 

There's two ways of going about it outlined there. Presuming they're still applicable. Easiest:

Settings> Users and Groups> Password> Asked on login> Change.

Mine says "Asked at Login", but it does not ask ... it auto logs in upon boot-up.

---

### Post by Bucky Ball on 2015-07-11
So that's the problem. Your first post only mentions how do you change it from one to the other, not that you already have and it doesn't work. 

Not sure. Have you dug anything up that relates to that issue? I'll have a look ... [here]("http://askubuntu.com/questions/106428/how-to-disable-automatic-login").

If the xfce4 tool is set to not autologin and it is, it's probably lightdm. Look at some of the answers on the link.

---

### Post by Rick St. George on 2015-07-11
Contents of LightDM;

```

[SeatDefaults]
user-session=xubuntu

```

AutoLogin is not even there.  So HOW do I turn it off ???

---

### Post by Bucky Ball on 2015-07-11
Unsure. Hopefully someone who's experienced this odd issue can help. Good luck. :)

---

### Post by Rick St. George on 2015-07-11
> **Bucky Ball said:**
> Unsure. Hopefully someone who's experienced this odd issue can help. Good luck. :)

Apparently I was in the wrong one. I was in .. /etc/lightdm/lightdm.conf.d//10-xubuntu.conf
the correct file is /etc/lightdm/lightdm.conf
I simply erased my username.
Reboot and wala ... Login Appears.

Thanks!
Rick

---

### Post by Bucky Ball on 2015-07-11
No probs. Glad you nutted it out. ;)

That explains everything. I don't use a stock standard Xubuntu but thought lightdm was a default with it.

---

