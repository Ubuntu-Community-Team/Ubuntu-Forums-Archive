---
title: "sharing and permissions cacked"
date: 2008-05-14
forum: General Help
---

### Post by OoooMatron on 2008-05-14
I'm so mad right now. Somethign out of nowhere has broken my system.

I rebooted yesterday after getting home from work. The pc has been on at least a week and i barely use it during the week days.

WHen i logged back in i couldn't use sudo , it told me my user had to be added. Well that was quite annoying but easily fixed. I rebooted to the rescue and added myself as a sudo user.

Now, when my external USB was turned off it didn't umount automatically, so the next time it was on it created a new name. This was ok except I couldn't get rid of the old name or umount it (Device busy - even though it wasn't in use).

Now I am trying to share my device again and I get

'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.


So now i can't even share my friggin drives!!!!

I tried going into the the authorisations menu but nothing happens at all when i click the buttons.

What the hell has gone wrong and how do i fix it?

---

### Post by az on 2008-05-14
Maybe you can start here:

[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

---

### Post by Monicker on 2008-05-14
The "net usershare" error is covered here: [http://ubuntuforums.org/showthread.php?t=773851]("http://ubuntuforums.org/showthread.php?t=773851")

Look at the Samba Shares section.

---

### Post by OoooMatron on 2008-05-15
that doesn't help becuase there is no solution there. nautilus-share is already installed.

---

### Post by OoooMatron on 2008-05-15
anorther problem is that synaptic icon keeps disappearing. i think my permissions are totally screwed somehow.

---

