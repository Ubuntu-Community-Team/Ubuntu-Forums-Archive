---
title: "Hardy Just freezes after startup"
date: 2008-04-28
forum: General Help
---

### Post by bigbrovar on 2008-04-28
After installing Hardy i thought it was cool.. however of recent i have been experiencing frequent freezing of my system.. the system would just hang.. and nothing would move except the mouse pointer... and the only thing that would bring it back is a hard reset.. other times the system would just automatically log me out.. today it actually got worse system froze 3 times in succession. each time i would do a hard reset and try logging in once i start firefox it would freeze again... its really frustrating and embarrassing infront of my window using friends ... beside ubuntu is the only  operating system i have .. Recently Wiped out Vista .. So if Ubuntu doesnt work i cant use my computer .. please am in dire need and any help is appreciated

my system info
Nvidia geforce 8400gt,2 gb ram,160 gbs,intel core 2 duo .sony vaio fz21e

---

### Post by bigbrovar on 2008-04-28
i did some search on the problem and i found pple having the same problem ... and the culprit seam to be firefox.. am still trying to work on a solution .. that would help any body who could also be faced with the same problem .. for now the only solution i can come up with is 
1 dont use firefox on hardy .. or if u most .. use the v2 which is available in ur add and remove... or dont use compiz .. if u most use firefox 3.. the 2 dont seem to mix..at least for now .. if anybody has infor that would help please it would be appreciated

---

### Post by swiftsam on 2008-04-28
I am having a similar problem.  After I enter my login and password, it just freezes on the brown background color.  All I can do is restart X with a ctrl+alt+bksp.  logging in with failsafe gnome results in the same problem.  failsafe xterm works, but I don't know what to do from the terminal.

I just did a clean install of 8.04 a couple of days ago.  The computer is a dell e1505.  the last time I was logged in, gnome-terminal stopped responding.  killing and restarting it just gave me a frozen terminal window.  I restarted and now I'm stuck mid-login.  

Any ideas on what to check from the terminal I have?

thanks

---

### Post by Bitter Peace on 2008-04-29
> **swiftsam said:**
> I am having a similar problem.  After I enter my login and password, it just freezes on the brown background color.  All I can do is restart X with a ctrl+alt+bksp.  logging in with failsafe gnome results in the same problem.  failsafe xterm works, but I don't know what to do from the terminal.

This is exactly the same problem I have, except I upgraded from 7.10. Luckily, I had Fluxbox installed before upgrading, and that works perfectly, so you might want to install that from the terminal. 

Gnome freezing is a known bug (there seems to be a problem with gnome-keyring-manager) and is hopefully resolved soon.

I read a workaround on these forums which said to manually install an older version of gnome-keyring-manager which didn't work for me.

---

