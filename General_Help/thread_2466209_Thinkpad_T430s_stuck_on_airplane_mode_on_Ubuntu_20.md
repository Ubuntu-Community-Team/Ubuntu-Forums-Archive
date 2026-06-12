---
title: "Thinkpad T430s stuck on airplane mode on Ubuntu 20.04 (Focal Fossa)"
date: 2021-08-23
forum: General Help
---

### Post by ron4ld on 2021-08-23
Hello fellow Ubuntu-ers, 

I tried Focal Fossa on T430s but somehow it kept stuck on airplane mode. 
It worked fine on Windows 10 .... 

The wifi hardware button is on. 

I tried a few commands like  
nmcli r wifi on 
rfkill unblock al 


But still stuck on airplane mode :(

Any idea? 

TIA [COLOR=#333333][FONT=&quot]&#128591;[/FONT][/COLOR]

---

### Post by blackbird34 on 2021-08-25
How are its function keys set up? 

Many laptops have function keys (F1, F2 etc) that double as hardware keys for things like play/pause, airplane mode etc, with an "FN" key somewhere on the keyboard to toggle between a "function key" mode and a "hardware key" mode. 

Have you accidentally activated the "function key" mode? (on my laptop it requires pressing fn + esc, but I didn't find out for several months and frequently had problems like this)

---

### Post by ron4ld on 2021-08-29
It's Fn + F5 for turning off/on wifi on the keyboard, yes I've tried this couple of times but still didn't work, 
also has restarted the laptop many times...

---

### Post by blackbird34 on 2021-08-30
I poked around Google for a bit and it appears there is a hardware switch for Wi-fi on the side of the T430s. Are you sure it's switched on?

---

