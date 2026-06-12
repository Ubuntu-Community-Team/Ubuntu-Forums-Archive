---
title: "Fire Fox won`t start!!!"
date: 2008-07-03
forum: General Help
---

### Post by heatblazer on 2008-07-03
Help! FF3 is doing craps again! It says that it`s running and to close it or to reboot. But I`ve rebooted, searched in the process list, it`s nowhere to be found :( I`ve tried to reboot in recovery mode, nope it`s stll giving me that message (thanx God there is Epiphany and Konqueror).
 Any help will be apprciated.

---

### Post by Bubba64 on 2008-07-03
Have you tried in the terminal typing firefox then enter to see if it opens or alt f2 and click on FF browser then run to see if it opens. Did you just close x when you rebooted or a restart. I put the system monitor in the top panel to see exactly what is running, you can also in the terminal type top to see whats running.

---

### Post by Sinkingships7 on 2008-07-03
Go to System->Administration->System Monitor

Right click on any instance of Firefox and press "Kill process".

---

### Post by Bubba64 on 2008-07-03
> **Sinkingships7 said:**
> Go to System->Administration->System Monitor

Right click on any instance of Firefox and press "Kill process".

Thats what I do, but I wasn't sure since I am not a real geek if this leaves any vulnerability. :)

---

### Post by pPrdrm on 2008-07-03
I had some issues like this with FF3 and the only solution I've found that fixed the problem was to delete the folder ".mozilla" in my home folder. What this does is deletes your firefox user profile and creates a new one. The only problem is that by deleting that folder you lose all your bookmarks, plugins, settings etc. So before deleting it check if this works on your case. Don't delete the ".mozilla" folder, just rename it to something like ".mozilla-Back_Up".

---

### Post by Bitten on 2008-07-04
> **pPrdrm said:**
> I had some issues like this with FF3 and the only solution I've found that fixed the problem was to delete the folder ".mozilla" in my home folder. 

Ah, brilliant. This did the trick for me as well. Firefox wouldn't start at all, it returned right away - no error message, no nothing. Also, the gecko engine (or whatever it's called) wasn't working neither so e.g. the Welcome screen in Eclipse was blank.

---

### Post by chrisccoulson on 2008-07-04
Out of interest, did you ever attempt to run firefox with sudo before your profile broke?

---

### Post by Bitten on 2008-07-06
Ah, I see now that my .mozilla has root as both owner and group (I kept the old profile by just renaming it). chowning/chgrping also fixes the problem.

Mine broke when upgrading to 8.04. I did not run firefox with sudo (at least not to my knowledge). I can say however that I ran Eclipse before Firefox the first time, maybe this messed something up? At least, the gecko engine was not working then (no welcome screen in Eclipse).

---

