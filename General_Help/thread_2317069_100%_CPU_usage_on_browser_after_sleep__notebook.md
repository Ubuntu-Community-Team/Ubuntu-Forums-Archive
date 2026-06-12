---
title: "100% CPU usage on browser after sleep / notebook"
date: 2016-03-13
forum: General Help
---

### Post by Yev on 2016-03-13
Greetings!

Sorry for my english. As title says, i have strange problem with CPU usage after i open my notebook lid(after sleep/hibernation). I can open any apps, everything will be fine. But when i start browser app(no matter firefox, chrome or opera) my CPU consumption is 80-100% on all 4 cores. I checked TOP in consoles, checked process managers, but see nothing there, only that my browser just eat everything. Because of so big CPU usage i cant use my browser, too slow. If i do restart - everything is fine, but so will be till i close my notebook lid :[

Same problem on all Ubuntu-based distros, xubuntu/ubuntu/kubuntu/lubuntu.

Notebook model: Dell Latitude E5420.

Archlinux, Debian and OpenSuse - everything is fine(except for other problems with my wifi drivers and other system bugs heh). Ubuntu working like a charm, but this browser thing just kills me. I really want to use ubuntu, but it is difficult without hibernation mode on notebook. Mobility is everything for me.

---

### Post by dragonfly41 on 2016-03-13
Launch System Tools > System Monitor > Processes > % CPU (sort so max value at top of sorted list)

Next time you have a freeze inspect browser CPU usage and you can End Process.

I often have Chromium Web Browser freezes and this is how I get out of it.  But I still don't know the cause.

My Dell is antique. Inspiron 1720.

---

### Post by Yev on 2016-03-13
Hm. Looks like "end Opera/Firefox/Chrome process" in SystemMonitor fix my problem without restart. At least something! Thank you friend. Still strange why i cant just close browser and reopen it normal way:'D

---

### Post by dragonfly41 on 2016-03-13
System Monitor is a work around to recover by End Process, avoiding a restart. 
But the cause is still a puzzle.

On End Process I read a crash report which I notice had this clue embedded in the report ..
> gpu-driver-bug-workarounds

I searched around and found these ...

[http://ubuntuforums.org/showthread.php?t=2214685](http://ubuntuforums.org/showthread.php?t=2214685)

[https://bugs.chromium.org/p/chromium/issues/detail?id=418858](https://bugs.chromium.org/p/chromium/issues/detail?id=418858)

I intend to try launching Chromium Browser from command line to see if I get no crashes

LIBGL_DRI3_DISABLE=1 chromium-browser

---

### Post by yevghenn on 2016-07-26
Update. I have found fix to my problem.

Seems like Linux dont know how to work with some notebook technologies. In BIOS(on my Dell Latitude) there is feature called "CPU C-state" in Power Management section. This thing "optimize CPU cores after sleep/suspend"(i dont know for sure, but so tells me BIOS). I disabled it and voila, no more problems with CPU usage and overheting after closing and opening lid.

---

