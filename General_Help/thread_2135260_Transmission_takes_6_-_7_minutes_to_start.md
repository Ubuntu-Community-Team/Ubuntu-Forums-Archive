---
title: "Transmission takes 6 - 7 minutes to start"
date: 2013-04-13
forum: General Help
---

### Post by igurev on 2013-04-13
Hi, I'm experiencing a problem with Transmission as I wrote in the title. Either when I launch it directly or I open a .torrent file with it, I have to wait for 6 - 7 minutes before its "apparition".

When I try to launch Transmission via terminal, I get no error and the delay remains the same.

Once Transmission has been opened for the first time, then I can close it completely and when I try to launch it again, it will open in 1 second. The problems reappear when I reboot the computer.

I've installed Deluge to check whether the problem is affecting all the BitTorrent Clients, but it works perfectly.


P.S.

I'm using Ubuntu 12.04 with Gnome Session Fallback. I tried to open Transmission also on Unity and the problem remains.

---

### Post by angry_johnnie on 2013-04-13
Does the same thing happen to all users, or just you?  If it happens to you only, try deleting $HOME/.config/transmission.

---

### Post by igurev on 2013-04-13
I've tried to make the access as a "Guest" and I've got the same problem. I've deleted the folder you told me and when I launched Transmission, it took 3 - 4 minutes so start. I don't know if this decreasing of delay is just a coincidence or not, because it is not always the same.

---

### Post by andrew.46 on 2013-04-14
I am not terribly familiar with Transmission but are you able to start it from a Terminal and look for any error messages?

---

### Post by speartip on 2013-04-14
I had a similar problem.
Transmission would open ok, but then it would often take 2-3 minutes before a download would start.
I now use qbittorrent, works perfectly.

---

### Post by igurev on 2013-04-14
> [COLOR=#000000]are you able to start it from a Terminal and look for any error messages?[/COLOR]

As I've said in the first thread, when I try to start it from a Terminal, I get no error messages. It hangs on and then, after 6 - 7 minutes, Transmission appears.


By the way, I've already tried to delete the .config/Transmission folder in the last month, but now I've done it again and I noticed that Transmission opens in a few seconds. I hope that the problem won't appear as the time passes. Every time that I'll reboot the computer I'll try to open Transmission so as to understand if the problem has been solved.

Thanks for the help!

---

### Post by andrew.46 on 2013-04-14
> **igurev said:**
> As I've said in the first thread, when I try to start it from a Terminal, I get no error messages. It hangs on and then, after 6 - 7 minutes, Transmission appears.

Ooops my apologies :). Perhaps build the latest version and see if this fixes this rather odd problem:

[https://help.ubuntu.com/community/CompilingTransmission](https://help.ubuntu.com/community/CompilingTransmission)

---

### Post by igurev on 2013-04-14
Thanks, andrew.46, I've followed that guide and now Transmission work perfectly! I've noticed that now when I open Transmission, on the panel appears the window title "Avvio di Transmission" (it is Italian and it means "Starting of Transmission") and after 2 seconds it is already open. Before this, nothing used to appear on the panel until the program was open.

Thank you so much for the help, I can sign as [SOLVED] this thread!

---

### Post by andrew.46 on 2013-04-14
This is great news although your previous error is still of unknown cause. Glad that guide which I created a fair while back has been useful :)

---

