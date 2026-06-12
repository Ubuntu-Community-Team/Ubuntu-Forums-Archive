---
title: "I have to restart my computer when connecting to a new SSID"
date: 2013-03-11
forum: General Help
---

### Post by supercheetah on 2013-03-11
Every time I go to a place with wifi networks my computer has not seen before, I cannot connect to any of them until I restart the computer.  When I click them to try to connect, it doesn't do anything.  It doesn't even bring up the prompt to enter in the wireless network key if there is one.  Once I completely reboot my computer, then it will start trying to reconnect, but not before then.

Does anyone have any clue as to what's going on, and how I can fix this?

---

### Post by steeldriver on 2013-03-11
There seems to be an issue with the nm-applet becoming unresponsive (e.g. can't even pop up the dialog for 'Edit Connections...')

I don't know what causes it but if that's your issue then less drastic than rebooting is just to restart nm-applet - in a terminal

```

pkill nm-applet
nm-applet 2>/dev/null &

```

---

### Post by supercheetah on 2013-03-11
Interesting.  I didn't even think about that being the possible reason.  I'll have to try that next time I'm connecting to a new network.

Could it be related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/930563")?

---

### Post by steeldriver on 2013-03-11
^^^ yes that sounds like it, I think I read that bug report before

will be interested to hear if your issue is related

---

