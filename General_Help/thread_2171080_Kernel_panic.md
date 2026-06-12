---
title: "Kernel panic"
date: 2013-08-29
forum: General Help
---

### Post by mrskytown11 on 2013-08-29
i just installed the latest version of Ubuntu and i keep crashing i took a pic of the madness,i think its my Bluetooth usb dongle because i notice when im trying to connect it to my phone it eventually crashes, and it happened more when it was on and connected even from start up, and now its not plugged in and i haven't crashed, i was on before for a long time updating stuff and downloading stuff and it was fine, no crashing. i had this weird black screen, but i want to know what is the cause of the problem of the crashing???
maybe the Bluetooth is not supported, it works fine on my windows 8 machine but i understand that Linux is different.the usb is from china lol. but still ?? !!

---

### Post by Werne on 2013-08-29
That is an aiee kernel panic, a Linux equivalent of a BSOD. Gotta say, black makes it look darn good.:cool:

Anyway, the reason for the panic can be seen in the kernel log (/var/log/kern.log) and can be seen in demsg output, unless the system was too busted to write it down. If it's there, you're in luck. You have info on performing system crash debug [here]("https://help.ubuntu.com/community/DebuggingSystemCrash"), though it only mentions the bare basics of recovering kern.log. Get kern.log with whatever method you prefer (I usually copy it to my home from a live USB) and find the kernel panic entry.

Note: make coffee cause you have some reading to do, kern.log is one big file, sometimes the info you're looking is in the last 200-500 lines, sometimes it's on line 6,423 in a file 12,365 lines long. You never know what you'll get, it's like those Kinder Surprise chocolate egg thingies.;)

---

### Post by mörgæs on 2013-08-29
You need to be more precise. Exactly what dongle?

---

### Post by tgalati4 on 2013-08-29
Maybe the dongle gets hot and freezes causing a system crash.  Try a different dongle.  It may work in Windows, but do you use it in Windows for hours at a time?  Try that and see if it freezes.  If so, then your  dongle is worn out.

The crash dump that you posted shows network modules involved at the top of the screen.  Unfortunately, you need the very top of the crash stack to see exactly which module caused the initial crash.  But it's a reasonable guess that your bluetooth dongle is the source of the problem.  Bluetooth is not designed for network connectivity.  Just because you can does not make it a good idea.

---

### Post by Werne on 2013-08-29
Well, I actually took time to read the provided kernel panic photo thoroughly (although there's not much use in that without the module that crapped out). There are a few lines that mention wireless modules, more specifically Atheros wireless driver (ath5k) and SoftMAC framework (mac80211).

It's possible that the Atheros wifi/bluetooth card/dongle is causing the kernel panic. Unfortunately, the module that started the panic which is at the top of the stack can't be seen and that one is important, you'd have to dig into kern.log to find it.

---

### Post by mrskytown11 on 2013-08-29
hmm,interesting, i did remember setting some sort of network thing on the Bluetooth setting from my phone, i think it was using it as a modem or something, not too sure, i haven't really got a chance of looking at the logs and checking to see whats really going on. but i will figure that out, im still new to the whole ubuntu world.

---

