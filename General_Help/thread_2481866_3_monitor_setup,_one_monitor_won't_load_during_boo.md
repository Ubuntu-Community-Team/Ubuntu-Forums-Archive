---
title: "3 monitor setup, one monitor won't load during boot."
date: 2022-12-11
forum: General Help
---

### Post by jxr006 on 2022-12-11
hey folks,
After a long hiatus (moved to macos) i committed all in to linux again, and brought my kids with me.

My main PC at home, that i use for work is a 3 monitor setup. One problem thats been driving me nuts is that: when the PC comes to the login screen only two monitors work.
The monitor doesn't work shows me systemd during the boot.
Then goes blank (no signal).
I log in on another monitor it all it comes back.


It was working for a little bit, but now i don't how to get them back... i know this is a problem i can live with.. but my brain won't let me leave it alone.

Anyone face this problem, and resolve it?

5.19.0-26-generic #27-Ubuntu SMP PREEMPT_DYNAMIC Wed Nov 23 20:44:15 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
Distributor ID: Ubuntu
Description:    Ubuntu 22.10
Release:        22.10
Codename:       kinetic


I am running kde plasma.



EDIT #1:
I just rebooted my computer, and the motherboard log in (ASUS) is scrambled. This has happened before and then i lost a monitor.. now my computer won't shutdown and reboot cleanly.
i had 1 month of peace and quite with no linux issues.. and now :(

---

### Post by jxr006 on 2022-12-11
anyone know how we can get a feature request like.... ->   ubuntu sudo apt-get rollback 2;
where we roll back 2days of updates.

i am so angry at myself. for the first time i had everything working perfectly. it would sleep / and come back alive... it would shut down cleanly..

now whatever i did yesterday prevents all of that. it crashes on sleep/hangs on reboot/shutdown, etc.., and i have one monitor that won't come on until after login, and flickers while i'm trying to work.

---

### Post by jxr006 on 2022-12-11
okay i solved it by reinstall xserver-xorg. Hope this helps someone else. i've been dealing with this issue on and off many times before, and sometimes got lucky as an updated fixed it.  if this works for anyone else, please let us know so we know this is a real solution.

[FONT=monospace][COLOR=#000000]sudo apt-get install --reinstall xserver-xorg

[/COLOR]
[/FONT]

---

### Post by jxr006 on 2022-12-11
anyone know how i can edit the title of the original post as "SOLVED" or is there a tool to mark this solved?

---

### Post by QIII on 2022-12-11
In the "Thread Tools" drop down (upper right), there is an option "Mark this thread as solved".

---

