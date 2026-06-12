---
title: "Weird Edgy Problem."
date: 2006-12-14
forum: General Help
---

### Post by Patrick-Ruff on 2006-12-14
I find this quite weird. I had to go into the menu editor to modify the shortcut to the Network Settings, I had to add gksudo for me to be able to actually use my Wireless card. 

The little network icon on the top panel that I have monitoring ETH1 (my wireless card) shows connectivity, I had to mess with it a lot to get it to work. Even then after messing with it and getting it to launch with administrator privilages, when I clicked the network name pulldown triangle, I couldn't see any networks . . . I had to type iwconfig and type in my router name manually for it to actually work. 

I want to be able to see networks available to me, so what can I do here? It worked perfectly in Dapper but now in Edgy (a fresh install) it doesn't.

also, when I double click on the network icon that shows my wireless connectivity, and click the Configure button, it doesn't launch with gksudo, it just launches without admin privilages.

what can I do here? I find it kind of irritating that dapper has such small issues, reminds me of the beta testing of Windows Vista :S.

anyways, any answers to such a problem will be greatly appriciated.

---

### Post by Patrick-Ruff on 2006-12-14
was I not discriptive enough?

---

### Post by Patrick-Ruff on 2006-12-14
or nobody cares . . .

---

### Post by fragos on 2006-12-14
I assume you're talking about the Network-monitor applet which you need but that's only one part.  It helps you assign the active network to your wireless.  There are a couple of choices but the one I've been most successful with is wifi-radar.  You can install it with Synaptic.  For best convienience I'd drag the wifi-radar icon to the applet bar.  Clicking it shows you a list of wireless networks available and allows you to select and configure for them.  The configurations can be saved for future use.  The network-monitor icon will display next to it an icron representing the signal strength of the wireless connection selected in wifi-radar.  I put those icons next to each other on my applet bar leaving room for the signal strenth pop up.

---

### Post by Patrick-Ruff on 2006-12-15
uh, I can't find the wifi-radar icon that shows the list of available wireless networks :P

also, I was just a bit concerned, because in dapper it automatically prompted with gksudo, but in this  . . . it just doesn't. makes me think a programmer made an error.

---

### Post by fragos on 2006-12-15
After you install wifi-radar you can access it with Applications-> Internet-> wifi-radar.  If you click and hold that icon you can drag it to the applet bar.  Edgy is a little different in this respect.  Some administrative function that used to require a change to root don't any more.  Also Edgy will remember that you have recently done a sudo or gksudo in the same terminal session and not require you to enter your password again.  There's nothing to be concerned about.  Tasks like installing still require passwords.

---

