---
title: "Things won't load"
date: 2007-02-06
forum: General Help
---

### Post by rruelas on 2007-02-06
There will often be a problem with my computer such as whenever I click a button such as to start the terminal or to shut down the computer, it will not respond. I can get almost every other program to start, but I can't get certain programs to even load.

I have a system monitor telling me that whenever I click on something, the CPU does work, but stops responding after a while. I see no change in the memory either. I was thinking that the process might just still be running, but there's no way I can kill it without the full system monitor or terminal, which I can't access.

Also, because of this problem, I can't shut down my computer properly. I always have to manually press the power button to shut it down.

My main question is, is there anything I can do to fix this? :confused:

---

### Post by amohanty on 2007-02-06
After a failure like that can you post the output of:
> dmesg | tail -n 100

Also in a terminal, if you type :
> sudo shutdown -r now

does the system reboot normally?

AM

---

### Post by rruelas on 2007-02-06
> **amohanty said:**
> After a failure like that can you post the output of:


Also in a terminal, if you type :


does the system reboot normally?

AM

As I said, I can't even access the terminal. I only click the icon, then at the bottom it shows "Starting Terminal" for a few seconds before vanishing, and the system acts like nothing's happened.

---

### Post by amohanty on 2007-02-06
HIt Ctrl+ALt+backspace to kill X and then do a 

dmesg | tail -n 100 | less
to view it.

AM

---

