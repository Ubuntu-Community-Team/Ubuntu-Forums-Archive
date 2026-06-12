---
title: "Just upgraded to gutsy, and need urgent help please"
date: 2007-10-19
forum: General Help
---

### Post by deformation on 2007-10-19
Hello forums..


upgraded from xubuntu feisty to gutsy, despite the fact that everything is a big mess, and the xfce desktop does not integrate with the human theme but i am facing a real real big annoying problem..


my fan does not stop running and giving me that sound as if the cpu is full, cpu usage is less than 10% and the fan does not stop spinning, i am using acer travelmate labtop..
why is this happening? i am annoyed by the sound and i feel that my labtop is burnning somehow!!

---

### Post by deformation on 2007-10-19
bump, guys please any advice/help?

---

### Post by bodhi.zazen on 2007-10-19
I do not know, but be sure it is not hardware related before you assume it is due to gutsy.

---

### Post by caldevil on 2007-10-19
Yes, usually the fan is controlled by bios, so it may be a hardware issue

---

### Post by deformation on 2007-10-19
its definitly due to gutsy, because 5 hours ago it was ok on feisty, once i booted into gutsy it started, i even did not move my laptop from its place. then i checked out with xp (double boot) and it was fine under xp

i think its one of the services that run with boot, i would appreciate a help with that , if you can tell me what services to start? i am using BUM.

---

### Post by caldevil on 2007-10-19
I am not sure if there is a service that is controlling the fan. If you monitor temperature using 'acpi -t' in terminal, does it seem OK?

---

### Post by deformation on 2007-10-19
when i run acpi -t

this is what it gives me :

 Battery 1: charged, 51%
No support for device type: thermal


strange because my battery is 100% and full!!

---

### Post by Merk42 on 2007-10-20
I'm on a desktop and have the same problem since I upgraded to Gutsy.  Reading these threads it seems a lot of people are having the fan issue.

---

### Post by Page on 2007-10-20
I get it sometimes, too.

---

### Post by deformation on 2007-10-20
the problem is that its somthing  that needs urgent attention, it may burn down the computer, and most guys here at the forums or irc support channel are not familiar with this error. :(

---

### Post by bodhi.zazen on 2007-10-20
> **deformation said:**
> the problem is that its somthing  that needs urgent attention, it may burn down the computer, and most guys here at the forums or irc support channel are not familiar with this error. :(

The mechanism to do this is to file a bug report :

How to : [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

---

