---
title: "shutdown as normal user."
date: 2006-09-07
forum: General Help
---

### Post by Hairy_Palms on 2006-09-07
is there a command i can use to shutdown as a normal user? if you use the gui logout dialog then root isnt needed but the shutdown halt and reboot commands all require root access. how can i shutdown from terminal as user?

---

### Post by tatimmer on 2006-09-07
On Mandrake it is possible to create a script which uses "sudo shutdown..." then edit your .sudoers file to allow certain users and groups to run this script.  I havent tied this on Ubuntu yet.

---

### Post by Hairy_Palms on 2006-09-07
i shouldve mentioned, doing anything that requires root access is not possible, the logout box does it without root access, is there a way to call whatever command the logout box uses?

---

### Post by Hairy_Palms on 2006-09-07
i shouldve mentioned, doing anything that requires root access is not possible, the logout box does it without root access, is there a way to call whatever command the logout box uses?

---

### Post by ayoli on 2006-09-07
try:
```
gdm-signal -h
```
dunno if you need sudo to run it, i dont want to test it now ;)
btw, i dont understand why you cant use sudo

---

### Post by Hairy_Palms on 2006-09-07
hmm it seems like it should work but it just isnt, ehrn i run it i get no errors but it just exits :(

---

### Post by Hairy_Palms on 2006-09-08
bump, anyone?

---

### Post by ayoli on 2006-09-08
> **ayoli said:**
> 
btw, i dont understand why you cant use sudo 
?

---

