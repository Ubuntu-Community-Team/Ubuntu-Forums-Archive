---
title: "Buggy Startup Applications"
date: 2008-03-30
forum: General Help
---

### Post by m4dm4n on 2008-03-30
I'm experiencing problems with applications which are running on startup and I can't seem to find anyone with the same issue. What happens is that programs I have enabled on startup through gnome-session-properties seem to be extremely buggy when started automatically. Normally, each application runs just fine, but here are some examples:

1. Kiba Dock
Kiba dock starts twice, the first time it appears as a weird image in the bottom right corner of the desktop which doesn't look anything like the dock (I only know because I right click it and the kiba-dock menu appears). The second time it appears looking more normal, but theres a strange empty white box added as an item. I have no problems if I quit both instances and start kiba-dock from the menu.

2. Tomboy Notes
Often spins off and chews up 100% of the CPU. Never displays in the tray on startup. I have never had either of these problems normally starting it.

3. Gnome-Do
Appears twice, the first instance without transparency, the second normal. This is not a major issue but if I disable it it just doesn't appear at all.

4. Gmail Notifier
In the list to run on startup but doesn't appear in the tray. Have to start it manually.

Essentially the two major problems are that nothing seems to display in the tray if its started automatically and both of the GUI applications are buggy, only on startup. I have checked and found that Tomboy and gmail-notifier are both running in the background, but without tray icons.

Is there some way to delay the start of these applications until a bit later? It seems like they're jumping the gun and firing up before the system tray has had a chance to get going and before everything's in place.

Any help would be greatly appreciated.

---

### Post by pointone on 2008-03-30
I think you're on the right track--it sounds like they're starting before the desktop has fully loaded. Create a wrapper script for these applications:

```
#! /bin/bash

sleep 15 # change depending on how long it takes to load the desktop after logging in
/path/to/application_1
/path/to/application_2
...
```

```
chmod +x /path/to/script
```

... and add this script to your session startup.

---

### Post by kerry_s on 2008-03-30
sounds to me like you saved a session with those programs running, so the session is starting them and your startup script is also starting them.
to test try disabling the startups you added and see if those programs still start.

---

### Post by m4dm4n on 2008-03-31
Seems to be that disabling Kiba dock fixes all of the problems I was having. That strange white box I was describing looks like the system tray segment of the top panel appearing in the dock for whatever reason, which meant that when the top panel did eventually load the icons weren't in it.

Thanks for your suggestions!

---

### Post by njparton on 2008-03-31
You may also be having problems with compiz?
 
Getting rid of it helped me out enormously!

---

