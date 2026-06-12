---
title: "Ubuntu Freezes When Playing Games"
date: 2019-08-25
forum: General Help
---

### Post by neorob22 on 2019-08-25
Hello,

I have Steam running in the background and whether I launch a game via Steam or outside of Steam, I eventually run into an issue when playing games where the game will start stuttering and frames start to drop until my entire desktop locks up/freezes. Not even ctrl-alt-f2 will get me to a terminal. 

Examples of when this has happened:
Deus Ex Mankind Divided via Steam
Minecraft

Specs:
Ubuntu 19.04
Intel I7 Ivy Bridge
980ti GPU

---

### Post by Autodave on 2019-08-25
What, if any, driver did you install for the Nvidia card?  Where did you get the driver from?

Mechanically speaking: are you sure that you are not overheating the machine?  Cooling fans clean and functioning?  Have you run a memory test?  How much memory do you have?

---

### Post by neorob22 on 2019-08-25
Thanks for the quick response!

I'm using the proprietary Nvidia driver 430.40. I was digging around my system and saw that one of my drives has over 4,000 bad sectors. Is it true that the way SATA is designed that the whole system could lock up if one drive's bad sector is accessed? THis would make sense because every time the system freezes, my hdd light is solid

Also, my GPU temps sit between 70-80c and I'm using a Noctua cooler and I have 12GB of RAM (odd number I know)

---

### Post by neorob22 on 2019-08-25
Well I removed the bad drive, but the freezing still occurred. My hdd light is solid as usual and monitors both just went to "no signal detected". One monitor detected something, but it's just a black screen

---

### Post by neorob22 on 2019-08-25
After waiting, my desktop session came back to life and I checked the logs. Turns out Deus Ex Mankind Divided had an out of memory error.

---

