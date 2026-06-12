---
title: "Cannot see any wireless networks?? sorry im a noob"
date: 2007-07-12
forum: General Help
---

### Post by ashrafabdeljaber on 2007-07-12
Sorry everyone im a noob in Ubuntu. I just installed it today and it is the first time ive ever touched Linux or ubuntu or whatever you call it lol.

Anyways I tried to go on the internet but i couldnt because i wasnt connected. When I look on the menu, i only see the network icon (the picture of the 2 computers behind each other) what I dont see is that bar signal icon for wireless. Why?? I'm trying to connect to a wpa encrypted network.

---

### Post by linuxwizard on 2007-07-12
Need more info computer and wireless card specs. Make & model #'s Than maybe someone can help you. When you post try to give as much info as possible.

---

### Post by cisforcojo on 2007-07-12
Firstly, no need to apologize for being a noob. That's what these forums are for!

Secondly, when you say 'menu' do you mean System -> Administration -> Network? or on the top bar in the upper-right, the network icon there? That's called the... system tray?? Just clarifying.

Ubuntu doesn't have a wireless signal strength icon like Windows does (although something similar CAN be added.) That doesn't exist in a standard install (but would be nice).

All you need to do with that networking icon is right click and make sure 'Enable Networking' is checked.

What you want to use is System -> Administration -> Networking.  Wireless networking isn't as seamless as in Windows, not yet anyway. You're going to need to know your ESSID (the name of your Wireless Network, mine for example is 'Tipping Point')

Let me know if you have further problems with the Networking window.

---

### Post by golan on 2007-12-06
Sorry for reviving a thread, but I suppose this is the best place to post.

Yeah, I've been trying to access wireless internet for awhile now, but no cooperation. Wired connection works fine (I'm on it as I write this) but there is no option for wireless connection. Here is a snapshot of my Network window. See, no wireless connection option.

[IMG]http://xs322.xs.to/xs322/07494/snapshot1.png[/IMG]

Help?

---

### Post by chalewa on 2007-12-06
what kind of wireless card are you dealing with here?


if you don't know, post the output of:

```
lspci
```

---

### Post by gumpontheweb on 2008-01-05
I lost mine too and it is different than anything you can add to panel????
Another thread talks about this too

---

### Post by zipperback on 2008-01-05
> **gumpontheweb said:**
> I lost mine too and it is different than anything you can add to panel????
Another thread talks about this too

Please tell me the exact make and model of your system.

Please provide the output of

```
lspci

ifconfig

iwconfig

```

- zipperback
:popcorn:

---

