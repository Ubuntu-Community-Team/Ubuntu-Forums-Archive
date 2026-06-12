---
title: "Task panes... gone!"
date: 2006-07-18
forum: General Help
---

### Post by JetaKing on 2006-07-18
Earlier today I was playing around Ubuntu, and accidently made it freeze up while trying to make it connect to a wireless access point. I restarted the computer, and when it was done rebooting, and I signed in... my task panels were both gone! Everything else is working fine, I can switch desktops and everything. Signing into Gnome Fail Safe mode makes everything right again, though... That makes me think that something in the sessions are all screwed up! What do you think?

---

### Post by Skia_42 on 2006-07-19
Task Panes? Do you mean the small panels that display each window that is open on the bottom Panel of your screen or the 4 seperate workspaces? You can right click on space off to the left to edit the panel preferences.

---

### Post by JetaKing on 2006-07-19
I actually meant the entire panels, sorry. >.<

---

### Post by aysiu on 2006-07-19
Alt-F2 ```
gnome-panel
```

---

### Post by JetaKing on 2006-07-20
Cool, thanks, that worked.

Also, one more thing that happened when everything glitched - when I want to turn off the computer, I push the little button... and there is no shut down or restart button! I've got Log off, switch user, hibernate, standby, lock screen... where did the important options go? 0.o

---

### Post by JetaKing on 2006-07-21
Bump... I really need help! It's like my computer has insomnia and never wants to turn off... :shock:

---

### Post by Skia_42 on 2006-07-21
What happens when you go to System >>> Quit... >>> Shut down? Edit: Did I miss a joke?

---

### Post by aysiu on 2006-07-21
People probably aren't answering because they don't know the answer.

In the meantime, if you want your computer to shut down, type this terminal command: ```
sudo shutdown -h now
```

---

### Post by JetaKing on 2006-07-21
> **Skia_42 said:**
> What happens when you go to System >>> Quit... >>> Shut down? Edit: Did I miss a joke?

That's the thing... There is no Shut Down in the menu! 0.0

There is Log Out, Lock Screen, and Switch User in the top row, as usual.

In the bottom row, there is only suspend and hibernate. No shut down or restart button at all. ](*,)

---

### Post by aysiu on 2006-07-21
Have you gone to System > Preferences > Sessions and check to see that "Ask on logout" is checked?

---

### Post by JetaKing on 2006-07-21
> **aysiu said:**
> Have you gone to System > Preferences > Sessions and check to see that "Ask on logout" is checked?
Yes, it is checked. :-/

---

### Post by aysiu on 2006-07-21
Can you try creating a new user (System > Administration > Users & Groups) and then see if that new user has the same problem?

---

