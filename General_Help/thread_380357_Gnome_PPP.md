---
title: "Gnome PPP"
date: 2007-03-09
forum: General Help
---

### Post by chrispche on 2007-03-09
Usually Gnome PPP displays a sort of dial up networking icon in the taskbar. Even with it enabled it no longer does this. Short of turning off the modem, how else can I terminate the dial up connection?

---

### Post by jimbob on 2007-03-09
Do you have network manager installed?  You can disable the modem connection in there I believe.

You can always do it the crude way from the command line by killing the ppp process:

ps aux | grep ppp
sudo kill -9 <pid>
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

