---
title: "IBM ThinkPad Fan Always On"
date: 2006-11-02
forum: General Help
---

### Post by Sethro on 2006-11-02
Hi I just installed Ubuntu 6.10 and my IBM Thinkpad T43 fan is always on, but in Windows the laptop runs quiet. How would I fix this problem, I already tried using the powersaver option in CPU Scaling. But it wont work...

Any suggestions would be greatly appreciated.

---

### Post by Sethro on 2006-11-02
Guys.....

anybody..?

---

### Post by apalacheno on 2006-12-06
Hi!
No solution is yet known, but [ThinkWiki]("http://www.thinkwiki.org/wiki/Problem_with_fan_noise") gives an insight on this problem and possible workarounds.

Hope that helps.
Cheers,
apalacheno

---

### Post by ubuntu.daemon on 2007-09-14
ever find the solution? i have the answer if you need it lol

---

### Post by apalacheno on 2007-09-16
Sooo... what is the solution?

---

### Post by ubuntu.daemon on 2007-09-16
well go to this thread, it an old one of mine....
[http://ubuntuforums.org/showthread.php?t=338757]("http://ubuntuforums.org/showthread.php?t=338757")
  

it going to point you to thinkwiki and you need to get the script.  just get the script for now, bc if hat works ill tell you how to do the rest...
:popcorn:

---

### Post by kyalpani on 2007-09-17
hi i had a similar problem on my newly bought sony vaio, and i found out what was its problem, perhaps you have the same problem. I think this is a hardware related issue... Through chance I noticed that when I use my laptop away from home, the fan blows rarely and everything behaves as I expected. I repeated this exercise several times, each time with the same result, at home the fan blows all the time, away from home it is all quite. Then another chance event happened, I decided to remove the laptop's battery, in order to keep it from being used. After that the laptop went quite at home as well (it takes about ten minutes, and after that the fan stops kicking in and cpu heat remains constant at 37degrees celsius). Essentially, I think that the laptop battery sucks up too much power and heats up when it is plugged in at home, perhaps a precursor to the famous burning laptop syndrome. Depending on where I have it hooked-up to the electricity, the battery may remain cooler. An electrical engineer would probably give me a good explanation for this behaviour.

Kuros

---

### Post by ubuntu.daemon on 2007-09-17
naw thinkpads are set up differently for acpi functions, so its just a matter of what is running his fan daemon....
:popcorn:

---

### Post by kyalpani on 2007-09-17
sure, thinkpad is different than vaio, but my fan was blowing continuously as well  (and I mean for hours),  so obviously the acpi implementations have something similar.  BTW, I had the same problem on my windows XP partition, so i am sure it is not ubuntu's fault. How would you explain the fact that once I removed the battery, the fan stopped blowing? In any case, since a fan normally kicks in when the laptop heats up, one obvious place to look for, is a source of heat  alongside faults with the acpi subsystem :guitar:

---

