---
title: "can't install updates"
date: 2008-01-20
forum: General Help
---

### Post by sf657 on 2008-01-20
I am new to ubuntu and linux in general. I installed yesterday and today I tried installing updates and got this error message-E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
I get the same message as soon as I open Synaptic. i tried pasting it in the terminal and it didn't recognize the command. Any help would be greatly appreciated.

---

### Post by aphirst on 2008-01-20
(Assuming of course you know how to use a terminal) : -

have you tried preceding it with 'sudo' :-

```
sudo dpkg --configure -a
```

Since dpkg is a key system tool, most useful functions/troubleshots require root access.

---

### Post by sf657 on 2008-01-20
it seems to be working now. thank you very much.

---

### Post by wennermark on 2008-05-09
Hi,

I use Gutsy 7.10 and i have the same problem..
but

```
sudo dpkg --configure -a
```

doesn't seem to work...

I think my users and groups are messed up, because i can't open "Users and Groups", "Synaptic", and others in the Administration. Anyway to reset the "Users and Groups"-settings?

---

