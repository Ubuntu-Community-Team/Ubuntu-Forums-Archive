---
title: "notify-send ignores the DISPLAY variable. Can I fix this?"
date: 2018-08-07
forum: General Help
---

### Post by Paddy Landau on 2018-08-07
I need to apply the [FONT=lucida console]DISPLAY[/FONT] environment variable to [FONT=lucida console]notify-send,[/FONT] e.g.
```
DISPLAY=:1 notify-send 'Title' 'Message'
```
Unfortunately, [FONT=lucida console]notify-send[/FONT] ignores the [FONT=lucida console]DISPLAY[/FONT] variable. Is there a way to fix this, so that [FONT=lucida console]notify-send[/FONT] goes to the correct display?

---

### Post by Holger_Gehrke on 2018-08-07
That's because notify-send doesn't display the notification, it sends it to a notification daemon (through the session-dbus, I think).

Holger

---

### Post by Paddy Landau on 2018-08-07
> **Holger_Gehrke said:**
> That's because notify-send doesn't display the notification, it sends it to a notification daemon (through the session-dbus, I think).
Ah, thanks. I don't suppose that there's a way to access the daemon directly, is there? Or, maybe, an alternative way to send a message to the display? For now, I'll use Zenity, which isn't ideal but will do. Or maybe I'll use [yad]("https://launchpad.net/~webupd8team/+archive/ubuntu/y-ppa-manager"), which is rather better.

---

