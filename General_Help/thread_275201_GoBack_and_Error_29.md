---
title: "GoBack and Error 29"
date: 2006-10-11
forum: General Help
---

### Post by jakechance on 2006-10-11
Hey guys,

So I sucessfully split some free space out of my Windows partition and installed Ubuntu on it. To do this I had to disable GoBack which is a backup imaging program owned by Symantec. To re-enable it, I have to go into Windows and select the option. It does some stuff before rebooting the computer to complete the process. Everything looks fine and then GoBack splash screen comes up before GRUB screen. However, no matter which option I select, Ubuntu or Windows XP Pro, I get "Error 29: Disk write error" :confused: and it returns me to the GRUB Window. I am able to use my system if I power down and disable GoBack via the initial splash screen. I was wondering if anyone could help me out with this.

---

### Post by nfiniti9 on 2006-10-11
Uninstall goback, burn it, stomp on it, give it to your worst enemy. It is the worst program ever made.  It will ensure you data is not readable if the goback strap ever breaks.  Seriously its a nightmare for techs when it messes up.  Its badly designed and doesnt do anything more than system restore can do safely.  Its total junk.  I couldnt ever tell anyone how to actually make it work, I would feel bad doing you a disservice.

---

### Post by jakechance on 2006-10-11
All the same, I still would like to use it. Windows system restore is a joke and GoBack has at least saved my arse a lot of trouble a few times. I think the problem is that it is writing something to the boot area as it's splash screen showes up before GRUB which then doesn't let anything else write to the drive. I don't know though what it is doing exactly otherwise I'd be better equiped to fix the problem.

---

