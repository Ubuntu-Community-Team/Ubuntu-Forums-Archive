---
title: "pidgin"
date: 2007-11-29
forum: General Help
---

### Post by nandorj78 on 2007-11-29
Hi,
Im getting used to pidgin as a replace to Live messenger, but there's something that still bothers me. I like to use it minimized in the system tray, so I would like it to warn me whenever a contact logs in, just like windows messenger does. I cant seem to find where to set it up. Anybody can help me?

thanks

---

### Post by nandorj78 on 2007-11-29
Another question:

how do I enter my personal message, right under the Nick?

Anybody? thanks!

---

### Post by kingofpain on 2007-11-29
1. For notifications, there are two plugins: libnotify (or something like that) and guifications. First should be installed by default. Look into Tools -> Plugins. If not, install pidgin plugins pack.
Guifications have to be installed separately.

2. In the BuddyList, down, where your name/nick is displayed, if you click on it, it will display a list with statuses you can choose.

---

### Post by vanadium on 2007-11-29
Pidgin remembers the last state it was in. If you minimized it, then the next time it is launched, it will remain minimized. There is one issue, though: if you launch it automatically during login using "Preferences - Sessions, Startup-programs", it starts invariably with the Buddy list open. I am not sure where the cause of this problem resides. An issue filed to the pidgin developers remained without follow up.

I was lucky to find solutions myself a few hours ago, though. I tested only the first solution (credit goes to another post which I probably found on this forum).

Solution 1: delay the startup of pidgin a bit

1) Create a small script, say "pidgin-startup"
```

#!/bin/sh
sleep 5; /usr/bin/pidgin

```

2) copy the script in a good location (I use my ~/bin, but you could use the system wide bin as well: /etc/bin)

3) In System - preferences - sessions, edit the startup command for pidgin to read pidgin-startup (better: provide full pathname, e.g. ~/bin/pidgin-startup)

Solution 2: the synaptic package pidgin-extprefs (the successor of gaim-extprefs) is supposed to contain an option to start pidgin minimized. I am not sure if this would work, though for the issue of startup during logging in.

---

### Post by nandorj78 on 2007-11-29
> **kingofpain said:**
> 
2. In the BuddyList, down, where your name/nick is displayed, if you click on it, it will display a list with statuses you can choose.

Ok, I guess I managed to set my nick, plus the message. But I can't see my buddies personal messages, only their nicks. What do I have to do to show their messages?

---

### Post by nandorj78 on 2007-11-30
Anyone knows how to show my contact (buddies) custom text message? At the moment I can only see their nicks

---

### Post by ZipoTe on 2007-11-30
Pidgin has not implemented this feature yet :(

---

### Post by genbuntu on 2008-02-20
> **vanadium said:**
> Pidgin remembers the last state it was in. If you minimized it, then the next time it is launched, it will remain minimized. There is one issue, though: if you launch it automatically during login using "Preferences - Sessions, Startup-programs", it starts invariably with the Buddy list open. I am not sure where the cause of this problem resides. An issue filed to the pidgin developers remained without follow up.

I was lucky to find solutions myself a few hours ago, though. I tested only the first solution (credit goes to another post which I probably found on this forum).

Solution 1: delay the startup of pidgin a bit

1) Create a small script, say "pidgin-startup"
```

#!/bin/sh
sleep 5; /usr/bin/pidgin

```

2) copy the script in a good location (I use my ~/bin, but you could use the system wide bin as well: /etc/bin)

3) In System - preferences - sessions, edit the startup command for pidgin to read pidgin-startup (better: provide full pathname, e.g. ~/bin/pidgin-startup)



ah, thanks for the nice explanation. After few months I thought I'd search this topic again and here I found a soultion that works :thumbsup: .

Edit: hmm.. sad news :( . It seemed to work at that time when I restarted the x system. However, upon rebooting it didn't make any changes . I have some possibilities in mind , so gonna try those now.

---

