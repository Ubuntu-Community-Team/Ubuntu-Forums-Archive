---
title: "Laptop goes to sleep while docked after login"
date: 2023-06-06
forum: General Help
---

### Post by diesieben07 on 2023-06-06
Since recently my Dell XPS 15 9500 running Ubuntu 22.04.2 has started exhibiting a new behavior. When it is connected to a thunderbolt dock (Dell WD19TB) with its lid closed it boots up normally and starts showing the login screen. Once I log in it *immediately* suspends. I can then wake up it again with the power button (the dock has a power button on it) and it will be on the desktop, without requiring a login and function normally. This behavior is new and has only started happening in the last couple days.

Note: I do *not* want to completely disable the lid switch as I also use my laptop outside of the dock, in that case I want it to go to sleep normally when I close the lid.
What I have tried so far:
[LIST]
[*]Update /etc/systemd/logind.conf:
[LIST]
[*]Uncomment HandleLidSwitch=suspend
[*]Uncomment HandleLidSwitchDocked line and change it to HandleLidSwitchDocked=ignore
[/LIST]

[*]Use GNOME Tweaks to turn off "Suspend when laptop lid is closed" (this is not what I want, but I tried it anyways - to no avail)
[/LIST]

What else can I try to restore the behavior that I had until a few days ago, where this functioned perfectly fine?

---

### Post by Jaxilian on 2023-06-08
I have same issue on 20.04.6 with Dell Latitude 7310 and WD19TBS dock. I have tried same as you.

---

### Post by Jaxilian on 2023-06-08
I tried uncommenting and changing the line to HandleLidSwitch=ignore in /etc/systemd/logind.conf and restarted computer.
Then it worked ok for me. If I open my lid then, it lights up the laptop screen and moves the dock to that one, but keeps the external screen active as a secondary. If I close the lid, it moves the dock back to the external screen.

---

### Post by diesieben07 on 2023-06-08
> **Jaxilian said:**
> I tried uncommenting and changing the line to HandleLidSwitch=ignore in /etc/systemd/logind.conf and restarted computer.
Then it worked ok for me.
Won't this make the laptop completely ignore the lid, even when not in the dock? I specifically want the laptop to still go to sleep upon closing the lid when it is not docked.

---

### Post by MAFoElffen on 2023-06-08
If that works-- Have you thought about a script to toggle that behavior for in-dock behavior and when not? Easy to do with just commnds using 'gsettings get' and 'gsettings set'...

---

### Post by Jaxilian on 2023-06-13
> **diesieben07 said:**
> Won't this make the laptop completely ignore the lid, even when not in the dock? I specifically want the laptop to still go to sleep upon closing the lid when it is not docked.

Sorry yes I was wrong there. That setting don't work. It only seemed to work.

---

### Post by Jaxilian on 2023-06-13
I tried this instead and it seems better. At least I don't experience that the laptop going to sleep during login

[B]HandleLidSwitchExternalPower=ignore
HandleLidSwitchDocked=ignore[/B]

and it also seems it goes to sleep when I pull the charger off the laptop. I see with command **sudo journalctl | grep systemd-sleep** that it goes down. I tried 5 restarts now and it seems to hold.

---

