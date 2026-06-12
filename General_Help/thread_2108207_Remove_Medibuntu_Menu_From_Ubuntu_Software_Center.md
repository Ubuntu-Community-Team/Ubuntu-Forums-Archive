---
title: "Remove Medibuntu Menu From Ubuntu Software Center"
date: 2013-01-24
forum: General Help
---

### Post by mardangga on 2013-01-24
Hii everyone...

I want to know, how to remove Medibuntu menu from Ubuntu Software Center??
I've remove medibuntu from software sources and remove medibuntu "app-install-data-medibuntu" and "apport-hooks-medibuntu" using 
"sudo apt-get remove app-install-data-medibuntu apport-hooks-medibuntu" command. And I've reboot my Ubuntu. But the menu still appear in Ubuntu Software Center when I click "Down Arrow" in Software Center.
Can anyone help me to fix this problem??
Thanks for the attention and sorry about my poor English.

---

### Post by oldos2er on 2013-01-24
You might just need to run ```
sudo apt-get update
```

---

### Post by mardangga on 2013-01-24
> **oldos2er said:**
> You might just need to run ```
sudo apt-get update
```

I've do that, but the menu is still appear. But the menu is menu is gone after I do reboot a few times :D

Now, I want to know, is it posible to remove PPA menu from Ubuntu Software Center without remove the PPA itself??
Coz, it doesn't look good. Each time I add new PPA, Ubuntu Software Center add new menu for those PPA.
Again, thanks for the attention :D

---

### Post by gifford on 2013-01-24
Have you tried to just uncheck the PPA in software sources? You don't delete the ppa, but disable it.

---

### Post by Frogs Hair on 2013-01-24
Packages that belong to a repository PPA or otherwise will appear in synaptic or the software center while software source is enabled.  > it doesn't look good. Each time I add new PPA Are you adding PPAS without permission or do you just want the packages to be hidden ?

---

### Post by mardangga on 2013-01-24
> **gifford said:**
> Have you tried to just uncheck the PPA in software sources? You don't delete the ppa, but disable it.
If I do this, do I still got update from those PPA??
> **Frogs Hair said:**
> Packages that belong to a repository PPA or otherwise will appear in synaptic or the software center while software source is enabled.   Are you adding PPAS without permission or do you just want the packages to be hidden ?

I just want to hide or remove the menu from Ubuntu Software Center, but not to remove the PPA. So, I still can get update from those PPA. Is it possible to do that?? :D

---

### Post by gifford on 2013-01-24
No. If they are disabled, you would not get update notifications.

---

### Post by mardangga on 2013-01-26
> **gifford said:**
> No. If they are disabled, you would not get update notifications.

So, is there a way to remove PPA menu from Ubuntu Software Center without disable or remove those PPA???

Updated: The main question of this topic is already solved. So, I'm gonna mark this thread as SOLVED and move my additional question into the new topic, to make this topic stay on the right track.

---

